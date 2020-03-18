---
title: 適用於 ASP.NET Web Forms 的 Blazor 開發人員
description: 瞭解如何使用 Blazor 和 .NET Core 以簡單和熟悉的方式使用 .NET 構建全堆疊 Web 應用程式。
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 394d11038b59f4cbe9e9955df43b6198eb5daaf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73088121"
---
# <a name="blazor-for-aspnet-web-forms-developers"></a>適用於 ASP.NET Web Forms 的 Blazor 開發人員

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![顯示無伺服器應用電子書封面的螢幕截圖。](./media/index/blazor-for-web-forms-developers-cover.png)

> 下載：<https://aka.ms/blazor-ebook>

發行者

Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組

Microsoft Corporation 部門

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2019 by Microsoft Corporation

著作權所有，並保留一切權利。 本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。

本書依照「現況」提供，代表作者的觀點和意見。 本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。

此處描述的一些範例僅供說明之用，純屬虛構。 並未影射或關聯任何真實的人、事、物。

Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。

Mac 與 macOS 是 Apple Inc. 的商標。

所有其他商標和標誌屬於其各自擁有者的財產。

作者：

> **[丹尼爾·羅斯](https://github.com/danroth27)**，微軟公司首席專案經理

> **[傑夫·弗裡茨](https://github.com/csharpfritz)**，微軟公司高級專案經理。

> **[泰勒·南威克](https://github.com/twsouthwick)**，微軟公司高級軟體工程師。

> **[斯科特·艾迪](https://github.com/scottaddie)**，微軟公司高級內容開發者。

## <a name="introduction"></a>簡介

.NET 長期以來一直通過ASP.NET支援 Web 應用開發，這是一套用於構建任何類型的 Web 應用的全套框架和工具。 ASP.NET有自己的 Web 框架和技術的血統，從經典活動伺服器頁面 （ASP） 開始。 ASP.NET Web 表單、ASP.NET MVC、ASP.NET 網頁以及最近ASP.NET Core 等框架提供了一種高效且強大的方法來構建*伺服器呈現的*Web 應用，其中 UI 內容在伺服器上動態生成以回應 HTTP 要求。 每個ASP.NET框架都迎合了不同的受眾和應用構建理念。 ASP.NET Web 表單隨 .NET Framework 的原始版本一起提供，並使用桌面開發人員熟悉的許多模式啟用 Web 開發，例如具有簡單事件處理的可重用 UI 控制項。 但是，ASP.NET產品都無法提供運行在使用者瀏覽器中執行的代碼的方法。 為此，需要編寫 JavaScript 並使用多年來逐漸流行和逐漸普及的許多 JavaScript 框架和工具中的任何一個：jQuery、挖空、角、反應等。

[Blazor](https://blazor.net)是一個新的 Web 框架，它改變了使用 .NET 構建 Web 應用時可能實現的內容。 Blazor 是基於 C# 而不是 JavaScript 的用戶端 Web UI 框架。 使用 Blazor，您可以在 C# 中編寫用戶端邏輯和 UI 元件，將它們編譯為正常的 .NET 程式集，然後使用稱為 WebAssembly 的新開放 Web 標準直接在瀏覽器中運行它們。 或者，Blazor 可以在伺服器上運行 .NET UI 元件，並在與瀏覽器的即時連接中流暢地處理所有 UI 交互。 與在伺服器上運行的 .NET 配對時，Blazor 支援使用 .NET 進行全堆疊 Web 開發。 雖然 Blazor 與 ASP.NET Web 表單有許多共同點，例如具有可重用的元件模型和處理使用者事件的簡單方法，但它也建立在 .NET Core 的基礎上，以提供現代和高性能的 Web 開發體驗。

本書以熟悉和方便的方式向布拉佐介紹了ASP.NET Web 表單開發人員。 它引入了 Blazor 概念，與ASP.NET Web 表單中的類似概念並行，同時解釋可能不太熟悉的新概念。 它涵蓋廣泛的主題和問題，包括元件創作、路由、佈局、配置和安全性。 雖然本書的內容主要是為了啟用新的開發，但它也涵蓋了將現有ASP.NET Web 表單遷移到 Blazor 的指南和策略，以便您更新現有應用。

## <a name="who-should-use-the-book"></a>誰應該用這本書

本書面向ASP.NET Web 表單開發人員，他們正在尋找有關他們現有知識和技能的 Blazor 簡介。 本書可以説明快速啟動基於 Blazor 的新專案，或者説明繪製現有ASP.NET Web 表單應用程式現代化的路線圖。

## <a name="how-to-use-the-book"></a>如何使用這本書

本書的第一部分介紹了 Blazor 的內容，並將其與 Web 應用開發與 ASP.NET Web 表單進行比較。 然後，這本書涵蓋了各種布拉佐爾主題，逐章，並將每個Blazor概念與ASP.NET Web 表單中的相應概念相關聯，或全面解釋任何全新的概念。 本書還定期提及在ASP.NET Web 表單和 Blazor 中實現的完整示例應用，以演示 Blazor 功能，並提供從ASP.NET Web 表單遷移到 Blazor 的案例研究。 您可以在[GitHub](https://github.com/dotnet-architecture/eshoponblazor)上找到示例應用（ASP.NET Web 表單和 Blazor 版本）的兩個實現。

## <a name="what-this-book-doesnt-cover"></a>這本書沒有涵蓋什麼

這本書是布拉佐爾的介紹，而不是全面的遷移指南。 雖然它包括有關如何處理從ASP.NET Web 表單遷移到 Blazor 的專案的指導，但它並不試圖涵蓋所有細微差別和細節。 有關從ASP.NET遷移到 ASP.NET 核心的更多一般指南，請參閱 ASP.NET 核心文檔中的[遷移指南](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/)。

### <a name="additional-resources"></a>其他資源

您可以在 找到官方布拉佐主頁和文檔在<https://blazor.net>。

## <a name="send-your-feedback"></a>傳送您的意見反應

本書和相關示例不斷演變，因此歡迎您的回饋！ 如果您對如何改進本書有意見，請使用基於[GitHub 問題](https://github.com/dotnet/docs/issues)構建的任何頁面底部的回饋部分。

>[!div class="step-by-step"]
>[下一步](introduction.md)
