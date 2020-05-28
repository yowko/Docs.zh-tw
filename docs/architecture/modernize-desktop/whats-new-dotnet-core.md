---
title: .NET Core for Desktop 有哪些新功能？
description: 瞭解 .NET Core、.NET Core 和 .NET Framework 之間的差異，以及已新增的新功能。
ms.date: 05/12/2020
ms.openlocfilehash: b4fc0cb2841fe13b000223aefc5eaf63bd911994
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144260"
---
# <a name="whats-new-with-net-core-for-desktop"></a>.NET Core for Desktop 有哪些新功能？

從 .NET Core 3.0 開始，.NET Core 支援 Windows Forms 和 WPF。 因此，您現在可以選擇桌面應用程式的 .NET Framework 和 .NET Core。 本章將說明什麼是 .NET Core，以及桌面應用程式的優點。

## <a name="the-motivation-behind-net-core"></a>.NET Core 背後的動機

從2002開始，.NET Framework 已演進多年來支援許多技術，例如 Windows Forms、ASP.NET、Entity Framework、Windows Store 等等。 它們本質上都不同。 因此，Microsoft 藉由取得部分 .NET Framework，並為每項技術建立不同的應用程式堆疊，而達到此演進。 如此一來，就可以針對特定堆疊的需求自訂開發功能，以將每個平臺的潛能最大化。 這會導致不同獨立小組所維護之 .NET Framework 版本的片段分散。 所有這些堆疊都有一個通用結構，其中包含應用程式模型、架構和執行時間，但它們在每個元件的執行中都不同。

如果您的目標只是其中一個平臺，您可以使用此模型。 不過，在許多情況下，您可能需要在相同的方案中有一個以上的目標平臺。 例如，您的應用程式可能會有桌面系統管理部分，也就是客戶面向的網站，它會共用在伺服器上執行的後端邏輯，甚至是行動用戶端。 在這種情況下，您需要統一的程式碼撰寫經驗，以橫跨所有此 .NET 縱向。

在 Windows 8 發行時，可移植的類別庫（Pcl）的概念已出生。 一開始，.NET Framework 的設計是假設它一律會部署為單一單位[，因此不](https://wikipedia.org/wiki/Decomposition_(computer_science))會有任何顧慮。 為了面對各種中間程式碼共用的問題，駕駛力是關於如何重構架構。 合約的概念是提供一個妥善要素的 API 介面區。 合約只是您針對編譯的元件，並以適當的分解來設計，以負責處理它們之間的相依性。

這會導致在元件層級的各個領域之間的 API 差異，而不是我們之前所用的個別 API 層級。 這個層面啟用了可鎖定多個縱向（也稱為可移植類別庫）的類別庫體驗。

![.NET Framework 的發行歷程記錄](./media/whats-new-dotnet-core/release-history.png)

使用 PCL 時，開發的體驗會根據 API 圖形，在各垂直間整合。 此外，也會解決在不同的縱向建立程式庫所需的最緊迫需求。 但有一個很大的挑戰：只有在跨所有的橫向移動應用程式時，Api 才可攜。

較好的方法是藉由提供一個完整的執行方式，而不是完整的視圖，藉以統一各個不同的整合。 您可以更輕鬆地要求每個擁有特定元件的小組，考慮其 Api 在所有的範圍內的工作方式，而不是嘗試追溯在最上層提供一致的 API 堆疊。 這就是 .NET Standard 的進入位置。 請參閱下一節的詳細資料。

另一個很大的挑戰就是如何部署 .NET Framework。 .NET Framework 是全電腦架構。 對其進行的任何變更都會影響所有相依于它的應用程式。 雖然此部署模型有許多優點，例如減少磁碟空間，以及集中存取服務，但它卻呈現一些陷阱。

一開始，應用程式開發人員很難以依賴最近發行的架構。 他們必須依賴最新的 OS，或提供安裝 .NET Framework 的應用程式安裝程式以及應用程式。 如果您是 網頁程式開發人員，即使 IT 部門建立了伺服器支援的版本，您可能還沒有這個選項。

即使您願意在 .NET Framework 設定中提供安裝程式的麻煩，也可能會發現升級 .NET Framework 可能會中斷其他應用程式。

雖然提供了回溯相容版本的架構，但仍有相容的變更可中斷應用程式。 例如，將介面新增至現有的類型，可以變更此類型的序列化方式，並根據現有的程式碼造成中斷的問題。 由於 .NET Framework 安裝的基礎非常龐大，因此對抗這些中斷案例會減緩 .NET Framework 內創新的步調。

為了解決所有這些問題，Microsoft 開發了 .NET Core 來處理 .NET 平臺的演進。

## <a name="introduction-to-net-core"></a>.NET Core 簡介

.NET Core 是 Microsoft .NET 技術發展成模組化、跨平臺、開放原始碼，以及雲端就緒的平臺。 它會在 Windows、macOS 和 Linux 上執行，且計畫也會在以 ARM 為基礎的架構（例如 Android 和 IoT）上執行。

.NET Core 的目的是為所有類型的應用程式提供統一的平臺，包括 Windows、跨平臺和行動應用程式。 [.NET Standard](../../standard/net-standard.md)提供每個應用程式模型所需的共用基底 api，並排除任何應用程式模型特定的 api，即可達成此目標。

此架構讓應用程式在效率和效能方面有許多好處，簡化了不同支援平臺中的封裝和部署。

.NET Core 的優點來自這三個特性：

- **跨平臺：** 它允許在不同的平臺（Windows、macOS 和 Linux）上執行應用程式。
- **開放原始碼：** .net Core 平臺是開放原始碼，可透過 GitHub 取得，並促進透明度和社會貢獻。
- **支援：** Microsoft 正式支援 .NET Core。

從 .NET Core 3.0 開始，除了現有的 web 和雲端支援之外，也支援桌面、IoT 和 AI 網域。 此架構的目標相當令人印象深刻：目標是每一種類型的 .NET 開發都是以目前和未來為目標。 Microsoft 計畫在2020結束時使用 .NET 5 來完成這項願景。 已移除「核心」名稱，以加強其在 .NET world 中的唯一性。

![.NET 5 的所有網域](./media/whats-new-dotnet-core/all-domains-of-dotnet5.png)

## <a name="net-framework-vs-net-core"></a>.NET Framework 與 .NET Core 的比較

現在您已瞭解適用于 .NET 的 Microsoft 策略中 .NET Core 的相關性，您可能會想知道 .NET Framework 會發生什麼事。 您可能會提出問題，例如：您是否必須放棄？ 它會消失嗎？ 我有哪些選擇可以將 .NET Framework 的應用程式現代化？

在2019中，已發行 **.NET Framework-4.8**的最後一個版本。 其中包含三個桌面應用程式的主要改良功能：

- **新式瀏覽器和媒體控制項**：現今，.net 桌面應用程式會使用 Internet Explorer 和 Windows 媒體播放機來顯示 HTML 和播放媒體檔案。 因為這些舊版控制項不會顯示最新的 HTML 或播放最新的媒體檔案，所以新增了新的控制項，以利用支援最新標準的 Microsoft Edge 和較新的媒體播放機。
- **Uwp 控制項的存取權**： uwp 包含新的控制項，可利用最新的 Windows 功能和觸控顯示。 您不需要重寫應用程式，就能使用這些新功能和控制項，因此您可以在現有的 WPF 或 Windows Forms 程式碼中使用這些新功能。
- **高 DPI 改善**：顯示器的解析度會增加到4K 和8k 解析度。 因此，.NET Framework 4.8 加入了新的 HDPI 改良功能，以確保您現有的 Windows Forms 和 WPF 應用程式在這些新的顯示器上看起來都很棒。

由於 .NET Framework 安裝在數百萬部電腦上，Microsoft 將繼續支援它，但不會新增功能。

.NET Core 是 .NET 的開放原始碼、跨平臺和快速移動版本。 因為其並存，所以不需要擔心中斷任何應用程式，就可以進行變更。 這表示 .NET Core 會在一段時間內取得新的 Api 和語言功能，.NET Framework 不會這麼做。 此外， **.Net Core**已經有 .NET Framework 可能無法執行的功能，例如：

- **支援 Windows Forms 和 WPF 的 .Net 並存版本**：這可解決更新機器的 framework 版本時的副作用問題。 多個版本的 .NET Core 可以安裝在同一部電腦上，而每個應用程式會指定應該使用的 .NET Core 版本。 更多，現在您可以在 .NET Core 之上開發和執行 Windows Forms 和 WPF。
- 將 **.net 直接內嵌至應用程式**：您可以將 .net Core 部署為應用程式套件的一部分。 這可讓您利用最新版本、功能和 Api，而不需要等候電腦上安裝特定版本。
- **利用 .Net core 功能**： .net core 是 .net 的快速移動、開放原始碼版本。 其並存特性可讓您快速引進新的創新 Api 和基類庫（BCL）改良功能，而不會有中斷相容性的風險。 現在 Windows Forms 和 WPF 應用程式都可以利用最新的 .NET Core 功能，其中也包含適用于執行時間效能、高 DPI 支援等等的更基本修正程式。

Microsoft 藍圖的重要部分是讓開發人員能夠輕鬆地將應用程式移至 .NET Core，並在未來進入 .NET 5。 但是，如果您已經有 .NET Framework 的應用程式，您應該不會覺得受到要移至 .NET Core。 .NET Framework 將受到完整支援，而且一律會成為 Windows 的一部分。 不過，如果您未來想要使用最新的語言功能和 Api，您必須將應用程式移至 .NET Core。

針對全新的桌面應用程式，我們建議您直接從 .NET Core 開始。 它是輕量且跨平臺、並存執行、具有高效能，而且完全符合容器和微服務架構。

![您可以使用最新的 .NET Framework 版本更新 .NET Framework 應用程式，或將應用程式移植到 .NET Core](./media/whats-new-dotnet-core/framework-vs-core.png)

## <a name="net-standard-vs-pcl"></a>.NET Standard 與 PCL 的比較

[.NET Standard](../../standard/net-standard.md) 是計劃在所有 .NET 實作提供的 .NET API 型式規格。 .NET Standard 背後的動機是在 .NET 生態系統中建立更高的一致性。 .NET Standard 是 .NET Api 的規格，可構成一組統一的合約，以編譯您的程式碼。 這些合約會在每個 .NET 類別中實作為，因此可跨不同的 .NET 部署提供可攜性。

.NET Standard 支援下列重要案例：

- 定義一組統一的基類程式庫 Api，以供所有要執行的 .NET 部署（與工作負載無關）。
- 可讓開發人員使用這組相同的 API，產生可跨 .NET 實作使用的可攜式程式庫。

.NET Standard 是 Pcl 的演進，下列清單顯示 .NET Standard 和 Pcl 之間的基本差異：

- .NET Standard 是由 Microsoft 挑選的一組策劃 Api。 Pcl 不是。
- PCL 所包含的 Api 取決於您在建立時選擇要設為目標的平臺。 這使得 PCL 只能針對您所選擇的特定目標進行共用。
- .NET Standard 與平臺無關，它可以在 Windows、macOS、Linux 等任何地方執行。
- Pcl 也可以跨平臺執行，但會有更多的範圍。 Pcl 只能以一組有限的平臺為目標。

## <a name="new-desktop-features-in-net-core"></a>.NET Core 中的新桌面功能

### <a name="support-for-windows-forms-and-wpf"></a>支援 Windows Forms 和 WPF

從3.0 版開始，Windows Forms 和 WPF 是 .NET Core 的一部分。 這兩種呈現架構僅適用于 Windows，因此不會跨平臺。 您可以將 WPF 視為透過 DirectX 和 Windows Forms 的豐富層級，做為透過 GDI + 的較精簡層。 WPF 和 Windows Forms 在 Windows 中，有很大的功能可以公開及運用大部分的桌面應用程式。 因此，Windows Forms 和 WPF 適用于 .NET Core 和 .NET Framework。 現在您可以開始以 .NET Core 為目標的新桌面應用程式，並將現有的應用程式從 .NET Framework 遷移至 .NET Core。

新版本的 .NET Standard （版本2.1）與 .NET Core 3.0 同時發行。 如預期，.NET Core 3.x 版本支援 .NET Standard 2.1 和更早版本。

此外，請務必注意，適用于 .NET Core 的 Windows Forms 和 WPF 都是開放原始碼。

### <a name="xaml-islands"></a>XAML Islands

[XAML Islands](/windows/apps/desktop/modernize/xaml-islands)是一組元件，可讓開發人員在其目前的 WPF、Windows Forms 和原生 Win32 應用程式（例如 MFC）中使用新的 Windows 10 控制項（UWP XAML 控制項）。 您可以在 Win32 應用程式中的任何位置，讓您的 UWP XAML 控制項有「群島」。

由於 Windows 10 版本1903引進了一組 Api，可讓您使用 windows 處理常式（Hwnd）在 Win32 視窗中裝載 UWP XAML 內容，因此可能會產生這些 XAML 孤島。 請注意，只有在 Windows 10 1903 和更新版本上執行的應用程式可以使用 XAML 島。

為了讓 Windows Forms 和 WPF 開發人員能夠更輕鬆地建立 XAML 島，Windows 社區工具組在數個 NuGet 套件中引進了一組 .NET 包裝函式。 這些包裝函式是包裝和裝載控制項：

- [ [Web](/windows/communitytoolkit/controls/wpf-winforms/webview)工作]、[ [WebViewCompatible](/windows/communitytoolkit/controls/wpf-winforms/webviewcompatible)]、[ [InkCanvas](/windows/communitytoolkit/controls/wpf-winforms/inkcanvas)]、[ [MediaPlayerElement](/windows/communitytoolkit/controls/wpf-winforms/mediaplayerelement)] 和 [ [MapControl](/windows/communitytoolkit/controls/wpf-winforms/mapcontrol) ] 包裝的控制項會將一些 UWP XAML 控制項包裝到 Windows Forms 或 WPF 控制項，以隱藏這些開發人員的 uwp 概念
- Windows Forms 和 WPF 的[WindowsXamlHost](/windows/communitytoolkit/controls/wpf-winforms/windowsxamlhost)控制項可讓其他未包裝的 UWP XAML 控制項和自訂控制項載入至 XAML 島。

### <a name="access-to-all-windows-10-apis"></a>存取所有 Windows 10 Api

Windows 10 有大量的 API 可供開發人員使用。 這些 Api 可讓您存取各種功能，例如驗證、藍牙、約會和連絡人。 這些 Api 現在透過 .NET Core 公開，讓 Windows 開發人員有機會利用 Windows 10 上的功能來建立強大的桌面應用程式。

### <a name="side-by-side-support-and-self-contained-exes"></a>並存支援和獨立 Exe

.NET Core 部署模型是 Windows 桌面開發人員在 .NET Core 中體驗的最大優點之一。 全域安裝 .NET Core 的功能可提供 .NET Framework 的許多相同中央安裝和服務優點，而不需要就地更新。

發行新的 .NET Core 版本時，您可以視需要更新電腦上的每個應用程式，而不會影響其他應用程式。 新的 .NET Core 版本會安裝在自己的目錄中，並彼此並存。

如果您需要以隔離方式部署，您可以使用應用程式來部署 .NET Core。 .NET Core 會將您的應用程式與 .NET Core 執行時間組合在同一個可執行檔中。

這些部署選項是由開發人員要求很長的時間，但使用 .NET Framework 並不容易達成。 .NET Core 所使用的模組化架構可讓這些彈性的部署選項可行。

### <a name="performance"></a>效能

從開始，以 web 和雲端工作負載為目標，.NET Core 已將效能插入其 DNA。 伺服器端程式碼的效能必須足以滿足高並行處理案例和 .NET Core 分數，做為市場上最佳的效能 web 平臺。

當您使用 .NET Core 來建立下一代的桌面應用程式時，您可以利用這些效能改進。

## <a name="benefits-of-open-source"></a>開放原始碼的優點

關於 .NET Core 的幾個單字是開放原始碼。 建立跨平臺堆疊是一項複雜的工作，需要在每個目標平臺上進行專門的小組互動。 這項作業需要在 Microsoft 內部和外部進行許多共同作業。 藉由開放原始碼並開放公開共同作業，您可以立即取得絕佳的 agile 開發風格，提高品質，因為問題是由一群龐大且活躍的開發人員所偵測到的。

這是 .NET Core 的重要成功因素，會繼續加速先前提到的藍圖：成為任何開發人員建立任何應用程式時所需的單一 .NET 平臺。

>[!div class="step-by-step"]
>[上一個](why-modern-applications.md) 
>[下一步](migrate-modern-applications.md)
