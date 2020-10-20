---
title: .NET Core for Desktop 有哪些新功能？
description: 深入瞭解 .NET Core、.NET Core 和 .NET Framework 之間的差異，以及已新增的新功能。
ms.date: 05/12/2020
ms.openlocfilehash: 796facaf8cd4f0d23fbcd04b90cb78fb28ebc465
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223640"
---
# <a name="whats-new-with-net-core-for-desktop"></a>.NET Core for Desktop 有哪些新功能？

從 .NET Core 3.0 開始，.NET Core 支援 Windows Forms 和 WPF。 因此，您現在可以在桌面應用程式的 .NET Framework 和 .NET Core 之間做選擇。 本章將說明什麼是 .NET Core，以及其對桌面應用程式的好處。

## <a name="the-motivation-behind-net-core"></a>.NET Core 背後的動機

因為它在2002中推出，.NET Framework 已發展多年來支援許多技術，例如 Windows Forms、ASP.NET、Entity Framework、Windows Store 和其他許多技術。 這些都是不同的本質。 因此，藉由取得部分 .NET Framework，並為每項技術建立不同的應用程式堆疊，Microsoft 就已達到這項演進。 如此一來，就可以根據特定堆疊的需求來自訂開發功能，以將每個平臺的潛能發揮到最大。 這會導致不同獨立團隊所維護的 .NET Framework 版本分散。 這些堆疊都有一個共通的結構，其中包含應用程式模型、架構和執行時間，但在每個元件的執行中都不同。

如果您只以上述其中一個平臺為目標，則可以使用此模型。 不過，在許多情況下，您可能需要在相同的方案中有多個目標平臺。 例如，您的應用程式可能會有桌面系統管理員的一部分，這是一個用戶端的網站，可共用在伺服器上執行的後端邏輯，甚至是行動用戶端。 在此情況下，您需要統一的程式碼撰寫體驗，以跨越所有的 .NET 縱向。

在 Windows 8 發行時， (Pcl) 的便攜類別庫概念。 一開始，.NET Framework 的設計是假設它一律會部署為單一單位，因此不會考慮 [分解](https://wikipedia.org/wiki/Decomposition_(computer_science)) 。 若要面對在縱向之間共用程式碼的問題，推動的推動力在於如何重構架構。 合約的概念是提供妥善要素的 API 介面區。 合約只是您針對進行編譯的元件，並以適當的分解方式設計，以考慮它們之間的相依性。

這會導致在元件層級的水準點之間進行 API 差異的原因，而不是之前的個別 API 層級。 此層面啟用了可將目標設為多個縱向的類別庫體驗，也稱為「便攜類別庫」。

![.NET Framework 的發行歷程記錄](./media/whats-new-dotnet-core/release-history.png)

透過 PCL，開發的體驗會根據 API 圖形在各方面整合。 此外，也會解決在不同的縱向建立程式庫的最緊迫需求。 但有一個很棒的挑戰：只有在所有縱向的進展都在執行時，才可移植 Api。

更好的方法是藉由提供妥善要素的執行，而不是妥善考慮的觀點，來跨縱向整合各項。 您可以更輕鬆地要求每個擁有特定元件的團隊，思考其 Api 在所有縱向的運作方式，而不是嘗試追溯在最上層提供一致的 API 堆疊。 這就是 .NET Standard 的來源。 請參閱下一節的詳細資料。

另一項很大的挑戰就是如何部署 .NET Framework。 .NET Framework 是全電腦的架構。 對它所做的任何變更都會影響相依于其上的所有應用程式。 雖然此部署模型有許多優點，例如減少磁碟空間和集中存取服務，但它會呈現一些陷阱。

從開始，應用程式開發人員很難依賴最近發行的架構。 他們必須依賴最新的 OS，或提供可安裝 .NET Framework 的應用程式安裝程式以及應用程式。 如果您是 網頁程式開發人員，您甚至可能無法使用此選項，因為 IT 部門會建立伺服器支援的版本。

即使您願意在 .NET Framework 安裝程式中提供安裝程式的麻煩，您可能會發現升級 .NET Framework 可能會中斷其他應用程式。

雖然能夠提供回溯相容版本的架構，但仍有相容的變更可以中斷應用程式。 例如，將介面新增至現有的型別可能會變更此類型的序列化方式，並根據現有的程式碼造成中斷的問題。 因為 .NET Framework 安裝的基礎很大，所以對抗這些中斷案例會減緩 .NET Framework 內創新的步調。

為了解決這些問題，Microsoft 開發了 .NET Core 來處理 .NET 平臺的演進。

## <a name="introduction-to-net-core"></a>.NET Core 簡介

.NET Core 是 Microsoft .NET 技術發展成模組化、跨平臺、開放原始碼和雲端就緒平臺的演進。 它會在 Windows、macOS 和 Linux 上執行，並計畫也可在以 ARM 為基礎的架構（例如 Android 和 IoT）上執行。

.NET Core 的目的是為所有類型的應用程式（包括 Windows、跨平臺和行動應用程式）提供統一的平臺。 [.NET Standard](../../standard/net-standard.md) 藉由提供共用基底 api （每個應用程式模型所需），以及排除任何應用程式模型專屬 api 來啟用此功能。

此架構可讓應用程式在效率和效能方面有許多優點，並簡化不同支援平臺的封裝和部署。

.NET Core 的優點來自這三個特性：

- **跨平臺：** 它可讓應用程式在不同的平臺上執行， (Windows、macOS 和 Linux) 。
- **開放原始碼：** .net Core 平臺是開放原始碼，可透過 GitHub 取得，以促進透明度和投稿貢獻。
- **支援：** Microsoft 正式支援 .NET Core。

從 .NET Core 3.0 開始，除了現有的 web 和雲端支援之外，還支援桌面、IoT 和 AI 網域。 此架構的目標相當令人印象深刻：將所有 .NET 開發類型的目標設為目標，並提供未來。 Microsoft 計畫在2020結束時，使用 .NET 5 來完成這項願景。 已移除「核心」名稱，以強化其在 .NET 世界中的唯一性。

![.NET 5 的所有網域](./media/whats-new-dotnet-core/all-domains-of-dotnet5.png)

## <a name="net-framework-vs-net-core"></a>.NET Framework 與 .NET Core 的比較

現在您已瞭解 .net Core 在 .NET 的 Microsoft 策略中的相關性，您可能會想知道 .NET Framework 會發生什麼事。 您可能會詢問類似下列的問題：您是否必須放棄？ 即將消失嗎？ 我可以選擇將我的 .NET Framework 應用程式現代化？

在2019中，已發行 **.NET Framework-4.8** 的最後一個版本。 它包含桌面應用程式的三項主要增強功能：

- **新式瀏覽器和媒體控制項**：現今，.net 桌面應用程式會使用 Internet Explorer 和 Windows Media Player 來顯示 HTML 及播放媒體檔案。 由於這些舊版控制項不會顯示最新的 HTML 或播放最新的媒體檔案，因此新增的控制項可利用支援最新標準的 Microsoft Edge 和較新的媒體播放機。
- **Uwp 控制項的存取**： uwp 包含的新控制項可利用最新的 Windows 功能和觸控顯示。 您不必重寫應用程式來使用這些新的功能和控制項，因此您可以在現有的 WPF 或 Windows Forms 程式碼中使用這些新功能。
- **高 DPI 增強功能**：顯示器的解析度會增加到4K 和8k 解析度。 因此，.NET Framework 4.8 加入了新的 HDPI 改進，以確保您現有的 Windows Forms 和 WPF 應用程式在這些新的顯示器上都能美觀。

由於 .NET Framework 安裝在數百萬部電腦上，因此 Microsoft 將繼續支援它，但不會新增新功能。

.NET Core 是 .NET 的開放原始碼、跨平臺和快速移動版本。 因為其並存本質，所以不需要擔心中斷任何應用程式，就可以進行變更。 這表示，.NET Core 會在一段時間內取得新的 Api 和語言功能，.NET Framework 不會這麼做。 此外， **.Net Core** 已經有 .NET Framework 無法執行的功能，例如：

- **支援 Windows Forms 和 WPF 的 .Net 並存版本**：這可在更新電腦的 framework 版本時解決副作用的問題。 您可以在相同的電腦上安裝多個版本的 .NET Core，且每個應用程式會指定其應使用的 .NET Core 版本。 更多，現在您可以在 .NET Core 上開發和執行 Windows Forms 和 WPF。
- 將 **.net 直接內嵌至應用程式**：您可以將 .net Core 部署為應用程式封裝的一部分。 這可讓您利用最新版本、功能和 Api，而不需要等到電腦上安裝特定版本。
- 利用 **.Net core 功能**： .net core 是 .net 的快速移動、開放原始碼版本。 其並存本質讓您能夠快速導入新的創新 Api 和基類庫 (BCL) 改進，而不會有中斷性的風險。 現在 Windows Forms 和 WPF 應用程式可以利用最新的 .NET Core 功能，其中也包含了執行時間效能、高 DPI 支援等的更多基本修正。

Microsoft 藍圖的重要部分是讓開發人員輕鬆地將應用程式移至 .NET Core，並且在未來進入 .NET 5。 但是，如果您有現有的 .NET Framework 應用程式，則您不應該覺得迫移至 .NET Core。 .NET Framework 會受到完整支援，而且一律會是 Windows 的一部分。 但是，如果您未來想要使用最新的語言功能和 Api，您必須將應用程式移至 .NET Core。

針對全新的桌面應用程式，建議您直接從 .NET Core 開始。 它是羽量級和跨平臺、並存執行、具有高效能，而且完全符合容器和微服務架構。

![您可以使用最新的 .NET Framework 版本，或將您的應用程式移植到 .NET Core，來更新 .NET Framework 應用程式](./media/whats-new-dotnet-core/framework-vs-core.png)

## <a name="net-standard-vs-pcl"></a>.NET Standard 與 PCL

[.NET Standard](../../standard/net-standard.md) 是適用于所有 .net 執行的正式 .net api 規格。 .NET Standard 背後的動機是在 .NET 生態系統中建立更高的一致性。 .NET Standard 是一種 .NET Api 規格，可組成一組統一的合約以編譯器代碼。 這些合約會在每個 .NET 類別中執行，因此可跨不同的 .NET 實作為可攜性。

.NET Standard 可提供下列主要案例：

- 定義適用于所有 .NET 實作為的統一基類庫 Api 集合，與工作負載無關。
- 可讓開發人員使用這組相同的 API，產生可跨 .NET 實作使用的可攜式程式庫。

.NET Standard 是 Pcl 的演進，下列清單顯示 .NET Standard 與 Pcl 之間的基本差異：

- .NET Standard 是一組由 Microsoft 挑選的策劃 Api。 Pcl 不是。
- PCL 所包含的 Api 相依于您在建立時選擇要設為目標的平臺。 這可讓您選擇的特定目標只能共用 PCL。
- .NET Standard 與平臺無關，可以在 Windows、macOS、Linux 等任何地方執行。
- Pcl 也可以跨平臺執行，但其觸及範圍也會更有限。 Pcl 只能以一組有限的平臺為目標。

## <a name="new-desktop-features-in-net-core"></a>.NET Core 中的新桌面功能

### <a name="support-for-windows-forms-and-wpf"></a>支援 Windows Forms 和 WPF

從3.0 版開始，Windows Forms 和 WPF 是 .NET Core 的一部分。 這兩種展示架構僅適用于 Windows，因此它們不是跨平臺。 您可以將 WPF 視為透過 DirectX 的豐富層次，並 Windows Forms 為透過 GDI + 更精簡的層級。 WPF 和 Windows Forms 在 Windows 中提供許多桌面應用程式的功能，因此是很好的工作。 因此 Windows Forms 和 WPF 適用于 .NET Core 和 .NET Framework。 現在您可以開始新的桌面應用程式，以 .NET Core 為目標，並將現有的應用程式從 .NET Framework 遷移至 .NET Core。

新版本的 .NET Standard 2.1 版，與 .NET Core 3.0 同時發行。 如預期，.NET Core 3.x 版本支援 .NET Standard 2.1 及更早版本。

此外，請務必注意，.NET Core 的 Windows Forms 和 WPF 執行都是開放原始碼。

### <a name="xaml-islands"></a>XAML Islands

[XAML 孤島](/windows/apps/desktop/modernize/xaml-islands) 是一組元件，可讓開發人員使用新的 Windows 10 控制項， (UWP XAML 控制項在其目前的 WPF、Windows Forms 和原生 Win32 應用程式中) ， (例如 MFC) 。 您可以在任何想要的 Win32 應用程式內部，使用 UWP XAML 控制項的「孤島」。

這些 XAML 孤島可能是因為 Windows 10 1903 版引進了一組 Api，可讓您使用 Windows 處理常式 (Hwnd) ，在 Win32 視窗中裝載 UWP XAML 內容。 請注意，只有在 Windows 10 1903 和更新版本上執行的應用程式可以使用 XAML 孤島。

為了讓 Windows Forms 和 WPF 開發人員更輕鬆地建立 XAML 孤島，Windows 社群工具組會在數個 NuGet 套件中引進一組 .NET 包裝函式。 這些包裝函式是包裝的和裝載控制項：

- [Web](/windows/communitytoolkit/controls/wpf-winforms/webview)程式設計、 [WebViewCompatible](/windows/communitytoolkit/controls/wpf-winforms/webviewcompatible)、 [InkCanvas](/windows/communitytoolkit/controls/wpf-winforms/inkcanvas)、 [MediaPlayerElement](/windows/communitytoolkit/controls/wpf-winforms/mediaplayerelement)和[隨 mapcontrol](/windows/communitytoolkit/controls/wpf-winforms/mapcontrol)包裝的控制項將某些 UWP XAML 控制項包裝成 WINDOWS FORMS 或 WPF 控制項，為這些開發人員隱藏 uwp 概念。
- Windows Forms 和 WPF 的 [WindowsXamlHost](/windows/communitytoolkit/controls/wpf-winforms/windowsxamlhost) 控制項可讓其他未包裝的 UWP XAML 控制項和自訂控制項可以載入至 XAML 島中。

### <a name="access-to-all-windows-10-apis"></a>存取所有 Windows 10 Api

Windows 10 有大量的 API 可供開發人員使用。 這些 Api 可讓您存取各種功能，例如驗證、藍牙、約會及連絡人。 這些 Api 現在透過 .NET Core 公開，讓 Windows 開發人員有機會利用 Windows 10 上的功能，建立功能強大的桌面應用程式。

### <a name="side-by-side-support-and-self-contained-exes"></a>並存支援和獨立 Exe

.NET Core 部署模型是 Windows 桌面開發人員使用 .NET Core 所體驗到的最大好處之一。 全域安裝 .NET Core 的能力提供 .NET Framework 的許多相同集中安裝和服務優點，而不需要就地更新。

當新的 .NET Core 版本發行時，您可以視需要更新電腦上的每個應用程式，而不會影響其他應用程式。 新的 .NET Core 版本是安裝在它們自己的目錄中，並且彼此並存。

如果您需要使用隔離來部署，您可以使用您的應用程式部署 .NET Core。 .NET Core 會將您的應用程式與 .NET Core 執行時間組合在同一個可執行檔中。

開發人員要求這些部署選項相當長一段時間，但很難使用 .NET Framework 來達成。 .NET Core 所使用的模組化架構可讓這些彈性的部署選項變得可行。

### <a name="performance"></a>效能

因為它的起點是以 web 和雲端工作負載為目標，所以 .NET Core 已將效能插入其 DNA 中。 伺服器端程式碼的效能必須足以滿足高並行情況和 .NET Core 分數，以作為市場中最佳的效能 web 平臺。

當您使用 .NET Core 建立新一代的桌面應用程式時，可以利用這些效能改進。

## <a name="benefits-of-open-source"></a>開放原始碼的優點

.NET Core 是開放原始碼的幾個字。 建立跨平臺堆疊是一項複雜的工作，需要在每個目標平臺上進行特殊團隊的互動。 這項工作需要 Microsoft 內部和外部的許多共同作業。 藉由使其成為開放原始碼，並開放給公共共同作業，您可以取得最終的敏捷式開發樣式，進而提高品質，因為開發人員會發現問題。

這是 .NET Core 的關鍵成功因素，可繼續加速先前提及的藍圖：成為任何開發人員都必須建立任何應用程式的單一 .NET 平臺。

>[!div class="step-by-step"]
>[上一個](why-modern-applications.md) 
>[下一步](migrate-modern-applications.md)
