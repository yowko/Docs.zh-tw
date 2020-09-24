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
# <a name="no-locblazor-for-aspnet-web-forms-developers"></a><span data-ttu-id="3c8dc-103">Blazor 適用于 ASP.NET Web Forms 開發人員</span><span class="sxs-lookup"><span data-stu-id="3c8dc-103">Blazor for ASP.NET Web Forms Developers</span></span>

![顯示「無伺服器應用程式」電子書封面的螢幕擷取畫面。](./media/index/blazor-for-aspnet-web-forms-developers.png)

> <span data-ttu-id="3c8dc-105">下載：<https://aka.ms/blazor-ebook></span><span class="sxs-lookup"><span data-stu-id="3c8dc-105">DOWNLOAD available at: <https://aka.ms/blazor-ebook></span></span>

<span data-ttu-id="3c8dc-106">發行者</span><span class="sxs-lookup"><span data-stu-id="3c8dc-106">PUBLISHED BY</span></span>

<span data-ttu-id="3c8dc-107">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="3c8dc-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="3c8dc-108">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="3c8dc-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="3c8dc-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="3c8dc-109">One Microsoft Way</span></span>

<span data-ttu-id="3c8dc-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="3c8dc-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="3c8dc-111">Microsoft Corporation 的著作權©2020</span><span class="sxs-lookup"><span data-stu-id="3c8dc-111">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="3c8dc-112">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-112">All rights reserved.</span></span> <span data-ttu-id="3c8dc-113">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="3c8dc-114">本書依照「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="3c8dc-115">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-115">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="3c8dc-116">此處描述的一些範例僅供說明之用，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="3c8dc-117">並未影射或關聯任何真實的人、事、物。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="3c8dc-118">Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-118">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="3c8dc-119">Mac 與 macOS 是 Apple Inc. 的商標。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="3c8dc-120">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="3c8dc-121">作者：</span><span class="sxs-lookup"><span data-stu-id="3c8dc-121">Authors:</span></span>

> <span data-ttu-id="3c8dc-122">Microsoft Corp 的首席專案經理**[Daniel Roth](https://github.com/danroth27)**。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-122">**[Daniel Roth](https://github.com/danroth27)**, Principal Program Manager, Microsoft Corp.</span></span>

> <span data-ttu-id="3c8dc-123">Microsoft Corp 資深專案經理**[Jeff Fritz](https://github.com/csharpfritz)**。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-123">**[Jeff Fritz](https://github.com/csharpfritz)**, Senior Program Manager, Microsoft Corp.</span></span>

> <span data-ttu-id="3c8dc-124">Microsoft Corp 資深軟體工程師**[Taylor Southwick](https://github.com/twsouthwick)**。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-124">**[Taylor Southwick](https://github.com/twsouthwick)**, Senior Software Engineer, Microsoft Corp.</span></span>

> <span data-ttu-id="3c8dc-125">**[Scott Addie](https://github.com/scottaddie)**，資深內容開發人員，Microsoft Corp。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-125">**[Scott Addie](https://github.com/scottaddie)**, Senior Content Developer, Microsoft Corp.</span></span>

> <span data-ttu-id="3c8dc-126">**[Steve "ardalis" Smith](https://ardalis.com)**，軟體架構設計人員和訓練員，ARDALIS Services LLC</span><span class="sxs-lookup"><span data-stu-id="3c8dc-126">**[Steve "ardalis" Smith](https://ardalis.com)**, Software Architect and Trainer, Ardalis Services LLC</span></span>

## <a name="introduction"></a><span data-ttu-id="3c8dc-127">簡介</span><span class="sxs-lookup"><span data-stu-id="3c8dc-127">Introduction</span></span>

<span data-ttu-id="3c8dc-128">.NET 透過 ASP.NET 提供長時間支援的 web 應用程式開發，這是一組完整的架構和工具，可用來建立任何類型的 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-128">.NET has long supported web app development through ASP.NET, a comprehensive set of frameworks and tools for building any kind of web app.</span></span> <span data-ttu-id="3c8dc-129">ASP.NET 有自己的 web 架構和技術歷程，從傳統的 Active Server Pages (ASP) 開始。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-129">ASP.NET has its own lineage of web frameworks and technologies starting all the way back with classic Active Server Pages (ASP).</span></span> <span data-ttu-id="3c8dc-130">ASP.NET Web Forms、ASP.NET MVC、ASP.NET Web Pages 等架構，以及最新 ASP.NET Core 的架構，可提供具生產力且功能強大的方式來建立 *伺服器呈現* 的 Web 應用程式，以在伺服器上動態產生 UI 內容以回應 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-130">Frameworks like ASP.NET Web Forms, ASP.NET MVC, ASP.NET Web Pages, and more recently ASP.NET Core, provide a productive and powerful way to build *server-rendered* web apps, where UI content is dynamically generated on the server in response to HTTP requests.</span></span> <span data-ttu-id="3c8dc-131">每個 ASP.NET 架構都已經考慮至不同的物件和應用程式建立原理。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-131">Each ASP.NET framework caters to a different audience and app building philosophy.</span></span> <span data-ttu-id="3c8dc-132">ASP.NET Web Forms 隨附于原始版本的 .NET Framework，並使用許多桌面開發人員熟悉的模式來啟用 Web 開發，例如可重複使用的 UI 控制項，以及簡單的事件處理。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-132">ASP.NET Web Forms shipped with the original release of the .NET Framework and enabled web development using many of the patterns familiar to desktop developers, like reusable UI controls with simple event handling.</span></span> <span data-ttu-id="3c8dc-133">不過，沒有任何 ASP.NET 供應專案會提供方法來執行在使用者的瀏覽器中執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-133">However, none of the ASP.NET offerings provide a way to run code that executed in the user's browser.</span></span> <span data-ttu-id="3c8dc-134">若要這麼做，需要撰寫 JavaScript，並使用許多 JavaScript 架構和工具，這些架構和工具在過去幾年內都有可能出現和不受歡迎： jQuery、挖起、角度、反應等。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-134">To do that requires writing JavaScript and using any of the many JavaScript frameworks and tools that have phased in and out of popularity over the years: jQuery, Knockout, Angular, React, and so on.</span></span>

<span data-ttu-id="3c8dc-135">[Blazor](https://blazor.net) 是新的 web 架構，可變更使用 .NET 建立 web 應用程式時可能發生的情況。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-135">[Blazor](https://blazor.net) is a new web framework that changes what is possible when building web apps with .NET.</span></span> <span data-ttu-id="3c8dc-136">Blazor 是以 c # 為基礎的用戶端 web UI 架構，而不是 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-136">Blazor is a client-side web UI framework based on C# instead of JavaScript.</span></span> <span data-ttu-id="3c8dc-137">Blazor您可以使用以 c # 撰寫用戶端邏輯和 UI 元件、將它們編譯成一般的 .net 元件，然後使用名為的新開放式 web 標準，直接在瀏覽器中執行它們 WebAssembly 。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-137">With Blazor you can write your client-side logic and UI components in C#, compile them into normal .NET assemblies, and then run them directly in the browser using a new open web standard called WebAssembly.</span></span> <span data-ttu-id="3c8dc-138">或者，也 Blazor 可以在伺服器上執行 .NET UI 元件，並透過瀏覽器的即時連線來處理所有 UI 互動流暢地。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-138">Or alternatively, Blazor can run your .NET UI components on the server and handle all UI interactions fluidly over a real-time connection with the browser.</span></span> <span data-ttu-id="3c8dc-139">當與在伺服器上執行的 .NET 搭配使用時， Blazor 可使用 .net 進行完整堆疊的 網頁程式開發。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-139">When paired with .NET running on the server, Blazor enables full-stack web development with .NET.</span></span> <span data-ttu-id="3c8dc-140">雖然 Blazor 與 ASP.NET Web Forms 共用許多共通性，例如擁有可重複使用的元件模型，以及處理使用者事件的簡單方法，但它也是以 .Net Core 的基礎為基礎，以提供現代化且高效能的 Web 開發體驗。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-140">While Blazor shares many commonalities with ASP.NET Web Forms, like having a reusable component model and a simple way to handle user events, it also builds on the foundations of .NET Core to provide a modern and high performance web development experience.</span></span>

<span data-ttu-id="3c8dc-141">本書以熟悉且方便的方式，介紹 ASP.NET Web Forms 開發人員 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-141">This book introduces ASP.NET Web Forms developers to Blazor in a way that is familiar and convenient.</span></span> <span data-ttu-id="3c8dc-142">它會以 Blazor ASP.NET Web Forms 中的類似概念來平行引進概念，同時也會說明可能較不熟悉的新概念。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-142">It introduces Blazor concepts in parallel with analogous concepts in ASP.NET Web Forms while also explaining new concepts that may be less familiar.</span></span> <span data-ttu-id="3c8dc-143">其中涵蓋各種主題和問題，包括元件撰寫、路由、配置、設定和安全性。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-143">It covers a broad range of topics and concerns including component authoring, routing, layout, configuration, and security.</span></span> <span data-ttu-id="3c8dc-144">雖然本書的內容主要是用來啟用新的開發，但它也涵蓋了將現有的 ASP.NET Web Forms 遷移至的指導方針和策略，以便將現有 Blazor 的應用程式現代化。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-144">And while the content of this book is primarily for enabling new development, it also covers guidelines and strategies for migrating existing ASP.NET Web Forms to Blazor for when you want to modernize an existing app.</span></span>

## <a name="who-should-use-the-book"></a><span data-ttu-id="3c8dc-145">誰應該使用書</span><span class="sxs-lookup"><span data-stu-id="3c8dc-145">Who should use the book</span></span>

<span data-ttu-id="3c8dc-146">這本書適用于 ASP.NET Web Forms 開發人員尋找與 Blazor 現有知識和技能相關的簡介。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-146">This book is for ASP.NET Web Forms developers looking for an introduction to Blazor that relates to their existing knowledge and skills.</span></span> <span data-ttu-id="3c8dc-147">本書可協助您快速開始使用新 Blazor 的專案，或協助圖表現代化現有 ASP.NET Web Forms 應用程式的藍圖。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-147">This book can help with quickly getting started on a new Blazor-based project or to help chart a roadmap for modernizing an existing ASP.NET Web Forms application.</span></span>

## <a name="how-to-use-the-book"></a><span data-ttu-id="3c8dc-148">如何使用書</span><span class="sxs-lookup"><span data-stu-id="3c8dc-148">How to use the book</span></span>

<span data-ttu-id="3c8dc-149">本書的第一個部分涵蓋了什麼， Blazor 並將其與 ASP.NET Web Forms 的 web 應用程式開發做比較。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-149">The first part of this book covers what Blazor is and compares it to web app development with ASP.NET Web Forms.</span></span> <span data-ttu-id="3c8dc-150">本書接著涵蓋各種 Blazor 主題（依章節），並將每個概念與 Blazor ASP.NET Web Forms 中的對應概念建立關聯，或徹底說明所有全新的概念。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-150">The book then covers a variety of Blazor topics, chapter by chapter, and relates each Blazor concept to the corresponding concept in ASP.NET Web Forms, or explains fully any completely new concepts.</span></span> <span data-ttu-id="3c8dc-151">本書也會定期參考在 ASP.NET Web Forms 中執行的完整範例應用程式，並 Blazor 示範 Blazor 功能以及提供從 ASP.NET Web Forms 遷移至的案例研究 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-151">The book also refers regularly to a complete sample app implemented in both ASP.NET Web Forms and Blazor to demonstrate Blazor features and to provide a case study for migrating from ASP.NET Web Forms to Blazor.</span></span> <span data-ttu-id="3c8dc-152">您可以在 GitHub 上找到範例應用程式的兩個 (ASP.NET Web Forms 和 Blazor 版本) 。 [GitHub](https://github.com/dotnet-architecture/eshoponblazor)</span><span class="sxs-lookup"><span data-stu-id="3c8dc-152">You can find both implementations of the sample app (ASP.NET Web Forms and Blazor versions) on [GitHub](https://github.com/dotnet-architecture/eshoponblazor).</span></span>

## <a name="what-this-book-doesnt-cover"></a><span data-ttu-id="3c8dc-153">本書未涵蓋的內容</span><span class="sxs-lookup"><span data-stu-id="3c8dc-153">What this book doesn't cover</span></span>

<span data-ttu-id="3c8dc-154">這本書是的簡介 Blazor ，而不是完整的遷移指南。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-154">This book is an introduction to Blazor, not a comprehensive migration guide.</span></span> <span data-ttu-id="3c8dc-155">雖然它包含有關如何將專案從 ASP.NET Web Forms 遷移至的指引 Blazor ，但並不會嘗試涵蓋每個微妙和詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-155">While it does include guidance on how to approach migrating a project from ASP.NET Web Forms to Blazor, it does not attempt to cover every nuance and detail.</span></span> <span data-ttu-id="3c8dc-156">如需從 ASP.NET 遷移至 ASP.NET Core 的一般指引，請參閱 ASP.NET Core 檔中的 [遷移指導](/aspnet/core/migration/proper-to-2x/) 方針。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-156">For more general guidance on migrating from ASP.NET to ASP.NET Core, refer to the [migration guidance](/aspnet/core/migration/proper-to-2x/) in the ASP.NET Core documentation.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3c8dc-157">其他資源</span><span class="sxs-lookup"><span data-stu-id="3c8dc-157">Additional resources</span></span>

<span data-ttu-id="3c8dc-158">您可以在中找到官方首頁 Blazor 和檔 <https://blazor.net> 。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-158">You can find the official Blazor home page and documentation at <https://blazor.net>.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="3c8dc-159">傳送您的意見反應</span><span class="sxs-lookup"><span data-stu-id="3c8dc-159">Send your feedback</span></span>

<span data-ttu-id="3c8dc-160">本書和相關的範例不斷演進，所以您的意見反應歡迎！</span><span class="sxs-lookup"><span data-stu-id="3c8dc-160">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="3c8dc-161">如果您有關于如何改進本書的意見，請使用內建于 [GitHub 問題](https://github.com/dotnet/docs/issues)之任何頁面底部的意見反應區段。</span><span class="sxs-lookup"><span data-stu-id="3c8dc-161">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="3c8dc-162">下一個</span><span class="sxs-lookup"><span data-stu-id="3c8dc-162">Next</span></span>](introduction.md)
