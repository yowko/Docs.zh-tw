---
title: ASP.NET Web Forms 和的架構比較 Blazor
description: 瞭解 ASP.NET Web Forms 與比較的架構 Blazor 。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 11/20/2020
ms.openlocfilehash: afb5d4025b81c2ddef782c462c94d32edc872a21
ms.sourcegitcommit: 2f485e721f7f34b87856a51181b5b56624b31fd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509724"
---
# <a name="architecture-comparison-of-aspnet-web-forms-and-no-locblazor"></a>ASP.NET Web Forms 和的架構比較 Blazor

雖然 ASP.NET Web Forms 並 Blazor 有許多類似的概念，但它們的運作方式有所差異。 本章將探討 ASP.NET Web Forms 和的內部運作和架構 Blazor 。

## <a name="aspnet-web-forms"></a>ASP.NET Web Forms

ASP.NET Web Forms framework 是以以頁面為中心的架構為基礎。 應用程式中某個位置的每個 HTTP 要求都是 ASP.NET 回應的個別頁面。 要求頁面時，瀏覽器的內容會取代為所要求頁面的結果。

頁面包含下列元件：

- HTML 標籤
- C# 或 Visual Basic 程式碼
- 包含邏輯和事件處理功能的程式碼後端類別
- 控制項

控制項是可重複使用的 web UI 單位，可透過程式設計的方式在頁面上進行放置和互動。 頁面是由包含標記、控制項和一些程式碼的 *.aspx* 結尾的檔案所組成。 程式碼後端類別位於具有相同基底名稱和 *aspx.cs* 或 *.aspx* 副檔名的檔案中，視所使用的程式設計語言而定。 有趣的是，網頁伺服器會解釋 *.aspx* 檔案的內容，並在每次變更時進行編譯。 即使 web 伺服器已經在執行中，還是會發生重新編譯。

您可以使用標記來建立控制項，並以使用者控制項的形式傳遞。 使用者控制項衍生自 `UserControl` 類別，而且具有類似于頁面的結構。 使用者控制項的標記會儲存在 *.ascx* 檔案中。 隨附的程式碼後端類別位於 *ascx.cs* 或 *.ascx* 檔案中。 您也可以從或基類繼承，藉由程式碼完全建立 `WebControl` 控制項 `CompositeControl` 。

頁面也有大量的事件生命週期。 每個頁面都會針對 ASP.NET 執行時間針對每個要求執行頁面程式碼時所發生的初始化、載入、呈現和卸載事件，引發事件。

頁面上的控制項通常會回傳至呈現控制項的相同頁面，並且會從名為的隱藏表單欄位中執行承載 `ViewState` 。 `ViewState`欄位包含控制項在頁面上呈現和呈現時的狀態相關資訊，可讓 ASP.NET 執行時間比較及識別提交至伺服器之內容中的變更。

## Blazor

Blazor 用戶端 web UI 架構的本質類似于 JavaScript 前端架構，例如角度或回應。 Blazor 處理使用者互動，並呈現必要的 UI 更新。 Blazor*不* 是以要求-回復模型為基礎。 使用者互動會以非任何特定 HTTP 要求內容中的事件來處理。

Blazor 應用程式是由一個或多個在 HTML 網頁上轉譯的根元件所組成。

![：：：非 loc (Blazor) ：：： HTML 中的元件](./media/architecture-comparison/blazor-components-in-html.png)

使用者如何指定應該呈現元件的位置，以及如何將元件連線到使用者互動的方式，就是 [裝載模型](hosting-models.md) 特定。

Blazor[元件](components.md)是代表可重複使用之 UI 片段的 .net 類別。 每個元件都會維護它自己的狀態，並指定自己的轉譯邏輯，其中可能包括呈現其他元件。 元件會指定特定使用者互動的事件處理常式，以更新元件的狀態。

在元件處理事件之後，轉譯 Blazor 元件，並追蹤轉譯輸出中的變更內容。 元件不會直接轉譯為檔物件模型的 (DOM) 。 它們會改為轉譯為 DOM 的記憶體中標記法， `RenderTree` 以便 Blazor 追蹤變更。 Blazor 比較新轉譯的輸出與先前的輸出，以計算可有效率地套用至 DOM 的 UI 差異。

![：：：非 loc (Blazor) ：：： DOM 互動](./media/architecture-comparison/blazor-dom-interaction.png)

元件也可以手動指出，如果它們的狀態在一般 UI 事件之外變更，則應該加以呈現。 Blazor 使用 `SynchronizationContext` 來強制執行單一邏輯執行緒。 元件的生命週期方法和引發的任何事件回呼 Blazor 都會在這個上執行 `SynchronizationContext` 。

>[!div class="step-by-step"]
>[上一個](introduction.md) 
>[下一步](hosting-models.md)
