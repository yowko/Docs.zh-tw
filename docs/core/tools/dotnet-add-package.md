---
title: dotnet add package 命令 - .NET Core CLI
description: "'dotnet add package' 命令提供方便的選項，將 NuGet 套件參考新增至專案。"
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 31dda9dbb101238b3a33d8b0d9a17765744480e0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696295"
---
# <a name="dotnet-add-package"></a>dotnet add package

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名稱

`dotnet add package` - 將套件參考新增至專案檔。

## <a name="synopsis"></a>概要

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a>描述

`dotnet add package` 命令提供方便的選項，可將套件參考新增至專案檔。 執行命令之後，會執行相容性檢查，確保套件與專案中的架構相容。 如果通過檢查，系統會將 `<PackageReference>` 元素新增到專案檔，並執行 [dotnet restore](dotnet-restore.md)。

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

例如，將 `Newtonsoft.Json` 新增至 *ToDo.csproj* 會產生類似下例的輸出：

```console
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\projects\ToDo\ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 235ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '10.0.3' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

*ToDo.csproj* 檔案現在會包含參考套件的 [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) 元素。

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a>引數

`PROJECT`

指定專案檔。 如果未指定，命令會在目前的目錄中搜尋一個專案檔。

`PACKAGE_NAME`

要新增的套件參考。

## <a name="options"></a>選項

`-h|--help`

印出命令的簡短說明。

`-f|--framework <FRAMEWORK>`

只有在以特定[架構](../../standard/frameworks.md)為目標時，才能新增套件參考。

`-n|--no-restore`

新增套件參考，而不執行還原預覽和相容性檢查。

`--package-directory <PACKAGE_DIRECTORY>`

將套件還原至指定的目錄。

`-s|--source <SOURCE>`

在還原作業期間，使用特定 NuGet 套件來源。

`-v|--version <VERSION>`

套件的版本。

## <a name="examples"></a>範例

將 `Newtonsoft.Json` NuGet 套件新增至專案：

`dotnet add package Newtonsoft.Json`

將特定版本的套件新增至專案：

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

使用特定 NuGet 來源新增套件：

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`
