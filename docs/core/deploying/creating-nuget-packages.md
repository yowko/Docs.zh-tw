---
title: 使用 .NET 核心 CLI 創建 NuGet 包
description: 了解如何使用 'dotnet pack' 命令建立 NuGet 套件。
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 3f8e75a501cfc48e1c416f71e91290cab1a4ffae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920912"
---
# <a name="how-to-create-a-nuget-package-with-the-net-core-cli"></a>如何使用 .NET 核心 CLI 創建 NuGet 包

> [!NOTE]
> 下圖顯示使用 Unix 的命令列範例。 此處顯示的 `dotnet pack` 命令，運作運作方式與在 Windows 上如出一轍。

.NET Standard 和 .NET Core 程式庫預期以 NuGet 封裝方式散發。 實際上，所有的 .NET 標準程式庫都是以這種方式散發及取用。 `dotnet pack` 命令最容易完成此作業。

假設您剛寫完酷炫的新程式庫，希望透過 NuGet 散發。 您可以使用跨平臺工具創建 NuGet 包，以便做到這一點！ 下面的示例假定一個名為 **"超級真棒庫**"的庫`netstandard1.0`以 。

如果您有傳遞依賴項，即依賴于另一個包的專案，請確保在創建 NuGet 包之前使用`dotnet restore`命令還原整個解決方案的包。 否則將導致`dotnet pack`命令無法正常工作。

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

在確定封裝還原後，您可以瀏覽至程式庫所在的目錄︰

```console
cd src/SuperAwesomeLibrary
```

然後，只要從命令列發出單一命令︰

```dotnetcli
dotnet pack
```

您的 */bin/調試*資料夾現在如下所示：

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

這將生成能夠調試的包。 如果想要建置具有版本二進位檔案的 NuGet 套件，您只需要新增 `--configuration` (或 `-c`) 參數，並使用 `release` 作為引數。

```dotnetcli
dotnet pack --configuration release
```

您的 */bin*資料夾現在將有一個包含 NuGet 包*的發佈*資料夾，其中包含發佈二進位檔案：

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

現在您有發行 NuGet 封裝所需的檔案！

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>請勿混淆 `dotnet pack` 與 `dotnet publish`

請務必注意，和 `dotnet publish` 命令一點關係都沒有。 `dotnet publish` 命令是要使用相同組合中的所有相依性來部署應用程式，不是用來產生要透過 NuGet 散發及使用的 NuGet 封裝。

## <a name="see-also"></a>另請參閱

- [快速入門：建立及發佈套件](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
