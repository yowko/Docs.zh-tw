---
title: BlazorASP.NET Web Forms 開發人員的簡介
description: Blazor使用 .net 撰寫完整堆疊 web 應用程式的簡介
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 09/11/2019
ms.openlocfilehash: a5aae6cf02ccec84ac8642b6ce8d9c919755e868
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267564"
---
# <a name="an-introduction-to-no-locblazor-for-aspnet-web-forms-developers"></a>BlazorASP.NET Web Forms 開發人員的簡介

由於 .NET Framework 第一次隨附于2002，因此 ASP.NET Web Forms framework 是 .NET Web 開發的一種裝訂。 回到網路的成形，ASP.NET Web Forms 藉由採用用於桌面開發的許多模式，讓建立 web 應用程式變得簡單又有效率。 在 ASP.NET Web Forms 中，可以從可重複使用的 UI 控制項快速撰寫網頁。 使用者互動是以事件的方式自然處理。 有豐富的 Web Form UI 控制項生態系統，由 Microsoft 和控制廠商提供。 這些控制項可讓您輕鬆地連接到資料來源，並顯示豐富的資料視覺效果。 針對視覺效果，Web Form 設計工具提供簡單的拖放介面來管理控制項。

多年來，Microsoft 引進了以 ASP.NET 為基礎的新 web 架構，以解決 網頁程式開發趨勢。 某些這類 web 架構包括 ASP.NET MVC、ASP.NET Web Pages，以及最近的 ASP.NET Core。 在每個新的架構中，有些已預測出 ASP.NET Web Forms 的即將拒絕，並將其 criticized 為過時、過時的 Web 架構。 儘管有這些預測，許多 .NET 網頁程式開發人員仍可繼續找到 ASP.NET Web Forms 簡單、穩定且有效率的方式來完成工作。

在撰寫本文時，將近一百萬名 網頁程式開發人員每個月會使用 ASP.NET Web Forms。 ASP.NET Web Forms framework 在一年前的檔、範例、書籍和 blog 文章之間保持不變，而且也很有説明。 對於許多 .NET 網頁程式開發人員來說，「ASP.NET」仍會與「ASP.NET Web Forms」同義，就像是在第一次構想 .NET 時一樣。 相較于其他新的 .NET Web 架構，ASP.NET Web Forms 的優缺點的引數可能會開始風行。 ASP.NET Web Forms 仍是用來建立 Web 應用程式的熱門架構。

即便如此，軟體發展的創新也不會變慢。 所有軟體發展人員都需要掌握新技術與趨勢。 有兩個特定的趨勢值得考慮：

1. 移至開放原始碼和跨平臺
2. 將應用程式邏輯轉移至用戶端

## <a name="an-open-source-and-cross-platform-net"></a>開放原始碼和跨平臺的 .NET

當 .NET 和 ASP.NET Web Forms 首次發行時，平臺生態系統看起來與現今的差異很大。 桌上型電腦和伺服器市場都是由 Windows 所主導。 替代平臺（例如 macOS 和 Linux）仍在努力吸引您的吸引力。 ASP.NET Web Forms 隨附 .NET Framework 作為僅限 Windows 的元件，這表示 ASP.NET Web Forms 應用程式只能在 Windows Server 電腦上執行。 許多新式環境現在對伺服器和開發電腦使用不同類型的平臺，因此許多使用者的跨平臺支援是絕對需求。

現今大部分的 web 架構也都是開放原始碼，有許多好處。 使用者不會 beheld 至單一專案擁有者來修正 bug 和新增功能。 開放原始碼專案可針對開發進度和即將進行的變更，提供更好的透明度。 開放原始碼專案可享受整個團體的貢獻，並促進可提供的開放原始碼生態系統。 儘管有開放原始碼的風險，許多取用者和參與者都找到適當的緩和措施，讓他們能夠以安全且合理的方式享受開放原始碼生態系統的優點。 這類緩和措施的範例包括參與者授權合約、易記的授權、歷史掃描，以及支援的基礎。

.NET 社區同時採用跨平臺支援和開放原始碼。 .NET Core 是 .NET 的開放原始碼和跨平臺執行，可在眾多的平臺上執行，包括 Windows、macOS 和各種 Linux 發行版本。 Xamarin 提供 Mono，也就是 .NET 的開放原始碼版本。 Mono 可在 Android、iOS 和各種其他外型規格上執行，包括監看式和智慧型電視。 Microsoft 宣佈 [.net 5](https://devblogs.microsoft.com/dotnet/introducing-net-5/) 將會將 .net Core 和 Mono 協調為「單一 .net 執行時間和架構，可在任何地方使用，並具備一致的執行時間行為和開發人員體驗。」

從移至開放原始碼和跨平臺支援，ASP.NET Web Forms 是否受益？ 抱歉，答案是否，或至少與其他平臺的範圍不同。 .NET 小組 [最近已清楚](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/) 指出 ASP.NET Web Forms 不會移植到 .net Core 或 .net 5。 這是為什麼？

在舊版的 .NET Core 中，有了 ASP.NET Web Forms 的通訊埠。 發現需要的中斷性變更數量太過多。 在這裡也有一個可供 Microsoft 使用的許可，也就是可同時支援的 web 架構數目限制。 也許是因為社區中有人會造成建立開放原始碼和跨平臺版本的 ASP.NET Web Forms 的原因。 [ASP.NET Web Forms 的原始程式碼](https://github.com/microsoft/referencesource)已公開提供給參考表單。 但在這段時間內，似乎 ASP.NET Web Forms 只會保留 Windows，且不會有開放原始碼的投稿模型。 如果跨平臺支援或開放原始碼對您的案例而言很重要，則您必須尋找新的內容。

這是否表示 *ASP.NET Web Forms 沒有作用，因此* 不應再使用？ 當然不是！ 只要 .NET Framework 隨附于 Windows 的一部分，ASP.NET Web Forms 就會是支援的架構。 對於許多 Web Form 開發人員來說，缺乏跨平臺和開放原始碼支援並不成問題。 如果您不需要跨平臺支援、開放原始碼或 .NET Core 或 .NET 5 中的任何其他新功能，則在 Windows 上 ASP.NET Web Forms 不會有問題。 ASP.NET Web Forms 將持續成為撰寫 Web apps 多年的生產力。

但還有另一個值得考慮的趨勢，而這就是用戶端的轉移。

## <a name="client-side-web-development"></a>用戶端 網頁程式開發

所有。以網路為基礎的 web 架構（包括 ASP.NET Web Forms）在過去有一個共通的內容：它們是 *伺服器呈現*的。 在伺服器呈現的 web 應用程式中，瀏覽器會向伺服器提出要求，這會在 ASP.NET apps) 中執行一些程式碼 ( .NET 程式碼，以產生回應。 該回應會傳送回瀏覽器以進行處理。 在此模型中，會使用瀏覽器作為精簡轉譯引擎。 在伺服器上產生 UI、執行商務邏輯和管理狀態的困難工作。

不過，瀏覽器已成為多功能平臺。 他們會採用不斷增加的開放式 web 標準，將存取權授與使用者電腦的功能。 為什麼無法利用用戶端裝置的計算能力、儲存體、記憶體和其他資源？ 尤其是在處理至少部分或完全用戶端時，UI 互動的優點是更豐富且更有互動的感覺。 應該在伺服器上處理的邏輯和資料仍可在伺服器端處理。 您可以使用 Web API 呼叫或甚至是即時的通訊協定，例如 Websocket。 如果 網頁程式開發人員願意撰寫 JavaScript，可免費使用這些權益。 用戶端 UI 架構（例如，角度、反應和 Vue）可簡化用戶端 網頁程式開發並提高普及度。 ASP.NET Web Forms 開發人員也可以利用用戶端獲益，甚至還能以整合式 JavaScript 架構（例如 ASP.NET AJAX）提供一些現成的支援。

但橋接兩個不同的平臺和生態系統 ( .NET 和 JavaScript) 會產生費用。 使用不同的語言、架構和工具，在兩個平行世界中需要專業知識。 在用戶端與伺服器之間無法輕鬆共用程式碼和邏輯，導致重複和工程額外負荷。 您也很難跟上 JavaScript 生態系統，它的歷程記錄會以 breakneck 速度演進。 前端架構和組建工具喜好設定會快速變更。 業界觀察到從 Grunt 到 Gulp 到 Webpack 等等的進展。 前端架構（例如 jQuery、挖對、角度、反應和 Vue）發生相同的 restless 變換。 但有了 JavaScript 的瀏覽器 monopoly，也有很多選擇。 也就是說，在 web 社區彼此聯繫並造成 *miracle* 發生之前，

## <a name="no-locwebassembly-fulfills-a-need"></a>WebAssembly 滿足需求

在2015中，主要的瀏覽器廠商已加入 W3C 社區群組中的強制，以建立名為的新開放式 web 標準 WebAssembly 。 WebAssembly 是 Web 的位元組碼。 如果您可以將程式碼編譯為 WebAssembly ，則可以在任何平臺上的任何瀏覽器上以近乎原生速度執行。 著重于 C/c + + 的初始工作。 結果是在沒有外掛程式的情況下，直接在瀏覽器中執行原生3D 圖形引擎的明顯示範。 WebAssembly 已經過了所有主要瀏覽器的標準化和實行。

在上執行 .NET 的工作 WebAssembly 已于2017年後期宣佈，並預期會在2020中寄出，包括 .net 5 的支援。 直接在瀏覽器中執行 .NET 程式碼的功能，可讓您使用 .NET 進行完整堆疊的 網頁程式開發。

## <a name="no-locblazor-full-stack-web-development-with-net"></a>Blazor：使用 .NET 進行完整堆疊 網頁程式開發

在瀏覽器中執行 .NET 程式碼的能力並不提供建立用戶端 web 應用程式的端對端體驗。 這就是您所 Blazor 遇到的。 Blazor 是以 c # 為基礎的用戶端 web UI 架構，而不是 JavaScript。 Blazor 可以直接在瀏覽器中執行 WebAssembly 。 不需要瀏覽器外掛程式。 或者， Blazor 應用程式可以在 .Net Core 上執行伺服器端，以及透過瀏覽器的即時連線來處理所有使用者互動。

Blazor 在 Visual Studio 和 Visual Studio Code 中有絕佳的工具支援。 此架構也包含完整的 UI 元件模型，而且具有適用于的內建功能：

- 表單和驗證
- 相依性插入
- 用戶端路由
- 版面配置
- 瀏覽器內調試
- JavaScript Interop

Blazor 有許多 ASP.NET Web Forms 的常見功能。 這兩種架構都提供以元件為基礎、事件驅動、具狀態的 UI 程式設計模型。 主要的架構差異在於 ASP.NET Web Forms 只會在伺服器上執行。 Blazor 可以在瀏覽器中的用戶端上執行。 但是，如果您是 ASP.NET Web Forms 背景，則有很多人 Blazor 都覺得很熟悉。 Blazor 是一種自然的解決方案，可讓 ASP.NET Web Forms 開發人員尋找一種方法來利用用戶端開發，以及 .NET 的開放原始碼、跨平臺的未來。

這本書提供了 Blazor 建立，專門提供給 ASP.NET Web Forms 開發人員的簡介。 每個 Blazor 概念都會顯示在類似的 ASP.NET Web Forms 功能和實務的內容中。 本書結束時，您將瞭解：

- 如何建立 Blazor 應用程式。
- 如何 Blazor 運作。
- 如何 Blazor 與 .Net Core 相關。
- 將現有 ASP.NET Web Forms 應用程式遷移到適當位置的合理策略 Blazor 。

## <a name="get-started-with-no-locblazor"></a>開始使用 Blazor

開始使用 Blazor 很簡單。 移至 <https://blazor.net> 並遵循連結，安裝適當的 .NET Core SDK 和 Blazor 專案範本。 您也可以找到 Blazor 在 Visual Studio 或 Visual Studio Code 中設定工具的指示。

>[!div class="step-by-step"]
>[上一個](index.md) 
>[下一步](architecture-comparison.md)
