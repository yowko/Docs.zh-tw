---
title: 安裝和管理 SDK 範本-.NET Core
description: 瞭解如何在 Windows、Linux 和 macOS 上安裝 .NET Core 範本。
author: adegeo
ms.author: adegeo
ms.date: 04/24/2020
zone_pivot_groups: operating-systems-set-one
no-loc:
- dotnet new
- dotnet nuget add source
ms.openlocfilehash: 09acae1409eb0492be10bd3a61b14da5be57c6c7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324493"
---
# <a name="manage-net-project-and-item-templates"></a>管理 .NET 專案和專案範本

.NET Core 提供範本系統，可讓使用者從 NuGet、NuGet 套件檔案或檔案系統目錄安裝或卸載範本。 本文說明如何透過 .NET Core SDK CLI 管理 .NET Core 範本。

如需建立範本的詳細資訊，請參閱[教學課程：建立範本](../tutorials/cli-templates-create-item-template.md)。

## <a name="install-template"></a>安裝範本

範本會透過 [dotnet new](../tools/dotnet-new.md) SDK 命令搭配參數來安裝 `-i` 。 您可以提供範本的 NuGet 套件識別碼，或包含範本檔案的資料夾。

### <a name="nuget-hosted-package"></a>NuGet 主控的套件

.NET CLI 範本會上傳至[NuGet](https://www.nuget.org/)以進行寬分佈。 您也可以從私人摘要安裝範本。 *Nupkg*範本檔案不會上傳至 NuGet 摘要，而是可以散發並手動安裝，如[本機 NuGet 封裝](#local-nuget-package)一節中所述。

如需有關設定 NuGet 摘要的詳細資訊，請參閱 [dotnet nuget add source](../tools/dotnet-nuget-add-source.md) 。

若要從預設的 NuGet 摘要安裝範本套件，請使用 `dotnet new -i {package-id}` 下列命令：

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates
```

若要從具有特定版本的預設 NuGet 摘要安裝範本套件，請使用 `dotnet new -i {package-id}::{version}` 命令：

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.2.6
```

### <a name="local-nuget-package"></a>本機 NuGet 套件

建立範本套件時，會產生*nupkg*檔案。 如果您有包含範本的*nupkg*檔案，您可以使用下列命令來安裝它 `dotnet new -i {path-to-package}` ：

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\Some.Templates.1.0.0.nupkg
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/Some.Templates.1.0.0.nupkg
```

::: zone-end

### <a name="folder"></a>資料夾

除了從*nupkg*檔案安裝範本以外，您也可以使用命令直接從資料夾安裝範本 `dotnet new -i {folder-path}` 。 指定的資料夾會被視為任何找到的範本的範本套件識別碼。 已安裝在指定資料夾階層中找到的任何範本。

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\some-folder\
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/some-folder/
```

::: zone-end

在 `{folder-path}` 命令上指定的會成為所有找到的範本的範本套件識別碼。 如 [[清單範本](#list-templates)] 區段中所指定，您可以使用命令來取得已安裝的範本清單 `dotnet new -u` 。 在此範例中，範本套件識別碼會顯示為用於安裝的資料夾：

::: zone pivot="os-windows"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  /home/username/code/templates
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="uninstall-template"></a>卸載範本

範本會透過 [dotnet new](../tools/dotnet-new.md) SDK 命令與參數一起卸載 `-u` 。 您可以提供範本的 NuGet 套件識別碼，或包含範本檔案的資料夾。

### <a name="nuget-package"></a>Nuget 套件

安裝 NuGet 範本套件之後（從 NuGet 摘要或*nupkg*檔案），您可以藉由參考 nuget 套件識別碼來將它卸載。

若要卸載範本套件，請使用 `dotnet new -u {package-id}` 命令：

```dotnetcli
dotnet new -u Microsoft.DotNet.Web.Spa.ProjectTemplates
```

### <a name="folder"></a>資料夾

透過[資料夾路徑](#folder)安裝範本時，資料夾路徑會變成範本套件識別碼。

若要卸載範本套件，請使用 `dotnet new -u {package-folder-path}` 命令：

::: zone pivot="os-windows"

```dotnetcli
dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="list-templates"></a>列出範本

藉由使用沒有套件識別碼的標準卸載命令，您可以查看已安裝的範本清單，以及用來卸載每個範本的命令。

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

## <a name="install-templates-from-other-sdks"></a>從其他 Sdk 安裝範本

如果您已依序安裝 sdk 的每個版本，例如安裝了 SDK 2.0、SDK 2.1 等等，則會安裝每個 SDK 的範本。 不過，如果您從較新的 SDK 版本開始（例如3.1），則只會包含適用于[LTS （長期支援）](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)版本的範本，而 sdk 3.1 版本則為 sdk 2.1 和 sdk 3.1。 不包含任何其他版本的範本。

.NET Core 範本可在 NuGet 上取得，而且您可以像任何其他範本一樣地進行安裝。 如需詳細資訊，請參閱[安裝 NuGet 託管套件](#nuget-hosted-package)。

| SDK              | NuGet 套件識別碼                                                                                                      |
|------------------|-------------------------------------------------------------------------------------------------------------------------------|
| .NET Core 2.1    | [`Microsoft.DotNet.Common.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.1) |
| .NET Core 2.2    | [`Microsoft.DotNet.Common.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.2) |
| .NET Core 3.0    | [`Microsoft.DotNet.Common.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.0) |
| .NET Core 3.1    | [`Microsoft.DotNet.Common.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.1) |
| ASP.NET Core 2.1 | [`Microsoft.DotNet.Web.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.1)       |
| ASP.NET Core 2。2 | [`Microsoft.DotNet.Web.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.2)       |
| ASP.NET Core 3。0 | [`Microsoft.DotNet.Web.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.0)       |
| ASP.NET Core 3。1 | [`Microsoft.DotNet.Web.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.1)       |

例如，.NET Core SDK 包含以 .NET Core 2.1 和 .NET Core 3.1 為目標之主控台應用程式的範本。 如果您想要將目標設為 .NET Core 3.0，您必須安裝3.0 範本。

01. 嘗試建立以 .NET Core 3.0 為目標的應用程式。

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    如果您看到錯誤訊息，則需要安裝範本。

    > 找不到符合輸入的已安裝範本，正在線上搜尋 .。。

01. 安裝 .NET Core 3.0 專案範本。

    ```dotnetcli
    dotnet new -i Microsoft.DotNet.Common.ProjectTemplates.3.0
    ```

01. 嘗試第二次建立應用程式。

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    您應該會看到一則訊息，指出已建立專案。

    > 已成功建立範本「主控台應用程式」。
    >
    > 正在處理建立後的動作 .。。正在 path-to-project-file 上執行 ' dotnet restore ' .。。正在判斷要還原的專案 .。。Path-to-project-file 的還原已于1.05 秒完成，適用于 .csproj。
    >
    > 還原成功。

## <a name="see-also"></a>另請參閱

- [教學課程：建立專案範本](../tutorials/cli-templates-create-item-template.md)
- [dotnet new](../tools/dotnet-new.md)
- [dotnet nuget add source](../tools/dotnet-nuget-add-source.md)
