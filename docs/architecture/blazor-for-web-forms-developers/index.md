---
title: Blazor適用于 ASP.NET Web Forms 開發人員
description: 瞭解如何以 Blazor 簡單且熟悉的方式，使用和 .Net Core 來建立具有 .net 的完整堆疊 web 應用程式。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 09/11/2019
ms.openlocfilehash: 779eb47d9796c61df9939d0e7de287443870576e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173246"
---
# <a name="blazor-for-aspnet-web-forms-developers"></a>Blazor<span data-ttu-id="fae37-103">適用于 ASP.NET Web Forms 開發人員</span><span class="sxs-lookup"><span data-stu-id="fae37-103"> for ASP.NET Web Forms Developers</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![顯示無伺服器應用程式電子書封面的螢幕擷取畫面。](./media/index/blazor-for-web-forms-developers-cover.png)

> <span data-ttu-id="fae37-105">下載：<https://aka.ms/blazor-ebook></span><span class="sxs-lookup"><span data-stu-id="fae37-105">DOWNLOAD available at: <https://aka.ms/blazor-ebook></span></span>

<span data-ttu-id="fae37-106">發行者</span><span class="sxs-lookup"><span data-stu-id="fae37-106">PUBLISHED BY</span></span>

<span data-ttu-id="fae37-107">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="fae37-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="fae37-108">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="fae37-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="fae37-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="fae37-109">One Microsoft Way</span></span>

<span data-ttu-id="fae37-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="fae37-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="fae37-111">Copyright © 2019 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="fae37-111">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="fae37-112">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="fae37-112">All rights reserved.</span></span> <span data-ttu-id="fae37-113">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="fae37-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="fae37-114">本書依照「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="fae37-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="fae37-115">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="fae37-115">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="fae37-116">此處描述的一些範例僅供說明之用，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="fae37-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="fae37-117">並未影射或關聯任何真實的人、事、物。</span><span class="sxs-lookup"><span data-stu-id="fae37-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="fae37-118">Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="fae37-118">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="fae37-119">Mac 與 macOS 是 Apple Inc. 的商標。</span><span class="sxs-lookup"><span data-stu-id="fae37-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="fae37-120">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="fae37-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="fae37-121">作者：</span><span class="sxs-lookup"><span data-stu-id="fae37-121">Authors:</span></span>

> <span data-ttu-id="fae37-122">**[Daniel Roth](https://github.com/danroth27)**，Microsoft Corp 的主要計畫經理。</span><span class="sxs-lookup"><span data-stu-id="fae37-122">**[Daniel Roth](https://github.com/danroth27)**, Principal Program Manager, Microsoft Corp.</span></span>

> <span data-ttu-id="fae37-123">Microsoft Corp 的資深計畫經理**[Jeff Fritz](https://github.com/csharpfritz)**。</span><span class="sxs-lookup"><span data-stu-id="fae37-123">**[Jeff Fritz](https://github.com/csharpfritz)**, Senior Program Manager, Microsoft Corp.</span></span>

> <span data-ttu-id="fae37-124">**[Taylor Southwick](https://github.com/twsouthwick)**，Microsoft Corp 的資深軟體工程師。</span><span class="sxs-lookup"><span data-stu-id="fae37-124">**[Taylor Southwick](https://github.com/twsouthwick)**, Senior Software Engineer, Microsoft Corp.</span></span>

> <span data-ttu-id="fae37-125">**[Scott Addie](https://github.com/scottaddie)**，Microsoft Corp 的資深內容開發人員。</span><span class="sxs-lookup"><span data-stu-id="fae37-125">**[Scott Addie](https://github.com/scottaddie)**, Senior Content Developer, Microsoft Corp.</span></span>

## <a name="introduction"></a><span data-ttu-id="fae37-126">簡介</span><span class="sxs-lookup"><span data-stu-id="fae37-126">Introduction</span></span>

<span data-ttu-id="fae37-127">.NET 透過 ASP.NET 提供長時間支援的 web 應用程式開發，這是一組完整的架構和工具，可用來建立任何類型的 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fae37-127">.NET has long supported web app development through ASP.NET, a comprehensive set of frameworks and tools for building any kind of web app.</span></span> <span data-ttu-id="fae37-128">ASP.NET 有自己的 web 架構和技術， (ASP) 的傳統 Active Server Pages 一併開始。</span><span class="sxs-lookup"><span data-stu-id="fae37-128">ASP.NET has its own lineage of web frameworks and technologies starting all the way back with classic Active Server Pages (ASP).</span></span> <span data-ttu-id="fae37-129">ASP.NET Web Forms、ASP.NET MVC、ASP.NET Web Pages 和最近 ASP.NET Core 的架構，可提供有效率且強大的方式來建立*伺服器呈現*的 Web 應用程式，其中 UI 內容是在伺服器上動態產生，以回應 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="fae37-129">Frameworks like ASP.NET Web Forms, ASP.NET MVC, ASP.NET Web Pages, and more recently ASP.NET Core, provide a productive and powerful way to build *server-rendered* web apps, where UI content is dynamically generated on the server in response to HTTP requests.</span></span> <span data-ttu-id="fae37-130">每個 ASP.NET 架構都會已經考慮到不同的物件和應用程式建立原理。</span><span class="sxs-lookup"><span data-stu-id="fae37-130">Each ASP.NET framework caters to a different audience and app building philosophy.</span></span> <span data-ttu-id="fae37-131">ASP.NET 原始版本 .NET Framework 隨附的 Web form，並使用桌面開發人員熟悉的許多模式來啟用 網頁程式開發，例如可重複使用的 UI 控制項與簡單的事件處理。</span><span class="sxs-lookup"><span data-stu-id="fae37-131">ASP.NET Web Forms shipped with the original release of the .NET Framework and enabled web development using many of the patterns familiar to desktop developers, like reusable UI controls with simple event handling.</span></span> <span data-ttu-id="fae37-132">不過，沒有任何 ASP.NET 供應專案會提供方法來執行在使用者的瀏覽器中執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="fae37-132">However, none of the ASP.NET offerings provide a way to run code that executed in the user's browser.</span></span> <span data-ttu-id="fae37-133">若要這麼做，需要撰寫 JavaScript，並使用多年來的任何 JavaScript 架構和工具： jQuery、挖式、角度、反應等等。</span><span class="sxs-lookup"><span data-stu-id="fae37-133">To do that requires writing JavaScript and using any of the many JavaScript frameworks and tools that have phased in and out of popularity over the years: jQuery, Knockout, Angular, React, and so on.</span></span>

<span data-ttu-id="fae37-134">[Blazor](https://blazor.net)是新的 web 架構，可變更使用 .NET 建立 web 應用程式時可能發生的情況。</span><span class="sxs-lookup"><span data-stu-id="fae37-134">[Blazor](https://blazor.net) is a new web framework that changes what is possible when building web apps with .NET.</span></span> Blazor<span data-ttu-id="fae37-135">是以 c # 為基礎的用戶端 web UI 架構，而不是 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="fae37-135"> is a client-side web UI framework based on C# instead of JavaScript.</span></span> <span data-ttu-id="fae37-136">Blazor您可以使用 c # 撰寫用戶端邏輯和 UI 元件，將它們編譯成一般的 .net 元件，然後使用名為的新開放式 web 標準，直接在瀏覽器中執行它們 WebAssembly 。</span><span class="sxs-lookup"><span data-stu-id="fae37-136">With Blazor you can write your client-side logic and UI components in C#, compile them into normal .NET assemblies, and then run them directly in the browser using a new open web standard called WebAssembly.</span></span> <span data-ttu-id="fae37-137">或者，也 Blazor 可以在伺服器上執行 .NET UI 元件，並處理與瀏覽器的即時連接流暢地的所有 UI 互動。</span><span class="sxs-lookup"><span data-stu-id="fae37-137">Or alternatively, Blazor can run your .NET UI components on the server and handle all UI interactions fluidly over a real-time connection with the browser.</span></span> <span data-ttu-id="fae37-138">當與伺服器上執行的 .NET 配對時，會 Blazor 啟用 .net 的完整堆疊 網頁程式開發。</span><span class="sxs-lookup"><span data-stu-id="fae37-138">When paired with .NET running on the server, Blazor enables full-stack web development with .NET.</span></span> <span data-ttu-id="fae37-139">雖然 Blazor 與 ASP.NET Web form 共用許多共通性，例如擁有可重複使用的元件模型，以及處理使用者事件的簡單方法，但它也是以 .Net Core 的基礎為基礎，以提供現代化且高效能的 Web 開發體驗。</span><span class="sxs-lookup"><span data-stu-id="fae37-139">While Blazor shares many commonalities with ASP.NET Web Forms, like having a reusable component model and a simple way to handle user events, it also builds on the foundations of .NET Core to provide a modern and high performance web development experience.</span></span>

<span data-ttu-id="fae37-140">本書以熟悉且方便的方式，介紹 ASP.NET Web Forms 開發人員 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="fae37-140">This book introduces ASP.NET Web Forms developers to Blazor in a way that is familiar and convenient.</span></span> <span data-ttu-id="fae37-141">它會以 Blazor ASP.NET Web form 中的類似概念平行引進概念，同時說明可能較不熟悉的新概念。</span><span class="sxs-lookup"><span data-stu-id="fae37-141">It introduces Blazor concepts in parallel with analogous concepts in ASP.NET Web Forms while also explaining new concepts that may be less familiar.</span></span> <span data-ttu-id="fae37-142">其中涵蓋了各種主題和疑慮，包括元件撰寫、路由、版面配置、設定和安全性。</span><span class="sxs-lookup"><span data-stu-id="fae37-142">It covers a broad range of topics and concerns including component authoring, routing, layout, configuration, and security.</span></span> <span data-ttu-id="fae37-143">雖然本書的內容主要是用來啟用新的開發，但它也涵蓋了 Blazor 當您想要將現有的應用程式現代化時，將現有的 ASP.NET Web form 遷移至的指導方針和策略。</span><span class="sxs-lookup"><span data-stu-id="fae37-143">And while the content of this book is primarily for enabling new development, it also covers guidelines and strategies for migrating existing ASP.NET Web Forms to Blazor for when you want to modernize an existing app.</span></span>

## <a name="who-should-use-the-book"></a><span data-ttu-id="fae37-144">誰應該使用本書</span><span class="sxs-lookup"><span data-stu-id="fae37-144">Who should use the book</span></span>

<span data-ttu-id="fae37-145">本書適用于 ASP.NET Web form 開發人員，尋找與 Blazor 現有知識和技能相關的簡介。</span><span class="sxs-lookup"><span data-stu-id="fae37-145">This book is for ASP.NET Web Forms developers looking for an introduction to Blazor that relates to their existing knowledge and skills.</span></span> <span data-ttu-id="fae37-146">本書可以協助您快速開始使用新 Blazor 的專案，或是協助圖表現代化現有 ASP.NET Web Forms 應用程式的藍圖。</span><span class="sxs-lookup"><span data-stu-id="fae37-146">This book can help with quickly getting started on a new Blazor-based project or to help chart a roadmap for modernizing an existing ASP.NET Web Forms application.</span></span>

## <a name="how-to-use-the-book"></a><span data-ttu-id="fae37-147">如何使用本書</span><span class="sxs-lookup"><span data-stu-id="fae37-147">How to use the book</span></span>

<span data-ttu-id="fae37-148">本書的第一個部分涵蓋了什麼 Blazor ，並將它與 web 應用程式開發與 ASP.NET web form 做比較。</span><span class="sxs-lookup"><span data-stu-id="fae37-148">The first part of this book covers what Blazor is and compares it to web app development with ASP.NET Web Forms.</span></span> <span data-ttu-id="fae37-149">本書接著會討論各種不同的 Blazor 主題，並將每個 Blazor 概念與 ASP.NET Web form 中的對應概念產生關聯，或完整說明所有全新的概念。</span><span class="sxs-lookup"><span data-stu-id="fae37-149">The book then covers a variety of Blazor topics, chapter by chapter, and relates each Blazor concept to the corresponding concept in ASP.NET Web Forms, or explains fully any completely new concepts.</span></span> <span data-ttu-id="fae37-150">本書也會定期參考完整的範例應用程式，並在 ASP.NET Web form 中執行並 Blazor 示範 Blazor 功能，並提供從 ASP.NET Web form 遷移至的案例研究 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="fae37-150">The book also refers regularly to a complete sample app implemented in both ASP.NET Web Forms and Blazor to demonstrate Blazor features and to provide a case study for migrating from ASP.NET Web Forms to Blazor.</span></span> <span data-ttu-id="fae37-151">您可以在 GitHub 上找到範例應用程式的兩個 (ASP.NET Web Forms 和 Blazor 版本) 。 [GitHub](https://github.com/dotnet-architecture/eshoponblazor)</span><span class="sxs-lookup"><span data-stu-id="fae37-151">You can find both implementations of the sample app (ASP.NET Web Forms and Blazor versions) on [GitHub](https://github.com/dotnet-architecture/eshoponblazor).</span></span>

## <a name="what-this-book-doesnt-cover"></a><span data-ttu-id="fae37-152">本書未涵蓋的內容</span><span class="sxs-lookup"><span data-stu-id="fae37-152">What this book doesn't cover</span></span>

<span data-ttu-id="fae37-153">本書是的簡介，而 Blazor 不是完整的遷移指南。</span><span class="sxs-lookup"><span data-stu-id="fae37-153">This book is an introduction to Blazor, not a comprehensive migration guide.</span></span> <span data-ttu-id="fae37-154">雖然其中包含如何將專案從 ASP.NET Web form 遷移至的指引 Blazor ，但不會嘗試涵蓋每一種細微性和詳細資料。</span><span class="sxs-lookup"><span data-stu-id="fae37-154">While it does include guidance on how to approach migrating a project from ASP.NET Web Forms to Blazor, it does not attempt to cover every nuance and detail.</span></span> <span data-ttu-id="fae37-155">如需從 ASP.NET 遷移至 ASP.NET Core 的一般指引，請參閱 ASP.NET Core 檔中的[遷移指引](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/)。</span><span class="sxs-lookup"><span data-stu-id="fae37-155">For more general guidance on migrating from ASP.NET to ASP.NET Core, refer to the [migration guidance](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/) in the ASP.NET Core documentation.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="fae37-156">其他資源</span><span class="sxs-lookup"><span data-stu-id="fae37-156">Additional resources</span></span>

<span data-ttu-id="fae37-157">您可以在中找到官方首頁 Blazor 和檔 <https://blazor.net> 。</span><span class="sxs-lookup"><span data-stu-id="fae37-157">You can find the official Blazor home page and documentation at <https://blazor.net>.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="fae37-158">傳送您的意見反應</span><span class="sxs-lookup"><span data-stu-id="fae37-158">Send your feedback</span></span>

<span data-ttu-id="fae37-159">這本書與相關範例不斷演進，所以您的意見反應歡迎！</span><span class="sxs-lookup"><span data-stu-id="fae37-159">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="fae37-160">如果您有關于如何改進這本書的意見，請使用[GitHub 問題](https://github.com/dotnet/docs/issues)上任何網頁底部的 [意見反應] 區段。</span><span class="sxs-lookup"><span data-stu-id="fae37-160">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="fae37-161">下一步</span><span class="sxs-lookup"><span data-stu-id="fae37-161">Next</span></span>](introduction.md)
