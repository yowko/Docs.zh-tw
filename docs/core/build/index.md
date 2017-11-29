---
title: "從原始檔建置 .NET Core"
description: "了解如何從原始程式碼建置 .NET Core 和 .NET Core CLI。"
keywords: ".NET, .NET Core, 原始檔, 建置"
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8b49079c-6ede-429a-92d7-ecd2fda1ab0e
ms.openlocfilehash: b2e62074992432dc5ee1360e17f87c782685dc35
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="build-net-core-from-source"></a>從原始檔建置 .NET Core

能夠從原始程式碼建置 .NET Core 很重要，如此一來就能輕鬆地將 .NET Core 移植到新平台、對產品提出貢獻和修正，並建立自訂的 .NET 版本。
本文為想要建置及散發自己的 .NET Core 版本的開發人員提供指引。

## <a name="build-the-clr-from-source"></a>從原始檔建置 CLR

您可以在 [GitHub 上的 `dotnet/coreclr` 存放庫](https://github.com/dotnet/coreclr/)中找到 .NET Core CLR 的原始程式碼。

此組建目前相依於下列必要條件：
* [Git](https://git-scm.com/)
* [CMake](https://cmake.org/)
* [Python](https://www.python.org/)
* C++ 編譯器。

安裝這些必要條件之後，您可以叫用 [Core CLR 存放庫](https://github.com/dotnet/coreclr/)基底的組建指令碼 (在 Windows 上為 `build.cmd`，在 Linux 和 macOS 上為 `build.sh`) 來建置 CLR。

安裝的元件會隨著作業系統 (OS) 而有所不同。 請參閱特定 OS 的建置指示：

 * [Windows](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
 * [Linux](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
 * [macOS](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
 * [FreeBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md) 
 * [NetBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

無法跨 OS 建置 (僅適用於建置在 X64 上的 ARM)。  
您必須在特定平台上，才能建置該平台。  

組建有兩個主要的 `buildTypes`：

 * 偵錯 (預設)：以最低最佳化來編譯執行階段，並進行額外的執行階段檢查 (判斷提示)。 降低最佳化層級與額外的檢查會讓執行階段的執行變慢，但是有助於偵錯。 這是開發和測試環境的建議設定。
 * 發行：以完整最佳化來編譯執行階段，且沒有額外的執行階段檢查。 如此會提高執行階段的效能，但是需要較長的建置時間，且偵錯較為困難。 若要選取此建置類型，請將 `release` 傳遞至建置指令碼。

此外根據預設，組建不只會建立執行階段可執行檔，也會建立所有測試。
由於有相當多的測試，因此如果您只想要試驗變更，這些測試會花費不必要的大量時間。
您可以將 `skiptests` 引數新增至建置指令碼來略過建立測試，如下列範例所示 (在 Unix 電腦上請將 `.\build` 取代為 `./build.sh`)：

```bat
    .\build skiptests 
```

前一個範例示範如何建置啟用開發階段檢查 (判斷提示) 並停用最佳化的 `Debug` 類別。 若要建置發行 (全速) 類別，請執行下列程式碼：

```bat 
    .\build release skiptests
```

您可以使用 -? 或 -help 限定詞，找到此組建的更多建置選項。   

### <a name="using-your-build"></a>使用您的組建

組建會將其產生的所有檔案放在存放庫的基底 `bin` 目錄下。
*bin\Log* 目錄包含建置期間所產生的記錄檔 (這在建置失敗時會最有用)。
實際輸出位於 *bin\Product\[平台].[CPU 架構].[組建類型]* 目錄下，例如 *bin\Product\Windows_NT.x64.Release*。

雖然建置的「原始」輸出有時很有用，但您通常只對 NuGet 套件有興趣，該套件位於先前輸出目錄的 `.nuget\pkg` 子目錄中。

您有兩個基本技術可使用新的執行階段：

 1. **使用 dotnet.exe 和 NuGet 撰寫應用程式**。
    如需使用您剛建立的 NuGet 套件和 'dotnet' 命令列介面 (CLI) 來建立使用新執行階段之程式的指示，請參閱 [Using your .NET Core Runtime Build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) (使用您的 .NET Core 執行階段組建)。 非執行階段開發人員預期可能會使用這項技術來取用您的新執行階段。    

 2. **使用 corerun.exe 透過未封裝的 DLL 執行應用程式**。
    此存放庫也會定義一個與 NuGet 沒有任何相依性的簡單主機，稱為 corerun.exe。
    您必須告訴主機何處可取得您實際使用的必要 DLL，而且您必須手動將這些 DLL 收集在一起。
    這項技術可供 [Core CLR 存放庫](https://github.com/dotnet/coreclr)中的所有測試使用，並且有助於在本機快速執行「編輯-編譯-偵錯」迴圈，例如初步單元測試。
    如需使用這項技術的詳細資料，請參閱 [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) (使用 corerun.exe 執行 .NET Core 應用程式)。

## <a name="build-the-cli-from-source"></a>從原始檔建置 CLI

您可以在 [`dotnet/cli`GitHub 上的存放庫](https://github.com/dotnet/cli/)中找到 .NET Core CLI 的原始程式碼。

若要建置 .NET Core CLI，您需要在電腦上安裝下列項目。

* Windows 和 Linux：
    - PATH 上的 git
* macOS：
    - PATH 上的 git
    - Xcode
    - Openssl

若要建置，請從根目錄執行 `build.cmd` (在 Windows 上) 或 `build.sh` (在 Linux 和 macOS 上)。 如果您不想要執行測試，請執行 `build.cmd /t:Compile` 或 `./build.sh /t:Compile`。 若要在 macOS Sierra 中建置 CLI，您必須執行 `export DOTNET_RUNTIME_ID=osx.10.11-x64` 來設定 DOTNET_RUNTIME_ID 環境變數。

### <a name="using-your-build"></a>使用您的組建

使用 *artifacts/{os}-{arch}/stage2* 中的 `dotnet` 可執行檔來試用新建置的 CLI。 如果您想要在從目前主控台叫用 `dotnet` 時使用建置輸出，您也可以將 *artifacts/{os}-{arch}/stage2* 新增至 PATH。

## <a name="see-also"></a>請參閱

* [.NET Core Common Language Runtime (CoreCLR)](https://github.com/dotnet/coreclr/blob/master/README.md)
* [.NET Core CLI 開發人員指南](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
* [.NET Core 發佈封裝](./distribution-packaging.md)
