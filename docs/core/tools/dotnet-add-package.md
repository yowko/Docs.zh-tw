---
title: dotnet add package 命令
description: "'dotnet add package' 命令提供方便的選項，將 NuGet 套件參考新增至專案。"
ms.date: 06/26/2019
ms.openlocfilehash: 124e42b1d5897802bb1698c8e22b7e76031391a2
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105170"
---
# <a name="dotnet-add-package"></a>dotnet add package

**本文適用於：✓** .NET Core 1.x SDK 和更新版本

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>名稱

`dotnet add package` - 將套件參考新增至專案檔。

## <a name="synopsis"></a>概要

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a>說明

`dotnet add package` 命令提供方便的選項，可將套件參考新增至專案檔。 執行命令之後，會執行相容性檢查，確保套件與專案中的架構相容。 如果通過檢查，系統會將 `<PackageReference>` 元素新增到專案檔，並執行 [dotnet restore](dotnet-restore.md)。

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

例如，將 `Newtonsoft.Json` 新增至 *ToDo.csproj* 會產生類似下例的輸出：

```console
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\Temp\projects\consoleproj\consoleproj.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 79ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg 232ms
log  : Installing Newtonsoft.Json 12.0.1.
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '12.0.1' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

*ToDo.csproj* 檔案現在會包含參考套件的 [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) 元素。

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a>引數

- **`PROJECT`**

  指定專案檔。 如果未指定，命令會在目前的目錄中搜尋一個專案檔。

- **`PACKAGE_NAME`**

  要新增的套件參考。

## <a name="options"></a>選項

- **`-f|--framework <FRAMEWORK>`**

  只有在以特定[架構](../../standard/frameworks.md)為目標時，才能新增套件參考。

- **`-h|--help`**

  印出命令的簡短說明。

- **`--interactive`**

  允許命令停止並等候使用者輸入或動作 (例如完成驗證)。 自 .NET Core 2.1 SDK 2.1.400 版起可用。

- **`-n|--no-restore`**

  新增套件參考，而不執行還原預覽和相容性檢查。

- **`--package-directory <PACKAGE_DIRECTORY>`**

  還原套件的目錄。 Windows 上的預設套件還原位置為 `%userprofile%\.nuget\packages`，macOS 和 Linux 上則為 `~/.nuget/packages`。 如需詳細資訊，請參閱[在 NuGet 中管理全域套件、快取和暫存資料夾](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)。

- **`-s|--source <SOURCE>`**

  要在還原作業期間使用的 NuGet 套件來源。

- **`-v|--version <VERSION>`**

  套件的版本。 請參閱 [NuGet 套件版本控制](https://docs.microsoft.com/nuget/reference/package-versioning) \(部分機器翻譯\)。

## <a name="examples"></a>範例

- 將 `Newtonsoft.Json` NuGet 套件新增至專案：

  ```console
  dotnet add package Newtonsoft.Json
  ```

- 將特定版本的套件新增至專案：

  ```console
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- 使用特定 NuGet 來源新增套件：

  ```console
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a>另請參閱

- [在 NuGet 中管理全域套件、快取和暫存資料夾](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [NuGet 套件版本控制](https://docs.microsoft.com/nuget/reference/package-versioning)
