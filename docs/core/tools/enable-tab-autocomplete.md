---
title: Activer la saisie semi-automatique via la touche TAB
description: Cet article vous explique comment activer la saisie semi-automatique via la touche TAB pour l’interface CLI .NET Core dans PowerShell, Bash et zsh.
author: thraka
ms.author: adegeo
ms.date: 12/17/2018
ms.openlocfilehash: 783868fb8300dd4a25c62a108c1c0f7a485721df
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029604"
---
# <a name="how-to-enable-tab-completion-for-net-core-cli"></a>Guide pratique pour activer la saisie semi-automatique à l’aide de la touche TAB pour l’interface CLI .NET Core

À compter du SDK .NET Core 2.0, l’interface CLI .NET Core prend en charge la saisie semi-automatique via la touche TAB. Cet article décrit comment configurer la saisie semi-automatique via la touche TAB pour trois des interpréteurs de commandes : PowerShell, Bash et zsh. D’autres interpréteurs de commandes peuvent prendre en charge la saisie semi-automatique. Consultez leur documentation pour configurer la saisie semi-automatique ; les étapes devraient être similaires à la procédure décrite dans cet article.

[!INCLUDE [topic-appliesto-net-core-2plus](~/includes/topic-appliesto-net-core-2plus.md)]

Une fois activée, la saisie semi-automatique via la touche TAB pour l’interface CLI .NET Core est déclenchée en tapant une commande `dotnet ` dans l’interpréteur de commandes, puis en appuyant sur la touche TAB. La ligne de commande actuelle est envoyée à la commande `dotnet complete`, et les résultats sont traités par votre interpréteur de commandes. Vous pouvez tester les résultats sans activer la saisie semi-automatique via la touche TAB en envoyant une instruction directement à la commande `dotnet complete`. Par exemple :

```
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

Si cette commande ne fonctionne pas, vérifiez que le kit SDK .NET Core 2.0 ou version ultérieure est installée. S’il est installé mais que cette commande ne fonctionne toujours pas, vérifiez que la commande `dotnet` correspond à la version 2.0 ou ultérieure du SDK .NET Core. Utilisez la commande `dotnet --version` pour afficher la version de `dotnet` correspondant à votre chemin d’accès actuel. Pour plus d’informations, consultez [Sélectionner la version .NET Core à utiliser](../versions/selection.md).

### <a name="examples"></a>Exemples

Voici quelques exemples de saisie semi-automatique via la touche TAB :

Entrée                                | devient                                                                     | car
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | `add` est la première sous-commande, par ordre alphabétique.
`dotnet add p⇥`                      | `dotnet add --help`                                                          | La saisie semi-automatique renvoie des sous-chaînes et `--help` s’affiche en premier, par ordre alphabétique.
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | Une seconde pression sur la touche TAB fait apparaître la suggestion suivante.      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | Les résultats s’affichent par ordre alphabétique.
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | La saisie semi-automatique via la touche TAB tient compte du fichier de projet.

## <a name="powershell"></a>PowerShell

Pour ajouter la saisie semi-automatique via la touche TAB à **PowerShell** pour l’interface CLI .NET Core, créez ou modifiez le profil stocké dans la variable `$PROFILE`. Pour plus d’informations, consultez [Création de votre profil](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#how-to-create-a-profile) et [Profils et stratégie d’exécution](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#profiles-and-execution-policy). 

Ajoutez le code suivant à votre profil :

```powershell
# PowerShell parameter completion shim for the dotnet CLI 
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a>Bash

Pour ajouter la saisie semi-automatique via la touche TAB à votre interpréteur de commandes **bash** pour l’interface CLI .NET Core, ajoutez le code suivant à votre fichier `.bashrc` :

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}")"

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a>Zsh

Pour ajouter la saisie semi-automatique via la touche TAB à votre interpréteur de commandes **zsh** pour l’interface CLI .NET Core, ajoutez le code suivant à votre fichier `.zshrc` :

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
