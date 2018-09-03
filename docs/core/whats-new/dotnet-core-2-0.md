---
title: .NET Core 2.0 的新功能
description: 了解 .NET Core 所提供的新功能。
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.openlocfilehash: 02aac2dab2b892927c0c98fae30bb287a6e24ad6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43456883"
---
# <a name="whats-new-in-net-core-20"></a>.NET Core 2.0 的新功能

.NET Core 2.0 包含針對下列區域的增強與新功能：

- [工具](#tooling)
- [語言支援](#language-support)
- [平台改善](#platform-improvements)
- [API 變更](#api-changes-and-library-support)
- [Visual Studio 整合](#visual-studio-integration)
- [文件改善](#documentation-improvements)

## <a name="tooling"></a>Tooling

### <a name="dotnet-restore-runs-implicitly"></a>dotnet restore 以隱含方式執行

在舊版的 .NET Core 中，您在使用 [dotnet new](../tools/dotnet-new.md) 命令建立新專案之後，以及將新的相依性新增至專案時，都必須立即執行 [dotnet restore](../tools/dotnet-restore.md) 命令以下載相依性。

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

您也可以透過將 `--no-restore` 參數傳遞至 `new`、`run`、`build`、`publish`、`pack`，以及 `test` 命令，來停用 `dotnet restore` 的自動引動過程。

### <a name="retargeting-to-net-core-20"></a>將目標重定至 .NET Core 2.0

如果已安裝 .NET Core 2.0 SDK，原先以 .NET Core 1.x 為目標的專案可以將目標重定至 .NET Core 2.0。

若要將目標重定至 .NET Core 2.0，請透過將 `<TargetFramework>` 元素 (在專案檔中具有多個目標的情況下則是 `<TargetFrameworks>` 元素) 的值從 1.x 變更至 2.0 來編輯專案檔：

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

您也可以用相同的方式，將目標從 .NET Standard 程式庫重定至 .NET Standard 2.0：

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

如需將專案移轉至 .NET Core 2.0 的詳細資訊，請參閱[從 ASP.NET Core 1.x 移轉至 ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index)。

## <a name="language-support"></a>語言支援

.NET Core 2.0 除了支援 C# 和 F# 之外，也支援 Visual Basic。

### <a name="visual-basic"></a>Visual Basic

.NET Core 2.0 現已支援 Visual Basic 2017。 您可以使用 Visual Basic 建立下列專案類型：

- .NET Core 主控台應用程式
- .NET Core 類別庫
- .NET Standard 類別庫
- .NET Core 單元測試專案
- .NET Core xUnit 測試專案

例如，若要建立 Visual Basic "Hello World" 應用程式，請從命令列執行下列步驟：

1. 開啟主控台視窗，建立專案的目錄，並將其設為目前的目錄。

1. 輸入 `dotnet new console -lang vb` 命令。

   該命令會建立具有 `.vbproj` 副檔名的專案檔，以及名為 *Program.vb* 的 Visual Basic 原始程式碼檔。 此檔案包含將 "Hello World!" 字串寫入至主控台視窗的原始程式碼。

1. 輸入 `dotnet run` 命令。 [.NET Core CLI](../tools/index.md) 會自動編譯並執行應用程式，該應用程式則會在主控台視窗中顯示 "Hello World!" 。

### <a name="support-for-c-71"></a>針對 C# 7.1 的支援

.NET Core 2.0 支援 C# 7.1，此版本加入了數個新的功能，包括：

- `Main` 方法 (應用程式進入點) 可以使用 [async](../../csharp/language-reference/keywords/async.md) 關鍵字進行標記。
- 推斷的元組名稱。
- 預設運算式。

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a>平台改善

.NET Core 2.0 包含可以更輕鬆地安裝 .NET Core 並在支援的作業系統上使用它的數個功能。

### <a name="net-core-for-linux-is-a-single-implementation"></a>適用於 Linux 的 .NET Core 為單一實作

.NET Core 2.0 提供可在多個 Linux 發行版本上運作的單一 Linux 實作。 .NET Core 1.x 需要您下載發行版本特定的 Linux 實作。

您也可以開發以單一作業系統形式的 Linux 作為目標的應用程式。 .NET Core 1.x 需要您個別以每個 Linux 發行版本作為目標。

### <a name="support-for-the-apple-cryptographic-libraries"></a>針對 Apple 加密編譯程式庫的支援

.NET Core 1.x 在 macOS 上需要 OpenSSL 工具組的加密編譯程式庫。 .NET Core 2.0 使用 Apple 加密編譯程式庫，且不需要 OpenSSL，因此您已不必安裝它。

## <a name="api-changes-and-library-support"></a>API 變更和程式庫支援

### <a name="support-for-net-standard-20"></a>針對 .NET Standard 2.0 的支援

.NET Standard 會定義一組必須在符合該標準版本之 .NET 實作上提供的已建立版本 API。 .NET Standard 是以程式庫開發人員為目標。 它的目的在於針對每個 .NET 實作上以 .NET Standard 的某個版本為目標的程式庫，保證程式庫中所能使用的功能。 .NET Core 1.x 支援 .NET Standard 1.6 版，.NET Core 2.0 則支援最新 .NET Standard 2.0 版。 如需詳細資訊，請參閱 [.NET Standard](../../standard/net-standard.md)。

除了 .NET Standard 1.6 原先所提供的 API 之外，.NET Standard 2.0 更包含了超過 20,000 個額外的 API。 我們主要是透過將 .NET Framework 和 Xamarin 的常見 API 合併至 .NET Standard，來對介面區進行擴展。

.NET Standard 2.0 類別庫也可以參考 .NET Framework 類別庫，前提是這些類別庫必須呼叫存在於 .NET Standard 2.0 中的 API。 不需要對 .NET Framework 程式庫進行任何重新編譯。

如需於 .NET Standard 1.6 之後新增至 .NET Standard 的 API 清單，請參閱 [.NET Standard 2.0 與1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md) \(英文\)。

### <a name="expanded-surface-area"></a>擴展的介面區

.NET Core 2.0 上的可用 API 總數，比 .NET Core 1.1 所提供的 API 多出了超過一倍的數量。

而從 .NET Framework 移植 [Windows 相容性套件](../porting/windows-compat-pack.md)也會變得簡單許多。

### <a name="support-for-net-framework-libraries"></a>針對 .NET Framework 程式庫的支援

.NET Core 程式碼可以參考現有的 .NET Framework 程式庫，包括現有的 NuGet 套件。 請注意，程式庫必須使用 .NET Standard 所提供的 API。

## <a name="visual-studio-integration"></a>Visual Studio 整合

Visual Studio 2017 15.3 版 (以及某些情況下的 Visual Studio for Mac) 能為 .NET Core 開發人員提供數個顯著的增強功能。

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a>重定 .NET Core 應用程式和 .NET Standard 程式庫的目標

如果已安裝 .NET Core 2.0 SDK，您可以將 .NET Core 1.x 專案的目標重定至 .NET Core 2.0，並將 .NET Standard 1.x 程式庫的目標重定至 .NET Standard 2.0。

若要在 Visual Studio 中重定專案的目標，請開啟專案屬性對話方塊的 [應用程式] 索引標籤，並將 [目標 Framework] 的值變更為 [.NET Core 2.0] 或 [.NET Standard 2.0]。 另一個變更它的方法，則是以滑鼠右鍵按一下專案並選取 [編輯 \*.csproj 檔案] 選項。 如需詳細資訊，請參閱本主題稍早的[工具](#tooling)小節。

### <a name="live-unit-testing-support-for-net-core"></a>.NET Core 的即時單元測試支援

每當您修改程式碼時，Live Unit Testing 會在背景自動執行任何受影響的單元測試，並會在 Visual Studio 環境中呈現即時的結果和程式碼涵蓋範圍。 .NET Core 2.0 現已支援 Live Unit Testing。 先前 Live Unit Testing 僅針對 .NET Framework 應用程式提供。

如需詳細資訊，請參閱 [Visual Studio 2017 的 Live Unit Testing](/visualstudio/test/live-unit-testing) 及 [Live Unit Testing 常見問題集](/visualstudio/test/live-unit-testing-faq)。

### <a name="better-support-for-multiple-target-frameworks"></a>更佳的多目標 Framework 支援

如果您正在針對多目標 Framework 建置專案，現在已可以從最上層功能表選取目標平台。 在下圖中，名為 SCD1 的專案是以 64 位元的 macOS X 10.11 (`osx.10.11-x64`)，以及 64 位元的 Windows 10/Windows Server 2016 (`win10-x64`) 為目標。 您可以在選取專案按鈕 (在此情況下為執行偵錯組建) 之前選取目標 Framework。

![於建置專案時選取目標 Framework](media/multitarget.png)

### <a name="side-by-side-support-for-net-core-sdks"></a>針對 .NET Core SDK 的並存功能支援

您現在可以獨立於 Visual Studio 安裝 .NET Core SDK。 這可以讓單一版本的 Visual Studio 建置以不同 .NET Core 版本為目標的專案。 在此之前，Visual Studio 和 .NET Core SDK 必須緊密關聯，只有特定版本的 SDK 才能搭配特定版本的 Visual Studio。

## <a name="documentation-improvements"></a>文件改善

### <a name="net-application-architecture"></a>.NET 應用程式架構

[.NET 應用程式架構](https://www.microsoft.com/net/learn/architecture)可讓您存取一系列針對使用 .NET 進行建置提供指引、最佳做法和範例應用程式的電子書：

- [微服務和 Docker 容器](../../standard/microservices-architecture/index.md)
- [使用 ASP.NET 的 Web 應用程式](../../standard/modern-web-apps-azure-architecture/index.md)
- [使用 Xamarin 的行動應用程式](/xamarin/xamarin-forms/enterprise-application-patterns/index.md)
- [使用 Azure 部署至雲端的應用程式](/azure/architecture/reference-architectures/index.md)

## <a name="see-also"></a>另請參閱

* [ASP.NET Core 2.0 的新功能](/aspnet/core/aspnetcore-2.0)
