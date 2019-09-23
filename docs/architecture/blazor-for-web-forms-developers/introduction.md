---
title: Blazor for ASP.NET Web Forms 開發人員簡介
description: 使用 .NET Blazor 和撰寫完整堆疊 web 應用程式的簡介
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 922e72514f0283b66de971d679fab0af436f1c75
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183844"
---
# <a name="an-introduction-to-blazor-for-aspnet-web-forms-developers"></a>Blazor for ASP.NET Web Forms 開發人員簡介

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

ASP.NET Web form 架構已經是 .NET Web 程式開發的裝訂，因為 .NET Framework 第一次在2002中出貨。 回到過去，當 Web 仍在成形中時，ASP.NET Web Forms 藉由採用許多用於桌面開發的模式，讓 web 應用程式的建立變得簡單又有效率。 在 ASP.NET Web Forms 中，可以從可重複使用的 UI 控制項快速地撰寫網頁。 使用者互動會自然地當做事件來處理。 Microsoft 和控制廠商提供了豐富的 Web Forms UI 控制項生態系統。 這些控制項會讓您輕鬆地連接到資料來源，並顯示豐富的資料視覺效果。 針對視覺上的傾向，Web Forms 設計工具提供簡單的拖放介面來管理控制項。

多年來，Microsoft 引進了以 ASP.NET 為基礎的新 web 架構，以解決 網頁程式開發趨勢。 某些這類 web 架構包括 ASP.NET MVC、ASP.NET Web Pages 和最近 ASP.NET Core。 有了每個新的架構，部分預測 ASP.NET Web form 即將下降，並將其 criticized 為過時的過時 web 架構。 儘管有這些預測，許多 .NET 網頁程式開發人員仍可繼續尋找 ASP.NET Web form，這是一種簡單、穩定又有效率的方式來完成工作。

在撰寫本文時，將近一百萬個 網頁程式開發人員每個月會使用 ASP.NET Web Forms。 ASP.NET Web form 架構的重點是，十年前的檔、範例、書籍和 blog 文章仍然有用且相關。 對於許多 .NET 網頁程式開發人員而言，"ASP.NET" 仍與 .NET 初次構想時的「ASP.NET Web form」同義。 相較于其他新 .NET Web 架構，ASP.NET Web form 優缺點的引數可能會開始風行在上。 ASP.NET Web Forms 仍然是建立 web 應用程式的熱門架構。

就算如此，軟體發展的創新也不會變慢。 所有軟體發展人員都必須掌握新技術和趨勢的步伐。 特別值得考慮的兩個趨勢： 

1. 轉移到開放原始碼和跨平臺
2. 應用程式邏輯對用戶端的轉換

## <a name="an-open-source-and-cross-platform-net"></a>開放原始碼和跨平臺的 .NET

當 .NET 和 ASP.NET Web form 第一次出貨時，平臺生態系統看起來會與今天的內容不同。 桌上型電腦和伺服器市場已由 Windows 主導。 其他平臺（例如 macOS 和 Linux）仍在努力，以獲得吸引力。 ASP.NET Web Forms 隨附 .NET Framework 做為僅限 Windows 的元件，這表示 ASP.NET Web Forms 應用程式只能在 Windows Server 電腦上執行。 許多現代化環境現在都會針對伺服器和開發電腦使用不同類型的平臺，讓許多使用者的跨平臺支援是絕對需求。

大部分的新式 web 架構現在也都是開放原始碼，有許多優點。 使用者不會 beheld 為單一專案擁有者，以修正 bug 並新增功能。 開放原始碼專案提供更佳的開發進度和近期變更的透明度。 開放原始碼專案可享受整個社區的貢獻，並促進開放原始碼生態系統。 儘管開放原始碼的風險，許多消費者和參與者都發現適當的緩和措施，讓他們能夠以安全且合理的方式享受開放原始碼生態系統的優勢。 這類緩和措施的範例包括參與者授權合約、易記授權、歷史掃描和支援的基礎。

.NET 的社區同時採用跨平臺支援和開放原始碼。 .NET Core 是 .NET 的開放原始碼和跨平臺執行，可在眾多的平臺上執行，包括 Windows、macOS 和各種 Linux 發行版本。 Xamarin 提供 Mono，這是一種開放原始碼的 .NET 版本。 Mono 會在 Android、iOS 和各種不同的外型規格上執行，包括監看式和智慧型電視。 Microsoft 已宣佈[.net 5](https://devblogs.microsoft.com/dotnet/introducing-net-5/)將 .net Core 和 Mono 協調成「單一 .net 執行時間和架構」，可以在任何地方使用，而且具有一致的執行時間行為和開發人員體驗。」

ASP.NET Web form 是否受益于移至開放原始碼和跨平臺支援？ 但不幸的是，答案是「否」，或至少與其他平臺的範圍相同。 .NET 團隊[最近使](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/)ASP.NET Web form 不會移植到 .net Core 或 .net 5。 為什麼？

在早期的 .NET Core 中，會投入 ASP.NET Web form 的埠。 發現所需的重大變更數目太過嚴重。 此外，在這裡也有一項可供 Microsoft 使用的許可，同時也會限制可以同時支援的 web 架構數目。 可能是因為社區中的某個人會造成建立 ASP.NET Web form 的開放原始碼和跨平臺版本的原因。 [ASP.NET Web](https://github.com/microsoft/referencesource) form 的原始程式碼已公開提供參考格式。 但在這種情況下，ASP.NET 的 Web 表單會保持僅限 Windows，而不會有開放原始碼的貢獻模型。 如果跨平臺支援或開放原始碼在您的案例中變得很重要，則您需要尋找新的專案。

這是否表示 ASP.NET Web form 已*失效*，不應再使用？ 當然不是！ 只要 .NET Framework 隨附于 Windows，ASP.NET Web Forms 就會是支援的架構。 對於許多 Web form 開發人員而言，缺乏跨平臺和開放原始碼支援並不是問題。 如果您不需要跨平臺支援、開放原始碼或 .NET Core 或 .NET 5 中的任何其他新功能，則在 Windows 上使用 ASP.NET Web form 並不會有問題。 ASP.NET Web Forms 會繼續以有效率的方式撰寫 web 應用程式多年來。

但是還有另一個值得考慮的趨勢，這就是用戶端的轉移。

## <a name="client-side-web-development"></a>用戶端 網頁程式開發

的所有。以網路為基礎的 web 架構（包括 ASP.NET Web form）在過去有一個共通的東西：它們是*伺服器*轉譯的。 在伺服器轉譯的 web 應用程式中，瀏覽器會對伺服器提出要求，這會執行一些程式碼（在 ASP.NET apps 中的 .NET 程式碼）來產生回應。 該回應會傳送回瀏覽器以處理。 在此模型中，瀏覽器會用來做為精簡轉譯引擎。 產生 UI、執行商務邏輯和管理狀態的困難工作會在伺服器上發生。

不過，瀏覽器已成為多樣化的平臺。 它們會採用不斷增加的開放式 web 標準數目，以授與使用者電腦功能的存取權。 為什麼無法利用用戶端裝置的計算能力、儲存體、記憶體和其他資源？ 特別是當至少部分或完全在用戶端上處理時，UI 互動可能會受益于更豐富且更具互動的風格。 應該在伺服器上處理的邏輯和資料仍然可以在伺服器端處理。 您可以使用 Web API 呼叫或甚至是即時通訊協定，例如 Websocket。 如果 網頁程式開發人員願意撰寫 JavaScript，就可以免費使用這些權益。 用戶端 UI 架構（例如，角度、反應和 Vue）可以簡化用戶端 網頁程式開發並增加熱門程度。 ASP.NET Web form 開發人員也可以受益于利用用戶端，甚至在整合式 JavaScript 架構（例如 ASP.NET AJAX）方面提供一些現成的支援。

但橋接兩個不同的平臺和生態系統（.NET 和 JavaScript）會產生成本。 在兩個具有不同語言、架構和工具的平行世界中，需要專長。 程式碼和邏輯無法輕鬆地在用戶端和伺服器之間共用，因而導致重複和工程額外負荷。 也很容易跟上 JavaScript 生態系統，其歷程記錄是以 breakneck 速度進化。 前端架構和組建工具喜好設定很快就會變更。 產業觀察到從 Grunt 到 Gulp 到 Webpack 的進展，依此類推。 前端架構（例如 jQuery、挖式、角度、反應和 Vue）發生相同的 restless 變換。 但是，在 JavaScript 的瀏覽器 monopoly 中，這沒什麼選擇。 也就是，在 web 社區整合並造成*製品*的情況下！

## <a name="webassembly-fulfills-a-need"></a>WebAssembly 滿足需求

在2015中，主要的瀏覽器廠商聯結會強制在 W3C 社區群組中建立稱為 WebAssembly 的新 open web standard。 WebAssembly 是 Web 的位元組代碼。 如果您可以將程式碼編譯為 WebAssembly，就可以在任何平臺上以近乎原生的速度在任何瀏覽器上執行。 首次致力於 C/C++。 結果是直接在瀏覽器中執行原生3D 圖形引擎（不含外掛程式）的大幅示範。 WebAssembly 已由所有主要瀏覽器標準化並實行。

在 WebAssembly 上執行 .NET 的工作已于2017年底發行，預計會在2020推出，包括 .NET 5 的支援。 直接在瀏覽器中執行 .NET 程式碼的功能，可以使用 .NET 進行完整堆疊的 網頁程式開發。

## <a name="blazor-full-stack-web-development-with-net"></a>Blazor：使用 .NET 進行完整堆疊 網頁程式開發

在瀏覽器中執行 .NET 程式碼的功能，並不提供建立用戶端 web 應用程式的端對端體驗。 這就是 Blazor 的來源。 Blazor 是以為基礎的用戶端 web UI 架構C# ，而不是 JavaScript。 Blazor 可以透過 WebAssembly 直接在瀏覽器中執行。 不需要瀏覽器外掛程式。 或者，Blazor apps 可以在 .NET Core 上執行伺服器端，並透過與瀏覽器的即時連線來處理所有使用者互動。

Blazor 在 Visual Studio 和 Visual Studio Code 中具有絕佳的工具支援。 此架構也包含完整的 UI 元件模型，並具有下列各項的內建功能：

* 表單和驗證
* 相依性插入
* 用戶端路由
* 版面配置
* 瀏覽器內的調試
* JavaScript Interop

Blazor 在 ASP.NET Web Forms 中有很多共同的功能。 這兩種架構都提供以元件為基礎、事件驅動、具狀態的 UI 程式設計模型。 主要的架構差異在於，ASP.NET Web Forms 只會在伺服器上執行。 Blazor 可以在瀏覽器中的用戶端上執行。 但是，如果您是從 ASP.NET Web form 背景，那麼很容易就會覺得 Blazor。 Blazor 是一種自然的解決方案，可讓您 ASP.NET Web form 開發人員，尋找如何利用用戶端開發以及 .NET 的開放原始碼、跨平臺的未來。

本書提供 Blazor 的簡介，建立專門用來 ASP.NET Web form 開發人員。 每個 Blazor 概念都會出現在類似的 ASP.NET Web form 功能和實務的內容中。 本書結束之後，您將瞭解：

* 如何建立 Blazor 應用程式。
* Blazor 的運作方式。
* Blazor 與 .NET Core 的關聯。
* 在適當的情況下，將現有的 ASP.NET Web Forms 應用程式遷移至 Blazor 的合理策略。

## <a name="get-started-with-blazor"></a>開始使用 Blazor

開始使用 Blazor 很容易。 移至<https://blazor.net>並遵循連結，以安裝適當的 .NET Core SDK 和 Blazor 專案範本。 您也可以在 Visual Studio 或 Visual Studio Code 中找到設定 Blazor 工具的指示。

>[!div class="step-by-step"]
>[上一頁](index.md)
>[下一頁](architecture-comparison.md)
