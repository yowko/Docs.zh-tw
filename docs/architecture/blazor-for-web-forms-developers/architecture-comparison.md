---
title: ASP.NET Web Forms 和 Blazor 的架構比較
description: 瞭解 ASP.NET Web Forms 和 Blazor 的架構比較。
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 1137218e1cd99a39240592be415f734223e90b77
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183956"
---
# <a name="architecture-comparison-of-aspnet-web-forms-and-blazor"></a>ASP.NET Web Forms 和 Blazor 的架構比較

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

雖然 ASP.NET Web form 和 Blazor 有許多相似的概念，但它們的使用方式有所差異。 本章將探討 ASP.NET Web Forms 和 Blazor 的內部工作和架構。

## <a name="aspnet-web-forms"></a>ASP.NET Web Form

ASP.NET Web Forms 架構是以頁面為中心的架構為基礎。 應用程式中某個位置的每個 HTTP 要求，都是 ASP.NET 回應的個別頁面。 當要求頁面時，瀏覽器的內容會被要求的頁面結果取代。

頁面包含下列元件：

* HTML 標籤
* C# 或 Visual Basic 程式碼
* 包含邏輯和事件處理功能的程式碼後置類別
* 控制項

控制項是可重複使用的 web UI 單位，可以透過程式設計方式在頁面上放置和互動。 頁面是由以 *.aspx*結尾的檔案所組成，其中包含標記、控制項和一些程式碼。 程式碼後置類別位於具有相同基底名稱和*aspx.cs*或 *.aspx*副檔名的檔案中，視所使用的程式語言而定。 有趣的是，web 伺服器會解讀 *.aspx*檔案的內容，並在每次變更時進行編譯。 即使 web 伺服器已經在執行中，也會進行重新編譯。

控制項可以使用標記來建立，並以使用者控制項的形式傳遞。 使用者控制項衍生自`UserControl`類別，並具有與頁面相似的結構。 使用者控制項的標記會儲存在 *.ascx*檔案中。 隨附的程式碼後置類別位於*ascx.cs*或 *.ascx*檔案中。 控制項也可以完全使用程式碼來建立，方法是繼承自`WebControl`或`CompositeControl`基類。

頁面也有廣泛的事件生命週期。 當 ASP.NET 執行時間針對每個要求執行頁面的程式碼時，每個頁面都會引發初始化、載入、呈現和卸載事件的事件。

頁面上的控制項通常會回傳至呈現控制項的相同頁面，並從稱為`ViewState`的隱藏表單欄位中，攜帶其承載。 `ViewState`欄位包含控制項在呈現和呈現在頁面上時的狀態相關資訊，可讓 ASP.NET 執行時間比較和識別提交至伺服器之內容中的變更。

## <a name="blazor"></a>Blazor

Blazor 是與 JavaScript 前端架構（例如角度或回應）本質相似的用戶端 web UI 架構。 Blazor 會處理使用者互動，並呈現必要的 UI 更新。 Blazor*不*是以要求-回復模型為基礎。 使用者互動會當做不在任何特定 HTTP 要求內容中的事件來處理。

Blazor 應用程式是由一個或多個在 HTML 網頁上轉譯的根元件所組成。

![HTML 中的 Blazor 元件](./media/architecture-comparison/blazor-components-in-html.png)

使用者如何指定元件應該呈現的位置，以及如何讓元件連線以進行使用者互動，就是[裝載模型](hosting-models.md)特定。

Blazor[元件](components.md)是代表可重複使用之 UI 部分的 .net 類別。 每個元件都會維護它自己的狀態，並指定自己的轉譯邏輯，其中可能包含呈現其他元件。 元件會指定特定使用者互動的事件處理常式，以更新元件的狀態。

在元件處理事件之後，Blazor 會轉譯該元件，並追蹤已轉譯輸出中變更的專案。 元件不會直接轉譯為檔物件模型（DOM）。 它們會改為轉譯成 DOM 的記憶體中表示，稱為`RenderTree` ，讓 Blazor 可以追蹤變更。 Blazor 會比較新呈現的輸出與先前的輸出，以計算 UI 差異，然後將其有效率地套用至 DOM。

![Blazor DOM 互動](./media/architecture-comparison/blazor-dom-interaction.png)

元件也可以手動指示，如果它們的狀態在一般 UI 事件之外發生變更，就應該加以呈現。 Blazor 會使用`SynchronizationContext`來強制執行單一邏輯執行緒。 元件的生命週期方法以及 Blazor 所引發的任何事件回呼都會在這個`SynchronizationContext`上執行。

>[!div class="step-by-step"]
>[上一頁](introduction.md)
>[下一頁](hosting-models.md)
