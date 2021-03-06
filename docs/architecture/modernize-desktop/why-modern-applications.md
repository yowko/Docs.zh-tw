---
title: 使用現代化傳統型應用程式的理由
description: 瞭解新式世界中的桌面技術，例如 Windows Forms、WPF 和 UWP。
ms.date: 12/29/2020
ms.openlocfilehash: 8489e41c973bb472a23bca38e9374c36e4cdd366
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615889"
---
# <a name="why-modern-desktop-applications"></a>使用現代化傳統型應用程式的理由

## <a name="introduction"></a>簡介

### <a name="a-story-of-one-company"></a>一家公司的故事

回到早期2000s，一家跨國公司開始開發分散式桌面解決方案，在公司不同分支之間交換資訊，並對集中式單位執行優化作業。 他們選擇了稱為 Windows Forms 的全新架構， (也稱為 WinForms) 來開發應用程式。 多年來，專案逐漸成為成熟、經過妥善測試且經過時間考驗的應用程式，並有數十萬行程式碼。 經過一段時間，.NET Framework 2.0 不再是最新的新技術。 正在處理此應用程式的開發人員面臨困境。 他們想要在開發過程中使用最新的技術堆疊，並讓應用程式的外觀和「感覺」現代化。 同時，他們不想要擲出超過15年的絕佳產品，並從頭重寫整個應用程式。

### <a name="your-story"></a>您的故事

您可能會在相同的船中找到自己的 Windows Forms 或 Windows Presentation Foundation (WPF) 應用程式，這些應用程式已證明其在多年的可靠性。 您可能想要繼續使用這些應用程式數年。 同時，因為這些應用程式是在不久之前撰寫的，所以它們可能遺失功能，例如新式外觀、效能、與新裝置和平臺功能的整合等等，讓他們覺得「舊科技」。 另外還有另一個問題，就是開發人員可能會擔心您的問題。 當您處理舊版的 .NET Framework，並維護一段時間所撰寫的應用程式時，您可能會覺得您不會學習新的技術，也不會因為建立新式技術技能而遺失。 如果這是您的故事，這本書適合您！

## <a name="desktop-applications-nowadays"></a>桌面應用程式現今

在網際網路引發之前，桌面應用程式是建立軟體系統的主要方法。 開發人員可以選擇任何程式設計語言，例如 COBOL、Fortran、VB6 或 c + +。 但是他們開發的是小型工具或複雜的分散式架構，全都是桌面應用程式。

然後，網際網路技術開始驚人開發環境，並透過更簡單的部署和簡化的散發流程等優點來贏得更多工程師。 一旦將 web 應用程式部署至生產環境，所有使用者都會收到自動更新，對軟體的靈活性有很大的影響。

不過，網際網路基礎結構、基礎通訊協定，以及 HTTP 和 HTML 等標準都不是設計來建立複雜的應用程式。 事實上，主要的開發工作只是要讓 web 應用程式具有桌面應用程式所擁有的相同功能，例如快速資料輸入和狀態管理。

即使 web 和行動應用程式以驚人的步調成長，但針對某些工作，桌面應用程式還是會在效率和效能方面保有一個位置的數位。 這解釋了為什麼有數百萬名開發人員使用 WPF 和 WinForms 建立專案，以及這些應用程式的數量不斷成長。

以下是在開發中選擇桌面應用程式的一些原因：

- 桌面應用程式與使用者的電腦有更好的互動。
- 桌面應用程式進行複雜計算的效能遠高於 web 應用程式的效能。
- 在用戶端上執行自訂邏輯是可行的，但對 web 應用程式而言很困難。
- 在桌面應用程式中使用多執行緒是更簡單且更有效率的。
- 設計使用者介面 (Ui) 的學習曲線不會有陡。 針對 WinForms，您可透過 Windows Forms 設計工具的拖放體驗來直覺化。
- 您可以輕鬆地開始編碼和測試您的演算法，而不需要設定伺服器基礎結構或在意連線問題、防火牆和瀏覽器相容性。
- 相較于 web 偵錯工具，偵錯工具的功能強大。
- 您可以輕鬆地存取硬體裝置，例如相機、藍牙或卡片讀卡機。
- 因為技術已經有一段時間，所以有許多專家和知識庫可用於開發桌面應用程式。

因此，如您所見，針對桌面進行開發的原因很高。 這項技術是成熟且經過時間測試的，開發週期很快，而偵錯工具的功能強大，而且可以更輕鬆地開始使用桌面應用程式。

在過去幾年來，Microsoft 提供許多 UI 桌面技術，從1995年引進的 Win32 到通用 Windows 平臺 (UWP) 在2016版中發行。

![Microsoft 桌面技術](./media/why-modern-applications/microsoft-desktop-technologies.png)

根據 Telerik 在2016年4月發佈的問卷，建立 Windows 桌面應用程式的最熱門技術是 Windows Forms、WPF 和 UWP。

![Telerik 問卷，以最受歡迎的桌面技術顯示 Windows Forms、WPF 和 UWP](./media/why-modern-applications/telerik-survey.png)

您可以使用 c # 和 Visual Basic 開發它們，但讓我們進一步瞭解。

### <a name="windows-forms"></a>Windows Forms

第一次發行于2002中，Windows Forms 是受控架構，而且是以 Windows 圖形裝置介面為基礎的最舊、最常使用的桌面技術 (GDI) 引擎。 它提供在 Visual Studio 中開發使用者介面的流暢拖放體驗。  同時，Windows Forms 依賴 Visual Studio 設計工具做為您開發 UI 的主要方式，因此從程式碼建立視覺效果元件並不重要。

下列清單摘要說明 Windows Forms 的主要特性：

- 有許多程式碼範例和檔的成熟技術。
- 功能強大且有效率的設計工具。 從程式碼設計 UI 並不方便。
- 很容易就能瞭解，因為設計工具的拖放體驗。
- 在任何 Windows 版本上都有支援。
- 在 .NET Core 3.0 和更新版本上支援。

### <a name="wpf"></a>WPF

WPF 會根據 XAML 語言規格來明確地分隔 UI 和程式碼。 XAML 提供了像是範本、樣式和系結等功能，適合用來建立大型應用程式。 就像 Windows Forms 一樣，它是一個受控架構，但設計是模組化且可重複使用。

以下是 WPF 的主要功能：

- 成熟的技術。
- 設計工具可供使用，但開發人員通常偏好使用宣告式 XAML 從程式碼建立設計。
- 學習曲線的較陡峭與 Windows Forms。
- 在任何 Windows 版本上都有支援。
- 在 .NET Core 3.0 和更新版本上支援。

### <a name="uwp"></a>UWP

UWP 不只是 WPF 和 Windows Forms 這類展示架構，也是平臺本身。 這個平臺有：

- 自己的 API 集 (Windows 執行階段 API) 。
- 新的部署系統 (MSIX) 
- 新式應用程式生命週期模型 () 電池耗用量不足。
- 新的資源管理系統 (以) 的 PRI 檔案為基礎。

平臺的建立是為了支援所有類型的輸入系統， (例如筆墨、觸控、遊戲台、滑鼠、鍵盤、注視等) 在所有外型規格中都是在考慮效能和低電池耗用量。 基於這些理由，Windows 10 OS 的 shell 會使用 UWP 平臺的元件。

![UWP 結構](./media/why-modern-applications/uwp-structure.png)

UWP 包含以 XAML 為基礎的展示架構（例如 WPF），但有一些重要的差異，例如：

- 應用程式會在應用程式容器中執行。 應用程式容器可控制 UWP 應用程式可以存取的資源。
- 僅 Windows 10 支援。
- 您可以透過 Microsoft Store 部署應用程式，以更輕鬆地進行部署。
- 設計為 Windows 執行階段 API 的一部分。
- 包含一組豐富的豐富內建控制項，以及透過 Microsoft UI 程式庫 NuGet 套件提供的額外控制項， (WinUI 程式庫) 每隔幾個月更新一次。

## <a name="a-tale-of-two-platforms"></a>兩個平臺的故事

過去20年來，雖然 UI 桌面技術的成長和遵循 Windows Forms 到 UWP 的路徑，但硬體也會從具有不同資料輸入技術（例如觸控和筆墨）的大量 CRT 監視器，一直演進到高 DPI 監視器和輕量平板電腦和手機。 這些變更產生了兩個不同的概念：桌面應用程式和新式應用程式。 新式應用程式是指將不同的裝置外型規格、各種輸入和輸出方法納入考慮，並在沙箱執行模型上執行時運用新式桌面功能的應用程式。 另一方面， (傳統) 傳統型應用程式的應用程式，需要具有高密度控制項且最適合使用滑鼠和鍵盤操作的穩固 UI。

下表說明這兩個概念之間的差異：

|   | 新式應用程式 | 桌面應用程式 |
| --- | --- | --- |
| 安全性 | 包含 &amp; 的執行絕佳基礎。 從頭開始設計，以尊重使用者的隱私權、管理電池壽命，以及專注于確保裝置安全。  | 使用者系統 &amp; 管理員的安全性層級。 您可以原生存取登錄和硬碟資料夾。 |
| 部署 | 安裝和更新是由平臺所管理。   | MSI，自訂安裝 &amp; 程式會更新。 傳統上，開發人員和 IT 管理員的問題來源。  |
| 散發 | 受信任 &amp; 的散發簽署套件。 散發是從信任的來源執行，而且永遠不會從網站執行。  | Web、SCCM &amp; 自訂散發。 無法控制已安裝的內容，會影響整台電腦。   |
| UI | 新式的 UI。 不同的輸入機制、筆墨、觸控、遊戲台、鍵盤、滑鼠等等。  | Windows Forms、WPF、MFC。 專為密集 UI 的滑鼠和鍵盤而設計，可從桌面取得最高的生產力。  |
| 資料 | 具有見解的雲端優先資料。 雲端中的真實來源。 深入瞭解您的應用程式會發生什麼情況，以及其執行方式。  | 本機資料。 傳統的桌面應用程式通常需要一些本機資料。  |
| 設計 | 專為重複使用而設計。 在不同的平臺、前端和後端之間重複使用，盡可能在許多地方執行資產。  | 僅適用于 Windows Desktop  |

為了為開發人員提供最佳工具來建立應用程式，Microsoft 致力於提供這些概念，或甚至是更接近的平臺，讓開發人員能以這兩種方式發揮最大優勢。 為了達成此目的，Microsoft 已在兩個平臺之間執行雙向工作。

![新式應用程式與桌面應用程式之間的雙向工作](./media/why-modern-applications/bidirectional-effort.png)

1. 將桌面應用程式案例移至新式應用程式平臺。 傳統的桌面開發仍很受歡迎，因為它能解決某些案例的狀況。 採用這些常見的桌上型電腦案例，並將它們帶入新式桌面平臺，讓平臺具備完整的能力，是合理的。

    ![將桌面應用程式案例移至新式應用程式平臺](./media/why-modern-applications/desktop-to-modern.png)

1. 將新式應用程式功能移至桌面應用程式。 如果現有的傳統型應用程式需要一種方式來利用新式功能，而不需要從頭重寫，則新式應用程式平臺的功能會被推送至桌面應用程式。

    ![將新式應用程式功能移至桌面應用程式](./media/why-modern-applications/modern-to-desktop.png)

在本書中，我們將著重于第二個部分，並示範如何將現有的桌面應用程式現代化。

## <a name="paths-to-modernization"></a>現代化的途徑

本指南的結構反映了三個不同的座標軸，以達成現代化：新式功能、部署和安裝。

### <a name="modern-features"></a>新式功能

假設您有一個可運作的 Windows Forms 應用程式，公司的銷售代表會使用此應用程式來填寫客戶訂單。 有一項新的需求可讓客戶使用 tablet 畫筆來簽署訂單。 筆跡在現今的作業系統和技術中是原生的，但在開發應用程式時無法使用。

此路徑將為您示範如何運用新式桌面功能來進行現有的桌面開發。

### <a name="deployment"></a>部署

新式開發週期有很大的彈性，讓您能夠靈活地將新版本的應用程式部署到每一位使用者。 由於 Windows Forms 和 WPF 應用程式是以必須存在於電腦上的特定 .NET Framework 版本為基礎，因此他們無法利用新的 .NET Framework 版本功能，而不需要對相同電腦上執行的其他應用程式造成副作用的風險。 它對開發人員來說，會因為強制它們維持 .NET Framework 的過時版本而有所限制。

自 .NET Core 3.0 推出之後，您可以利用新的方法來並行部署多個版本的 .NET，並指定每個應用程式應該設為目標的 .NET 版本。 如此一來，您就可以使用一個應用程式中的最新功能，同時確信不會中斷任何其他應用程式。

### <a name="installation"></a>安裝

桌面應用程式一律依賴某種安裝程式，使用者才能開始使用。 這項事實讓遊戲成為遊戲的一組技術，從 MSI 和 ClickOnce 到自訂安裝程式，甚至是 XCOPY 部署。 這些方法中的任何一種都有精密的問題，因為應用程式需要一種方式來存取電腦上的共用資源。 有時安裝需要存取登錄來插入或更新新的金鑰值，有時會更新主要應用程式所參考的共用 Dll。 這種行為會對使用者造成相當麻煩的情況，因此在您安裝某些應用程式之後，您的電腦將永遠不會相同，即使您之後再卸載。

在本書中，我們將介紹使用 MSIX 來安裝應用程式的新方式，以解決稍早所述的問題。 您將瞭解如何輕鬆地設定應用程式的封裝、安裝和更新。

>[!div class="step-by-step"]
>[上一個](index.md) 
>[下一步](whats-new-dotnet.md)
