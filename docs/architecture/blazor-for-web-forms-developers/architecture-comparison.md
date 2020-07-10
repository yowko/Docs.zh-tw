---
title: ASP.NET Web Forms 和的架構比較Blazor
description: 瞭解 ASP.NET Web Forms 和比較的架構 Blazor 。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/11/2019
ms.openlocfilehash: 51b114c842e131ad9b9a589bf5137a522e135082
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173428"
---
# <a name="architecture-comparison-of-aspnet-web-forms-and-blazor"></a><span data-ttu-id="d1ee2-103">ASP.NET Web Forms 和的架構比較Blazor</span><span class="sxs-lookup"><span data-stu-id="d1ee2-103">Architecture comparison of ASP.NET Web Forms and Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="d1ee2-104">雖然 ASP.NET Web form 並 Blazor 有許多相似的概念，但它們的使用方式也有所差異。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-104">While ASP.NET Web Forms and Blazor have many similar concepts, there are differences in how they work.</span></span> <span data-ttu-id="d1ee2-105">本章將探討 ASP.NET Web form 和的內部運作和架構 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-105">This chapter examines the inner workings and architectures of ASP.NET Web Forms and Blazor.</span></span>

## <a name="aspnet-web-forms"></a><span data-ttu-id="d1ee2-106">ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="d1ee2-106">ASP.NET Web Forms</span></span>

<span data-ttu-id="d1ee2-107">ASP.NET Web Forms 架構是以頁面為中心的架構為基礎。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-107">The ASP.NET Web Forms framework is based on a page-centric architecture.</span></span> <span data-ttu-id="d1ee2-108">應用程式中某個位置的每個 HTTP 要求，都是 ASP.NET 回應的個別頁面。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-108">Each HTTP request for a location in the app is a separate page with which ASP.NET responds.</span></span> <span data-ttu-id="d1ee2-109">當要求頁面時，瀏覽器的內容會被要求的頁面結果取代。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-109">As pages are requested, the contents of the browser are replaced with the results of the page requested.</span></span>

<span data-ttu-id="d1ee2-110">頁面包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="d1ee2-110">Pages consist of the following components:</span></span>

- <span data-ttu-id="d1ee2-111">HTML 標籤</span><span class="sxs-lookup"><span data-stu-id="d1ee2-111">HTML markup</span></span>
- <span data-ttu-id="d1ee2-112">C# 或 Visual Basic 程式碼</span><span class="sxs-lookup"><span data-stu-id="d1ee2-112">C# or Visual Basic code</span></span>
- <span data-ttu-id="d1ee2-113">包含邏輯和事件處理功能的程式碼後置類別</span><span class="sxs-lookup"><span data-stu-id="d1ee2-113">A code-behind class containing logic and event-handling capabilities</span></span>
- <span data-ttu-id="d1ee2-114">控制項</span><span class="sxs-lookup"><span data-stu-id="d1ee2-114">Controls</span></span>

<span data-ttu-id="d1ee2-115">控制項是可重複使用的 web UI 單位，可以透過程式設計方式在頁面上放置和互動。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-115">Controls are reusable units of web UI that can be programmatically placed and interacted with on a page.</span></span> <span data-ttu-id="d1ee2-116">頁面是由以 *.aspx*結尾的檔案所組成，其中包含標記、控制項和一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-116">Pages are composed of files that end with *.aspx* containing markup, controls, and some code.</span></span> <span data-ttu-id="d1ee2-117">程式碼後置類別位於具有相同基底名稱和*aspx.cs*或 *.aspx*副檔名的檔案中，視所使用的程式語言而定。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-117">The code-behind classes are in files with the same base name and an *.aspx.cs* or *.aspx.vb* extension, depending on the programming language used.</span></span> <span data-ttu-id="d1ee2-118">有趣的是，web 伺服器會解讀 *.aspx*檔案的內容，並在每次變更時進行編譯。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-118">Interestingly, the web server interprets contents of the *.aspx* files and compiles them whenever they change.</span></span> <span data-ttu-id="d1ee2-119">即使 web 伺服器已經在執行中，也會進行重新編譯。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-119">This recompilation occurs even if the web server is already running.</span></span>

<span data-ttu-id="d1ee2-120">控制項可以使用標記來建立，並以使用者控制項的形式傳遞。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-120">Controls can be built with markup and delivered as user controls.</span></span> <span data-ttu-id="d1ee2-121">使用者控制項衍生自 `UserControl` 類別，並具有與頁面相似的結構。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-121">A user control derives from the `UserControl` class and has a similar structure to the Page.</span></span> <span data-ttu-id="d1ee2-122">使用者控制項的標記會儲存在 *.ascx*檔案中。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-122">Markup for user controls is stored in an *.ascx* file.</span></span> <span data-ttu-id="d1ee2-123">隨附的程式碼後置類別位於*ascx.cs*或 *.ascx*檔案中。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-123">An accompanying code-behind class resides in an *.ascx.cs* or *.ascx.vb* file.</span></span> <span data-ttu-id="d1ee2-124">控制項也可以完全使用程式碼來建立，方法是繼承自 `WebControl` 或 `CompositeControl` 基類。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-124">Controls can also be built completely with code, by inheriting from either the `WebControl` or `CompositeControl` base class.</span></span>

<span data-ttu-id="d1ee2-125">頁面也有廣泛的事件生命週期。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-125">Pages also have an extensive event lifecycle.</span></span> <span data-ttu-id="d1ee2-126">當 ASP.NET 執行時間針對每個要求執行頁面的程式碼時，每個頁面都會引發初始化、載入、呈現和卸載事件的事件。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-126">Each page raises events for the initialization, load, prerender, and unload events that occur as the ASP.NET runtime executes the page's code for each request.</span></span>

<span data-ttu-id="d1ee2-127">頁面上的控制項通常會回傳至呈現控制項的相同頁面，並從稱為的隱藏表單欄位中，攜帶其承載 `ViewState` 。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-127">Controls on a Page typically post-back to the same page that presented the control, and carry along with them a payload from a hidden form field called `ViewState`.</span></span> <span data-ttu-id="d1ee2-128">`ViewState`欄位包含控制項在呈現和呈現在頁面上時的狀態相關資訊，可讓 ASP.NET 執行時間比較和識別提交至伺服器之內容中的變更。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-128">The `ViewState` field contains information about the state of the controls at the time they were rendered and presented on the page, allowing the ASP.NET runtime to compare and identify changes in the content submitted to the server.</span></span>

## Blazor

Blazor<span data-ttu-id="d1ee2-129">是一種用戶端 web UI 架構，本質上類似于 JavaScript 前端架構，例如角度或反應。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-129"> is a client-side web UI framework similar in nature to JavaScript front-end frameworks like Angular or React.</span></span> Blazor<span data-ttu-id="d1ee2-130">處理使用者互動，並呈現必要的 UI 更新。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-130"> handles user interactions and renders the necessary UI updates.</span></span> Blazor<span data-ttu-id="d1ee2-131">*不*是以要求-回復模型為基礎。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-131"> *isn't* based on a request-reply model.</span></span> <span data-ttu-id="d1ee2-132">使用者互動會當做不在任何特定 HTTP 要求內容中的事件來處理。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-132">User interactions are handled as events that aren't in the context of any particular HTTP request.</span></span>

Blazor<span data-ttu-id="d1ee2-133">應用程式是由一個或多個在 HTML 網頁上轉譯的根元件所組成。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-133"> apps consist of one or more root components that are rendered on an HTML page.</span></span>

<span data-ttu-id="d1ee2-134">![BlazorHTML 中的元件](./media/architecture-comparison/blazor-components-in-html.png)</span><span class="sxs-lookup"><span data-stu-id="d1ee2-134">![Blazor components in HTML](./media/architecture-comparison/blazor-components-in-html.png)</span></span>

<span data-ttu-id="d1ee2-135">使用者如何指定元件應該呈現的位置，以及如何讓元件連線以進行使用者互動，就是[裝載模型](hosting-models.md)特定。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-135">How the user specifies where components should render and how the components are then wired up for user interactions is [hosting model](hosting-models.md) specific.</span></span>

Blazor<span data-ttu-id="d1ee2-136">[元件](components.md)是代表可重複使用之 UI 片段的 .net 類別。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-136"> [components](components.md) are .NET classes that represent a reusable piece of UI.</span></span> <span data-ttu-id="d1ee2-137">每個元件都會維護它自己的狀態，並指定自己的轉譯邏輯，其中可能包含呈現其他元件。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-137">Each component maintains its own state and specifies its own rendering logic, which can include rendering other components.</span></span> <span data-ttu-id="d1ee2-138">元件會指定特定使用者互動的事件處理常式，以更新元件的狀態。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-138">Components specify event handlers for specific user interactions to update the component's state.</span></span>

<span data-ttu-id="d1ee2-139">在元件處理事件之後，會轉譯 Blazor 該元件，並追蹤已轉譯輸出中的變更。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-139">After a component handles an event, Blazor renders the component and keeps track of what changed in the rendered output.</span></span> <span data-ttu-id="d1ee2-140">元件不會直接轉譯成檔物件模型 (DOM) 。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-140">Components don't render directly to the Document Object Model (DOM).</span></span> <span data-ttu-id="d1ee2-141">它們會改為轉譯成 DOM 的記憶體中表示，稱為， `RenderTree` 以便 Blazor 追蹤變更。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-141">They instead render to an in-memory representation of the DOM called a `RenderTree` so that Blazor can track the changes.</span></span> Blazor<span data-ttu-id="d1ee2-142">比較新呈現的輸出與先前的輸出，以計算 UI 差異，然後將其有效率地套用至 DOM。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-142"> compares the newly rendered output with the previous output to calculate a UI diff that it then applies efficiently to the DOM.</span></span>

<span data-ttu-id="d1ee2-143">![BlazorDOM 互動](./media/architecture-comparison/blazor-dom-interaction.png)</span><span class="sxs-lookup"><span data-stu-id="d1ee2-143">![Blazor DOM interaction](./media/architecture-comparison/blazor-dom-interaction.png)</span></span>

<span data-ttu-id="d1ee2-144">元件也可以手動指示，如果它們的狀態在一般 UI 事件之外發生變更，就應該加以呈現。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-144">Components can also manually indicate that they should be rendered if their state changes outside of a normal UI event.</span></span> Blazor<span data-ttu-id="d1ee2-145">會使用 `SynchronizationContext` 來強制執行單一邏輯執行緒。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-145"> uses a `SynchronizationContext` to enforce a single logical thread of execution.</span></span> <span data-ttu-id="d1ee2-146">Blazor會在這個上執行元件的生命週期方法和所引發的任何事件回呼 `SynchronizationContext` 。</span><span class="sxs-lookup"><span data-stu-id="d1ee2-146">A component's lifecycle methods and any event callbacks that are raised by Blazor are executed on this `SynchronizationContext`.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d1ee2-147">[上一個](introduction.md) 
>[下一步](hosting-models.md)</span><span class="sxs-lookup"><span data-stu-id="d1ee2-147">[Previous](introduction.md)
[Next](hosting-models.md)</span></span>
