---
title: Blazor 適用于 ASP.NET Web Forms 開發人員
description: 瞭解如何以簡單且熟悉的方式，使用 .NET Core 以 .NET 建立完整堆疊的 web 應用程式 Blazor 。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 09/11/2019
ms.openlocfilehash: 3ac9a02a2f5c93cbfd9377a9f6fff4b6c5f45e93
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158171"
---
# <a name="no-locblazor-for-aspnet-web-forms-developers"></a>Blazor 適用于 ASP.NET Web Forms 開發人員

![顯示「無伺服器應用程式」電子書封面的螢幕擷取畫面。](./media/index/blazor-for-aspnet-web-forms-developers.png)

> 下載：<https://aka.ms/blazor-ebook>

發行者

Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組

Microsoft Corporation 部門

One Microsoft Way

Redmond, Washington 98052-6399

Microsoft Corporation 的著作權©2020

著作權所有，並保留一切權利。 本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。

本書依照「現況」提供，代表作者的觀點和意見。 本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。

此處描述的一些範例僅供說明之用，純屬虛構。 並未影射或關聯任何真實的人、事、物。

Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。

Mac 與 macOS 是 Apple Inc. 的商標。

所有其他商標和標誌屬於其各自擁有者的財產。

作者：

> Microsoft Corp 的首席專案經理**[Daniel Roth](https://github.com/danroth27)**。

> Microsoft Corp 資深專案經理**[Jeff Fritz](https://github.com/csharpfritz)**。

> Microsoft Corp 資深軟體工程師**[Taylor Southwick](https://github.com/twsouthwick)**。

> **[Scott Addie](https://github.com/scottaddie)**，資深內容開發人員，Microsoft Corp。

> **[Steve "ardalis" Smith](https://ardalis.com)**，軟體架構設計人員和訓練員，ARDALIS Services LLC

## <a name="introduction"></a>簡介

.NET 透過 ASP.NET 提供長時間支援的 web 應用程式開發，這是一組完整的架構和工具，可用來建立任何類型的 web 應用程式。 ASP.NET 有自己的 web 架構和技術歷程，從傳統的 Active Server Pages (ASP) 開始。 ASP.NET Web Forms、ASP.NET MVC、ASP.NET Web Pages 等架構，以及最新 ASP.NET Core 的架構，可提供具生產力且功能強大的方式來建立 *伺服器呈現* 的 Web 應用程式，以在伺服器上動態產生 UI 內容以回應 HTTP 要求。 每個 ASP.NET 架構都已經考慮至不同的物件和應用程式建立原理。 ASP.NET Web Forms 隨附于原始版本的 .NET Framework，並使用許多桌面開發人員熟悉的模式來啟用 Web 開發，例如可重複使用的 UI 控制項，以及簡單的事件處理。 不過，沒有任何 ASP.NET 供應專案會提供方法來執行在使用者的瀏覽器中執行的程式碼。 若要這麼做，需要撰寫 JavaScript，並使用許多 JavaScript 架構和工具，這些架構和工具在過去幾年內都有可能出現和不受歡迎： jQuery、挖起、角度、反應等。

[Blazor](https://blazor.net) 是新的 web 架構，可變更使用 .NET 建立 web 應用程式時可能發生的情況。 Blazor 是以 c # 為基礎的用戶端 web UI 架構，而不是 JavaScript。 Blazor您可以使用以 c # 撰寫用戶端邏輯和 UI 元件、將它們編譯成一般的 .net 元件，然後使用名為的新開放式 web 標準，直接在瀏覽器中執行它們 WebAssembly 。 或者，也 Blazor 可以在伺服器上執行 .NET UI 元件，並透過瀏覽器的即時連線來處理所有 UI 互動流暢地。 當與在伺服器上執行的 .NET 搭配使用時， Blazor 可使用 .net 進行完整堆疊的 網頁程式開發。 雖然 Blazor 與 ASP.NET Web Forms 共用許多共通性，例如擁有可重複使用的元件模型，以及處理使用者事件的簡單方法，但它也是以 .Net Core 的基礎為基礎，以提供現代化且高效能的 Web 開發體驗。

本書以熟悉且方便的方式，介紹 ASP.NET Web Forms 開發人員 Blazor 。 它會以 Blazor ASP.NET Web Forms 中的類似概念來平行引進概念，同時也會說明可能較不熟悉的新概念。 其中涵蓋各種主題和問題，包括元件撰寫、路由、配置、設定和安全性。 雖然本書的內容主要是用來啟用新的開發，但它也涵蓋了將現有的 ASP.NET Web Forms 遷移至的指導方針和策略，以便將現有 Blazor 的應用程式現代化。

## <a name="who-should-use-the-book"></a>誰應該使用書

這本書適用于 ASP.NET Web Forms 開發人員尋找與 Blazor 現有知識和技能相關的簡介。 本書可協助您快速開始使用新 Blazor 的專案，或協助圖表現代化現有 ASP.NET Web Forms 應用程式的藍圖。

## <a name="how-to-use-the-book"></a>如何使用書

本書的第一個部分涵蓋了什麼， Blazor 並將其與 ASP.NET Web Forms 的 web 應用程式開發做比較。 本書接著涵蓋各種 Blazor 主題（依章節），並將每個概念與 Blazor ASP.NET Web Forms 中的對應概念建立關聯，或徹底說明所有全新的概念。 本書也會定期參考在 ASP.NET Web Forms 中執行的完整範例應用程式，並 Blazor 示範 Blazor 功能以及提供從 ASP.NET Web Forms 遷移至的案例研究 Blazor 。 您可以在 GitHub 上找到範例應用程式的兩個 (ASP.NET Web Forms 和 Blazor 版本) 。 [GitHub](https://github.com/dotnet-architecture/eshoponblazor)

## <a name="what-this-book-doesnt-cover"></a>本書未涵蓋的內容

這本書是的簡介 Blazor ，而不是完整的遷移指南。 雖然它包含有關如何將專案從 ASP.NET Web Forms 遷移至的指引 Blazor ，但並不會嘗試涵蓋每個微妙和詳細資料。 如需從 ASP.NET 遷移至 ASP.NET Core 的一般指引，請參閱 ASP.NET Core 檔中的 [遷移指導](/aspnet/core/migration/proper-to-2x/) 方針。

### <a name="additional-resources"></a>其他資源

您可以在中找到官方首頁 Blazor 和檔 <https://blazor.net> 。

## <a name="send-your-feedback"></a>傳送您的意見反應

本書和相關的範例不斷演進，所以您的意見反應歡迎！ 如果您有關于如何改進本書的意見，請使用內建于 [GitHub 問題](https://github.com/dotnet/docs/issues)之任何頁面底部的意見反應區段。

>[!div class="step-by-step"]
>[下一個](introduction.md)
