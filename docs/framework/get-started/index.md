---
title: .NET Framework 使用者入門
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
ms.openlocfilehash: 8708fbd21967c5acb548e0e77ba5d9e060336c50
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345040"
---
# <a name="get-started-with-net-framework"></a>開始使用 .NET 框架

.NET 框架是管理目標 .NET 框架的應用的運行時執行環境。 其由通用語言執行平台及廣大的類別庫組成，前者提供記憶體管理和其他系統服務，後者則能讓程式設計人員將強固、可靠的程式碼善用於應用程式開發的所有主要領域。

> [!NOTE]
> .NET 框架僅在 Windows 系統上可用。 您可以使用[.NET Core](../../core/index.yml)在 Windows、MacOS 和 Linux 上開發和運行應用。

## <a name="what-is-net-framework"></a>什麼是 .NET 框架？

.NET 框架是 Windows 的託管執行環境，為正在運行的應用提供各種服務。 其由兩個主要元件組成：通用語言執行平台 (CLR) 和 .NET Framework 類別庫，前者是負責處理執行中應用程式的執行引擎，後者提供通過測試、可重複使用的程式碼程式庫，讓開發人員可從自己的應用程式中呼叫。 .NET Framework 為正在運行的應用提供的服務包括：

- 記憶體管理。 在許多程式設計語言中，程式設計人員負責配置和釋放記憶體，以及處理物件存留期。 在 .NET Framework 應用程式中，CLR 會代表應用程式提供這些服務。

- 一般型別系統。 在傳統的程式語言中，基本型別是由編譯器所定義，這會讓跨語言互通性變得很複雜。 在 .NET 框架中，基本類型由 .NET 框架類型系統定義，並且對於針對 .NET 框架的所有語言都是通用的。

- 廣泛類別庫。 程式設計人員不再需要撰寫大量的程式碼來處理常見的低階程式設計作業，而能夠使用 .NET Framework 類別庫中可立即存取的類型程式庫及其成員來完成這項工作。

- 開發架構和技術。 .NET 框架包括用於應用開發特定領域的庫，例如 Web 應用ASP.NET、資料訪問ADO.NET、面向服務的應用程式的 Windows 通信基礎以及 Windows 桌面應用的 Windows 演示基礎。

- 語言互通性。 目標 .NET Framework 的語言編譯器發出名為"通用中間語言 （CIL）"的中間代碼，而後者又在運行時由通用語言運行時編譯。 有了此功能，使用某一種語言撰寫的常式就能供其他語言存取，而程式設計人員也能使用自己慣用的語言專心建立應用程式。

- 版本相容性。 除了極少數例外情況外，使用特定版本的 .NET Framework 開發的應用在更高版本中無需修改即可運行。

- 並存執行。 .NET Framework 允許同一台電腦上存在公共語言運行時的多個版本，從而説明解決版本衝突。 這意味著多個版本的應用可以共存，並且應用可以在構建它的 .NET 框架版本上運行。 並存執行適用於.NET Framework 版本群組 1.0/1.1、2.0/3.0/3.5 和 4/4.5.x/4.6.x/4.7.x/4.8。

- 多目標。 將目標設為 [.NET Standard](../../standard/net-standard.md)，開發人員就能建立可在該標準版本所支援的多個 .NET Framework 平台上運作的類別庫。 例如，目標 .NET 標準 2.0 的庫可用於目標 .NET 框架 4.6.1、.NET 核心 2.0 和 UWP 10.0.16299 的應用。

<a name="ForUsers"></a>
## <a name="the-net-framework-for-users"></a>適用於使用者的 .NET Framework

如果不開發 .NET 框架應用，但使用它們，則不需要對 .NET 框架或其操作有特定知識。 在大多數情況下，框架對使用者是完全透明的。

如果您使用的是 Windows 作業系統，則您的電腦上可能已安裝了 .NET 框架。 此外，如果安裝需要 .NET 框架的應用，則該應用的安裝程式可能會在電腦上安裝框架的特定版本。 在某些情況下，您可能會看到一個對話方塊，要求您安裝 .NET 框架。 如果您剛剛嘗試在顯示此對話方塊時運行應用，並且您的電腦具有 Internet 存取權限，則可以轉到允許您安裝缺少版本的 .NET Framework 的網頁。 有關詳細資訊，請參閱[安裝指南](../install/index.md)。

通常，不應卸載電腦上安裝的 .NET 框架版本。 不這麼做的原因有兩個：

- 如果您使用的應用依賴于 .NET Framework 的特定版本，則如果刪除該版本，該應用可能會中斷。

- .NET 框架的某些版本是早期版本的就地更新。 例如，.NET Framework 3.5 是版本 2.0 的就地更新，.NET 框架 4.8 是版本 4 到 4.7.2 的就地更新。 如需詳細資訊，請參閱 [.NET Framework 版本和相依性](../migration-guide/versions-and-dependencies.md)。

在 Windows 8 之前的 Windows 版本上，如果選擇刪除 .NET 框架，請始終使用"控制台 **"的"程式和功能**"卸載它。 切勿手動刪除 .NET 框架的版本。 在 Windows 8 及上面，.NET Framework 是一個作業系統元件，無法獨立卸載。

.NET 框架的多個版本可以同時共存于一台電腦上。 這表示，您不需要解除安裝舊版，就可以直接安裝新版。

## <a name="net-framework-for-developers"></a>.NET 開發人員框架

如果您是開發人員，請選擇支援 .NET 框架的任何程式設計語言來創建應用。 由於 .NET Framework 提供語言獨立性和互通性，因此您與其他 .NET Framework 應用和元件交互，而不管它們使用何種語言。

若要開發 .NET Framework 應用程式或元件，請執行下列步驟：

1. 如果作業系統未預先安裝，請安裝應用將針對的 .NET 框架版本。 最新的生產版本是 .NET 框架 4.8。 它預先安裝在 Windows 10 五月 2019 更新，可在早期版本的 Windows 作業系統上下載。 如需 .NET Framework 系統需求，請參閱[系統需求](system-requirements.md)。 有關安裝 .NET 框架的其他版本的資訊，請參閱[安裝指南](../install/guide-for-developers.md)。 其他.NET Framework 套件會在頻外發行，也就是在任何定期或排程發行週期以外輪流發行。 有關這些包的資訊，請參閱[.NET 框架和帶外版本](the-net-framework-and-out-of-band-releases.md)。

2. 選擇要用於開發應用的 .NET 框架版本支援的語言或語言。 有多種語言可供選擇，包括 Microsoft 的 [Visual Basic](../../visual-basic/index.yml)[C#](../../csharp/index.yml)、[F#](../../fsharp/index.yml) 及 [C++/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp)。 （允許您為 .NET 框架開發應用的程式設計語言符合[通用語言基礎結構 （CLI） 規範](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/)。

3. 選取並安裝要用來建立應用程式，且支援所選程式設計語言的開發環境。 適用於 .NET Framework 應用程式的 Microsoft 整合式開發環境 (IDE) 為 [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)。 並有多個版本可供使用。

有關開發面向 .NET 框架的應用的詳細資訊，請參閱[開發指南](../development-guide.md)。

## <a name="related-articles"></a>相關文章

| Title | 描述 |
| ----- |------------ |
| [概觀](overview.md) | 為構建面向 .NET 框架的應用的開發人員提供詳細資訊。 |
| [安裝指南](../install/index.md) | 提供有關安裝 .NET 框架的資訊。 |  
| [.NET 框架和帶外版本](the-net-framework-and-out-of-band-releases.md) | 描述 .NET Framework 不定期發行以及如何在您的應用程式中使用它們。 |
| [系統要求](system-requirements.md) | 列出運行 .NET 框架的硬體和軟體要求。 |
| [.NET 的核心和開放原始碼](net-core-and-open-source.md) | 描述 .NET 核心與 .NET 框架的關係以及如何訪問開源 .NET Core 專案。 |
| [.NET Core 文件](../../core/index.yml) | 提供適用於 .NET Core 的概念性及 API 參考文件。 |
| [.NET Standard](../../standard/net-standard.md) | 討論 .NET 標準，這是單個 .NET 實現支援的版本化規範，可確保在多個平臺上提供一組一致的 API。

## <a name="see-also"></a>另請參閱

- [.NET Framework 指南](../index.yml)
- [新功能](../whats-new/index.md)
- [.NET API 瀏覽器](../../../api/index.md)
- [開發指南](../development-guide.md)
