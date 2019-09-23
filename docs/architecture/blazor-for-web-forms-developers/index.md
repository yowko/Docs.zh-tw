---
title: 適用于 ASP.NET Web Forms 開發人員的 Blazor
description: 瞭解如何以簡單且熟悉的方式，使用 Blazor 和 .NET Core 以 .NET 建立完整堆疊的 web 應用程式。
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: a80483f6a1f1cb9e5a3e2ffff18cbd59c5b67af3
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183795"
---
# <a name="blazor-for-aspnet-web-forms-developers"></a>適用于 ASP.NET Web Forms 開發人員的 Blazor

![顯示無伺服器應用程式電子書封面的螢幕擷取畫面。](./media/index/blazor-for-web-forms-developers-cover.png)

> 下載：<https://aka.ms/blazor-ebook>

發行者

Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組

Microsoft Corporation 部門

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2019 by Microsoft Corporation

著作權所有，並保留一切權利。 本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。

本書依照「現況」提供，代表作者的觀點和意見。 本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。

此處所描述的一些範例僅供說明，純屬虛構。 任何實際關聯或連結純屬巧合。

Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。

Mac 與 macOS 是 Apple Inc. 的商標。

所有其他商標和標誌屬於其各自擁有者的財產。

製作

> **[Daniel Roth](https://github.com/danroth27)** ，Microsoft Corp 的主要計畫經理。

> Microsoft Corp 的資深計畫經理 **[Jeff Fritz](https://github.com/csharpfritz)** 。

> **[Taylor Southwick](https://github.com/twsouthwick)** ，Microsoft Corp 的資深軟體工程師。

> **[Scott Addie](https://github.com/scottaddie)** ，Microsoft Corp 的資深內容開發人員。

## <a name="introduction"></a>簡介

.NET 透過 ASP.NET 提供長時間支援的 web 應用程式開發，這是一組完整的架構和工具，可用來建立任何類型的 web 應用程式。 ASP.NET 有自己的 web 架構和技術歷程，從傳統的 Active Server Pages （ASP）開始一直回到一步。 ASP.NET Web Forms、ASP.NET MVC、ASP.NET Web Pages 和最近 ASP.NET Core 的架構，可提供有效率且強大的方式來建立*伺服器呈現*的 Web 應用程式，其中 UI 內容是在伺服器上動態產生，以回應 HTTP發送. 每個 ASP.NET 架構都會已經考慮到不同的物件和應用程式建立原理。 ASP.NET 原始版本 .NET Framework 隨附的 Web form，並使用桌面開發人員熟悉的許多模式來啟用 網頁程式開發，例如可重複使用的 UI 控制項與簡單的事件處理。 不過，沒有任何 ASP.NET 供應專案會提供方法來執行在使用者的瀏覽器中執行的程式碼。 若要這麼做，需要撰寫 JavaScript，並使用多年來的任何 JavaScript 架構和工具： jQuery、挖式、角度、反應等等。

[Blazor](https://blazor.net)是新的 web 架構，可變更使用 .net 建立 web 應用程式時可能發生的情況。 Blazor 是以為基礎的用戶端 web UI 架構C# ，而不是 JavaScript。 透過 Blazor，您可以在中C#撰寫用戶端邏輯和 UI 元件、將它們編譯成一般的 .net 元件，然後使用稱為 WebAssembly 的新 open web standard，直接在瀏覽器中執行它們。 或者，Blazor 可以在伺服器上執行 .NET UI 元件，並處理與瀏覽器的即時連線流暢地的所有 UI 互動。 當與伺服器上執行的 .NET 配對時，Blazor 會啟用 .NET 的完整堆疊 網頁程式開發。 雖然 Blazor 與 ASP.NET Web form 共用許多共通性，例如擁有可重複使用的元件模型，以及處理使用者事件的簡單方法，但它也是以 .NET Core 的基礎為基礎，以提供現代化且高效能的 Web 開發體驗。

本書介紹 ASP.NET Web Forms 開發人員，以熟悉且方便的方式 Blazor。 它會以 ASP.NET Web form 中的類似概念來平行引進 Blazor 概念，同時說明可能較不熟悉的新概念。 其中涵蓋了各種主題和疑慮，包括元件撰寫、路由、版面配置、設定和安全性。 雖然本書的內容主要是用來啟用新的開發，但它也涵蓋了將現有的 ASP.NET Web form 遷移至 Blazor 的指導方針和策略，以供您想要將現有的應用程式現代化。

## <a name="who-should-use-the-book"></a>誰應該使用本書

本書適用于 ASP.NET Web form 開發人員，尋找與現有知識和技能相關的 Blazor 簡介。 本書可以協助您快速開始使用新的 Blazor 專案，或協助圖表現代化現有 ASP.NET Web Forms 應用程式的藍圖。

## <a name="how-to-use-the-book"></a>如何使用本書

本書的第一個部分涵蓋 Blazor 的內容，並將它與 web 應用程式開發與 ASP.NET Web form 做比較。 本書接著涵蓋各種不同的 Blazor 主題，一章章節，並將每個 Blazor 概念與 ASP.NET Web Forms 中的對應概念產生關聯，或完整說明所有全新的概念。 本書也會定期參考完整的範例應用程式，同時在 ASP.NET Web form 和 Blazor 中執行，以示範 Blazor 功能，並提供從 ASP.NET Web form 遷移至 Blazor 的案例研究。 您可以在[GitHub](https://github.com/dotnet-architecture/eshoponblazor)上找到範例應用程式的兩個（ASP.NET Web Forms 和 Blazor 版本）。

## <a name="what-this-book-doesnt-cover"></a>本書未涵蓋的內容

本書介紹 Blazor，而不是完整的遷移指南。 雖然其中包含如何將專案從 ASP.NET Web form 遷移至 Blazor 的指引，但並不會嘗試涵蓋每一種細微性和詳細資料。 如需從 ASP.NET 遷移至 ASP.NET Core 的一般指引，請參閱 ASP.NET Core 檔中的[遷移指引](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/)。

### <a name="additional-resources"></a>其他資源

您可以在<https://blazor.net>中找到官方 Blazor 首頁和檔。

## <a name="send-your-feedback"></a>傳送您的意見反應

這本書與相關範例不斷演進，所以您的意見反應歡迎！ 如果您有關于如何改進這本書的意見，請使用[GitHub 問題](https://github.com/dotnet/docs/issues)上任何網頁底部的 [意見反應] 區段。

>[!div class="step-by-step"]
>[下一步](introduction.md)
