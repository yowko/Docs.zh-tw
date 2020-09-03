---
title: .NET Framework 使用者入門
description: 開始使用 .NET，這是管理應用程式的執行時間執行環境。 它包含通用語言執行時間 (CLR) 和廣泛的類別庫。
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
ms.openlocfilehash: 85ba856fd695f264f75a6dab2dca3aded4e5cdc1
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414964"
---
# <a name="get-started-with-net-framework"></a>開始使用 .NET Framework

.NET Framework 是一種執行時間執行環境，負責管理以 .NET Framework 為目標的應用程式。 其由通用語言執行平台及廣大的類別庫組成，前者提供記憶體管理和其他系統服務，後者則能讓程式設計人員將強固、可靠的程式碼善用於應用程式開發的所有主要領域。

> [!NOTE]
> .NET Framework 只能在 Windows 系統上使用。 您可以使用 [.Net Core](../../core/introduction.md) 在 Windows、MacOS 和 Linux 上開發和執行應用程式。

## <a name="what-is-net-framework"></a>什麼是 .NET Framework？

.NET Framework 是適用于 Windows 的受控執行環境，可為執行中的應用程式提供各種服務。 其由兩個主要元件組成：通用語言執行平台 (CLR) 和 .NET Framework 類別庫，前者是負責處理執行中應用程式的執行引擎，後者提供通過測試、可重複使用的程式碼程式庫，讓開發人員可從自己的應用程式中呼叫。 .NET Framework 提供給執行中應用程式的服務包括下列各項：

- 記憶體管理。 在許多程式設計語言中，程式設計人員負責配置和釋放記憶體，以及處理物件存留期。 在 .NET Framework 應用程式中，CLR 會代表應用程式提供這些服務。

- 一般型別系統。 在傳統的程式語言中，基本型別是由編譯器所定義，這會讓跨語言互通性變得很複雜。 在 .NET Framework 中，基本類型是由 .NET Framework 類型系統所定義，而且是以 .NET Framework 為目標的所有語言通用。

- 廣泛類別庫。 程式設計人員不再需要撰寫大量的程式碼來處理常見的低階程式設計作業，而能夠使用 .NET Framework 類別庫中可立即存取的類型程式庫及其成員來完成這項工作。

- 開發架構和技術。 .NET Framework 包含特定應用程式開發領域的程式庫，例如 web 應用程式的 ASP.NET、適用于資料存取的 ADO.NET、服務導向應用程式的 Windows Communication Foundation，以及適用于 Windows 桌面應用程式的 Windows Presentation Foundation。

- 語言互通性。 以 .NET Framework 的語言編譯器會發出名為通用中繼語言 (CIL) 的中繼程式碼，而該程式碼會在執行時間由 common Language runtime 進行編譯。 有了此功能，使用某一種語言撰寫的常式就能供其他語言存取，而程式設計人員也能使用自己慣用的語言專心建立應用程式。

- 版本相容性。 在罕見的情況下，使用特定版本的 .NET Framework 開發的應用程式會在較新版本上執行，而不需要修改。

- 並存執行。 .NET Framework 可讓多個版本的 common language runtime 存在於同一部電腦上，以協助解決版本衝突。 這表示應用程式的多個版本可以並存，而且應用程式可以在其建立所在的 .NET Framework 版本上執行。 並存執行適用於.NET Framework 版本群組 1.0/1.1、2.0/3.0/3.5 和 4/4.5.x/4.6.x/4.7.x/4.8。

- 多目標。 將目標設為 [.NET Standard](../../standard/net-standard.md)，開發人員就能建立可在該標準版本所支援的多個 .NET Framework 平台上運作的類別庫。 例如，以 .NET Standard 2.0 為目標的程式庫可供以 .NET Framework 4.6.1、.NET Core 2.0 和 UWP 10.0.16299 為目標的應用程式使用。

<a name="ForUsers"></a>
## <a name="the-net-framework-for-users"></a>適用於使用者的 .NET Framework

如果您未開發 .NET Framework 的應用程式，但您使用這些應用程式，就不需要具備 .NET Framework 或其作業的特定知識。 大部分的情況下，架構對使用者來說都是完全透明的。

如果您使用的是 Windows 作業系統，.NET Framework 可能已安裝在您的電腦上。 此外，如果您安裝需要 .NET Framework 的應用程式，應用程式的安裝程式可能會在您的電腦上安裝特定版本的架構。 在某些情況下，您可能會看到對話方塊，要求您安裝 .NET Framework。 如果您在這個對話方塊出現時剛嘗試執行應用程式，而且您的電腦可以存取網際網路，您可以移至網頁，讓您安裝遺失的 .NET Framework 版本。 如需詳細資訊，請參閱 [安裝指南](../install/index.md)。

一般而言，您不應該卸載電腦上安裝的 .NET Framework 版本。 不這麼做的原因有兩個：

- 如果您使用的應用程式取決於特定的 .NET Framework 版本，則該應用程式可能會在該版本移除時中斷。

- 某些版本的 .NET Framework 是較舊版本的就地更新。 例如，.NET Framework 3.5 是2.0 版的就地更新，而 .NET Framework 4.8 是版本4到4.7.2 的就地更新。 如需詳細資訊，請參閱 [.NET Framework 版本和相依性](../migration-guide/versions-and-dependencies.md)。

在 Windows 8 之前的 Windows 版本中，如果您選擇移除 .NET Framework，請一律使用主控台的 [ **程式和功能** ] 將它卸載。 絕對不要手動移除版本的 .NET Framework。 在 Windows 8 和以上版本中，.NET Framework 是作業系統元件，無法獨立卸載。

多個版本的 .NET Framework 可以同時並存于單一電腦上。 這表示，您不需要解除安裝舊版，就可以直接安裝新版。

## <a name="net-framework-for-developers"></a>適用于開發人員的 .NET Framework

如果您是開發人員，請選擇支援 .NET Framework 的任何程式設計語言來建立您的應用程式。 由於 .NET Framework 提供語言獨立性和互通性，因此不論開發的語言為何，您都可以與其他 .NET Framework 應用程式和元件互動。

若要開發 .NET Framework 應用程式或元件，請執行下列步驟：

1. 如果未在您的作業系統上預先安裝，請安裝您的應用程式將作為目標的 .NET Framework 版本。 最新的生產版本是 .NET Framework 4.8。 它會預先安裝在 Windows 10 2019 年5月更新上，並可在舊版 Windows 作業系統上下載。 如需 .NET Framework 系統需求，請參閱[系統需求](system-requirements.md)。 如需安裝其他 .NET Framework 版本的詳細資訊，請參閱 [安裝指南](../install/guide-for-developers.md)。 其他.NET Framework 套件會在頻外發行，也就是在任何定期或排程發行週期以外輪流發行。 如需這些套件的詳細資訊，請參閱 [.NET Framework 和頻外發行](the-net-framework-and-out-of-band-releases.md)。

2. 選取您要用來開發應用程式的 .NET Framework 版本所支援的語言或語言。 有多種語言可供選擇，包括 Microsoft 的 [Visual Basic](../../visual-basic/index.yml)[C#](../../csharp/index.yml)、[F#](../../fsharp/index.yml) 及 [C++/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp)。  (一種程式設計語言，可讓您開發適用于 .NET Framework 的應用程式遵循 [通用語言基礎結構 (CLI) 規格](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/)。 ) 

3. 選取並安裝要用來建立應用程式，且支援所選程式設計語言的開發環境。 適用於 .NET Framework 應用程式的 Microsoft 整合式開發環境 (IDE) 為 [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)。 並有多個版本可供使用。

如需有關開發以 .NET Framework 為目標之應用程式的詳細資訊，請參閱 [開發指南](../development-guide.md)。

## <a name="related-articles"></a>相關文章

| Title | 描述 |
| ----- |------------ |
| [概觀](overview.md) | 針對建立以 .NET Framework 為目標之應用程式的開發人員，提供詳細的資訊。 |
| [安裝指南](../install/index.md) | 提供有關安裝 .NET Framework 的資訊。 |  
| [.NET Framework 和頻外版本](the-net-framework-and-out-of-band-releases.md) | 描述 .NET Framework 不定期發行以及如何在您的應用程式中使用它們。 |
| [系統需求](system-requirements.md) | 列出執行 .NET Framework 的硬體和軟體需求。 |
| [.NET 的核心和開放原始碼](net-core-and-open-source.md) | 描述 .NET Core 的相關 .NET Framework 以及如何存取開放原始碼 .NET Core 專案。 |
| [.NET Core 文件](../../core/introduction.md) | 提供適用於 .NET Core 的概念性及 API 參考文件。 |
| [.NET Standard](../../standard/net-standard.md) | 討論 .NET Standard，其為個別 .NET 執行所支援的版本規格，以保證可在多個平臺上使用一組一致的 Api。

## <a name="see-also"></a>另請參閱

- [.NET Framework 指南](../index.yml)
- [新功能](../whats-new/index.md)
- [.NET API 瀏覽器](../../../api/index.md)
- [開發指南](../development-guide.md)
