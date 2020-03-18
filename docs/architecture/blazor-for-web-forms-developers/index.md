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
# <a name="blazor-for-aspnet-web-forms-developers"></a><span data-ttu-id="9b535-103">適用於 ASP.NET Web Forms 的 Blazor 開發人員</span><span class="sxs-lookup"><span data-stu-id="9b535-103">Blazor for ASP.NET Web Forms Developers</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![顯示無伺服器應用電子書封面的螢幕截圖。](./media/index/blazor-for-web-forms-developers-cover.png)

> <span data-ttu-id="9b535-105">下載：<https://aka.ms/blazor-ebook></span><span class="sxs-lookup"><span data-stu-id="9b535-105">DOWNLOAD available at: <https://aka.ms/blazor-ebook></span></span>

<span data-ttu-id="9b535-106">發行者</span><span class="sxs-lookup"><span data-stu-id="9b535-106">PUBLISHED BY</span></span>

<span data-ttu-id="9b535-107">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="9b535-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="9b535-108">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="9b535-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="9b535-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="9b535-109">One Microsoft Way</span></span>

<span data-ttu-id="9b535-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="9b535-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="9b535-111">Copyright © 2019 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="9b535-111">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="9b535-112">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="9b535-112">All rights reserved.</span></span> <span data-ttu-id="9b535-113">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="9b535-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="9b535-114">本書依照「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="9b535-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="9b535-115">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="9b535-115">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="9b535-116">此處描述的一些範例僅供說明之用，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="9b535-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="9b535-117">並未影射或關聯任何真實的人、事、物。</span><span class="sxs-lookup"><span data-stu-id="9b535-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="9b535-118">Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="9b535-118">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="9b535-119">Mac 與 macOS 是 Apple Inc. 的商標。</span><span class="sxs-lookup"><span data-stu-id="9b535-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="9b535-120">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="9b535-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="9b535-121">作者：</span><span class="sxs-lookup"><span data-stu-id="9b535-121">Authors:</span></span>

> <span data-ttu-id="9b535-122">**[丹尼爾·羅斯](https://github.com/danroth27)**，微軟公司首席專案經理</span><span class="sxs-lookup"><span data-stu-id="9b535-122">**[Daniel Roth](https://github.com/danroth27)**, Principal Program Manager, Microsoft Corp.</span></span>

> <span data-ttu-id="9b535-123">**[傑夫·弗裡茨](https://github.com/csharpfritz)**，微軟公司高級專案經理。</span><span class="sxs-lookup"><span data-stu-id="9b535-123">**[Jeff Fritz](https://github.com/csharpfritz)**, Senior Program Manager, Microsoft Corp.</span></span>

> <span data-ttu-id="9b535-124">**[泰勒·南威克](https://github.com/twsouthwick)**，微軟公司高級軟體工程師。</span><span class="sxs-lookup"><span data-stu-id="9b535-124">**[Taylor Southwick](https://github.com/twsouthwick)**, Senior Software Engineer, Microsoft Corp.</span></span>

> <span data-ttu-id="9b535-125">**[斯科特·艾迪](https://github.com/scottaddie)**，微軟公司高級內容開發者。</span><span class="sxs-lookup"><span data-stu-id="9b535-125">**[Scott Addie](https://github.com/scottaddie)**, Senior Content Developer, Microsoft Corp.</span></span>

## <a name="introduction"></a><span data-ttu-id="9b535-126">簡介</span><span class="sxs-lookup"><span data-stu-id="9b535-126">Introduction</span></span>

<span data-ttu-id="9b535-127">.NET 長期以來一直通過ASP.NET支援 Web 應用開發，這是一套用於構建任何類型的 Web 應用的全套框架和工具。</span><span class="sxs-lookup"><span data-stu-id="9b535-127">.NET has long supported web app development through ASP.NET, a comprehensive set of frameworks and tools for building any kind of web app.</span></span> <span data-ttu-id="9b535-128">ASP.NET有自己的 Web 框架和技術的血統，從經典活動伺服器頁面 （ASP） 開始。</span><span class="sxs-lookup"><span data-stu-id="9b535-128">ASP.NET has its own lineage of web frameworks and technologies starting all the way back with classic Active Server Pages (ASP).</span></span> <span data-ttu-id="9b535-129">ASP.NET Web 表單、ASP.NET MVC、ASP.NET 網頁以及最近ASP.NET Core 等框架提供了一種高效且強大的方法來構建*伺服器呈現的*Web 應用，其中 UI 內容在伺服器上動態生成以回應 HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="9b535-129">Frameworks like ASP.NET Web Forms, ASP.NET MVC, ASP.NET Web Pages, and more recently ASP.NET Core, provide a productive and powerful way to build *server-rendered* web apps, where UI content is dynamically generated on the server in response to HTTP requests.</span></span> <span data-ttu-id="9b535-130">每個ASP.NET框架都迎合了不同的受眾和應用構建理念。</span><span class="sxs-lookup"><span data-stu-id="9b535-130">Each ASP.NET framework caters to a different audience and app building philosophy.</span></span> <span data-ttu-id="9b535-131">ASP.NET Web 表單隨 .NET Framework 的原始版本一起提供，並使用桌面開發人員熟悉的許多模式啟用 Web 開發，例如具有簡單事件處理的可重用 UI 控制項。</span><span class="sxs-lookup"><span data-stu-id="9b535-131">ASP.NET Web Forms shipped with the original release of the .NET Framework and enabled web development using many of the patterns familiar to desktop developers, like reusable UI controls with simple event handling.</span></span> <span data-ttu-id="9b535-132">但是，ASP.NET產品都無法提供運行在使用者瀏覽器中執行的代碼的方法。</span><span class="sxs-lookup"><span data-stu-id="9b535-132">However, none of the ASP.NET offerings provide a way to run code that executed in the user's browser.</span></span> <span data-ttu-id="9b535-133">為此，需要編寫 JavaScript 並使用多年來逐漸流行和逐漸普及的許多 JavaScript 框架和工具中的任何一個：jQuery、挖空、角、反應等。</span><span class="sxs-lookup"><span data-stu-id="9b535-133">To do that requires writing JavaScript and using any of the many JavaScript frameworks and tools that have phased in and out of popularity over the years: jQuery, Knockout, Angular, React, and so on.</span></span>

<span data-ttu-id="9b535-134">[Blazor](https://blazor.net)是一個新的 Web 框架，它改變了使用 .NET 構建 Web 應用時可能實現的內容。</span><span class="sxs-lookup"><span data-stu-id="9b535-134">[Blazor](https://blazor.net) is a new web framework that changes what is possible when building web apps with .NET.</span></span> <span data-ttu-id="9b535-135">Blazor 是基於 C# 而不是 JavaScript 的用戶端 Web UI 框架。</span><span class="sxs-lookup"><span data-stu-id="9b535-135">Blazor is a client-side web UI framework based on C# instead of JavaScript.</span></span> <span data-ttu-id="9b535-136">使用 Blazor，您可以在 C# 中編寫用戶端邏輯和 UI 元件，將它們編譯為正常的 .NET 程式集，然後使用稱為 WebAssembly 的新開放 Web 標準直接在瀏覽器中運行它們。</span><span class="sxs-lookup"><span data-stu-id="9b535-136">With Blazor you can write your client-side logic and UI components in C#, compile them into normal .NET assemblies, and then run them directly in the browser using a new open web standard called WebAssembly.</span></span> <span data-ttu-id="9b535-137">或者，Blazor 可以在伺服器上運行 .NET UI 元件，並在與瀏覽器的即時連接中流暢地處理所有 UI 交互。</span><span class="sxs-lookup"><span data-stu-id="9b535-137">Or alternatively, Blazor can run your .NET UI components on the server and handle all UI interactions fluidly over a real-time connection with the browser.</span></span> <span data-ttu-id="9b535-138">與在伺服器上運行的 .NET 配對時，Blazor 支援使用 .NET 進行全堆疊 Web 開發。</span><span class="sxs-lookup"><span data-stu-id="9b535-138">When paired with .NET running on the server, Blazor enables full-stack web development with .NET.</span></span> <span data-ttu-id="9b535-139">雖然 Blazor 與 ASP.NET Web 表單有許多共同點，例如具有可重用的元件模型和處理使用者事件的簡單方法，但它也建立在 .NET Core 的基礎上，以提供現代和高性能的 Web 開發體驗。</span><span class="sxs-lookup"><span data-stu-id="9b535-139">While Blazor shares many commonalities with ASP.NET Web Forms, like having a reusable component model and a simple way to handle user events, it also builds on the foundations of .NET Core to provide a modern and high performance web development experience.</span></span>

<span data-ttu-id="9b535-140">本書以熟悉和方便的方式向布拉佐介紹了ASP.NET Web 表單開發人員。</span><span class="sxs-lookup"><span data-stu-id="9b535-140">This book introduces ASP.NET Web Forms developers to Blazor in a way that is familiar and convenient.</span></span> <span data-ttu-id="9b535-141">它引入了 Blazor 概念，與ASP.NET Web 表單中的類似概念並行，同時解釋可能不太熟悉的新概念。</span><span class="sxs-lookup"><span data-stu-id="9b535-141">It introduces Blazor concepts in parallel with analogous concepts in ASP.NET Web Forms while also explaining new concepts that may be less familiar.</span></span> <span data-ttu-id="9b535-142">它涵蓋廣泛的主題和問題，包括元件創作、路由、佈局、配置和安全性。</span><span class="sxs-lookup"><span data-stu-id="9b535-142">It covers a broad range of topics and concerns including component authoring, routing, layout, configuration, and security.</span></span> <span data-ttu-id="9b535-143">雖然本書的內容主要是為了啟用新的開發，但它也涵蓋了將現有ASP.NET Web 表單遷移到 Blazor 的指南和策略，以便您更新現有應用。</span><span class="sxs-lookup"><span data-stu-id="9b535-143">And while the content of this book is primarily for enabling new development, it also covers guidelines and strategies for migrating existing ASP.NET Web Forms to Blazor for when you want to modernize an existing app.</span></span>

## <a name="who-should-use-the-book"></a><span data-ttu-id="9b535-144">誰應該用這本書</span><span class="sxs-lookup"><span data-stu-id="9b535-144">Who should use the book</span></span>

<span data-ttu-id="9b535-145">本書面向ASP.NET Web 表單開發人員，他們正在尋找有關他們現有知識和技能的 Blazor 簡介。</span><span class="sxs-lookup"><span data-stu-id="9b535-145">This book is for ASP.NET Web Forms developers looking for an introduction to Blazor that relates to their existing knowledge and skills.</span></span> <span data-ttu-id="9b535-146">本書可以説明快速啟動基於 Blazor 的新專案，或者説明繪製現有ASP.NET Web 表單應用程式現代化的路線圖。</span><span class="sxs-lookup"><span data-stu-id="9b535-146">This book can help with quickly getting started on a new Blazor-based project or to help chart a roadmap for modernizing an existing ASP.NET Web Forms application.</span></span>

## <a name="how-to-use-the-book"></a><span data-ttu-id="9b535-147">如何使用這本書</span><span class="sxs-lookup"><span data-stu-id="9b535-147">How to use the book</span></span>

<span data-ttu-id="9b535-148">本書的第一部分介紹了 Blazor 的內容，並將其與 Web 應用開發與 ASP.NET Web 表單進行比較。</span><span class="sxs-lookup"><span data-stu-id="9b535-148">The first part of this book covers what Blazor is and compares it to web app development with ASP.NET Web Forms.</span></span> <span data-ttu-id="9b535-149">然後，這本書涵蓋了各種布拉佐爾主題，逐章，並將每個Blazor概念與ASP.NET Web 表單中的相應概念相關聯，或全面解釋任何全新的概念。</span><span class="sxs-lookup"><span data-stu-id="9b535-149">The book then covers a variety of Blazor topics, chapter by chapter, and relates each Blazor concept to the corresponding concept in ASP.NET Web Forms, or explains fully any completely new concepts.</span></span> <span data-ttu-id="9b535-150">本書還定期提及在ASP.NET Web 表單和 Blazor 中實現的完整示例應用，以演示 Blazor 功能，並提供從ASP.NET Web 表單遷移到 Blazor 的案例研究。</span><span class="sxs-lookup"><span data-stu-id="9b535-150">The book also refers regularly to a complete sample app implemented in both ASP.NET Web Forms and Blazor to demonstrate Blazor features and to provide a case study for migrating from ASP.NET Web Forms to Blazor.</span></span> <span data-ttu-id="9b535-151">您可以在[GitHub](https://github.com/dotnet-architecture/eshoponblazor)上找到示例應用（ASP.NET Web 表單和 Blazor 版本）的兩個實現。</span><span class="sxs-lookup"><span data-stu-id="9b535-151">You can find both implementations of the sample app (ASP.NET Web Forms and Blazor versions) on [GitHub](https://github.com/dotnet-architecture/eshoponblazor).</span></span>

## <a name="what-this-book-doesnt-cover"></a><span data-ttu-id="9b535-152">這本書沒有涵蓋什麼</span><span class="sxs-lookup"><span data-stu-id="9b535-152">What this book doesn't cover</span></span>

<span data-ttu-id="9b535-153">這本書是布拉佐爾的介紹，而不是全面的遷移指南。</span><span class="sxs-lookup"><span data-stu-id="9b535-153">This book is an introduction to Blazor, not a comprehensive migration guide.</span></span> <span data-ttu-id="9b535-154">雖然它包括有關如何處理從ASP.NET Web 表單遷移到 Blazor 的專案的指導，但它並不試圖涵蓋所有細微差別和細節。</span><span class="sxs-lookup"><span data-stu-id="9b535-154">While it does include guidance on how to approach migrating a project from ASP.NET Web Forms to Blazor, it does not attempt to cover every nuance and detail.</span></span> <span data-ttu-id="9b535-155">有關從ASP.NET遷移到 ASP.NET 核心的更多一般指南，請參閱 ASP.NET 核心文檔中的[遷移指南](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/)。</span><span class="sxs-lookup"><span data-stu-id="9b535-155">For more general guidance on migrating from ASP.NET to ASP.NET Core, refer to the [migration guidance](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/) in the ASP.NET Core documentation.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9b535-156">其他資源</span><span class="sxs-lookup"><span data-stu-id="9b535-156">Additional resources</span></span>

<span data-ttu-id="9b535-157">您可以在 找到官方布拉佐主頁和文檔在<https://blazor.net>。</span><span class="sxs-lookup"><span data-stu-id="9b535-157">You can find the official Blazor home page and documentation at <https://blazor.net>.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="9b535-158">傳送您的意見反應</span><span class="sxs-lookup"><span data-stu-id="9b535-158">Send your feedback</span></span>

<span data-ttu-id="9b535-159">本書和相關示例不斷演變，因此歡迎您的回饋！</span><span class="sxs-lookup"><span data-stu-id="9b535-159">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="9b535-160">如果您對如何改進本書有意見，請使用基於[GitHub 問題](https://github.com/dotnet/docs/issues)構建的任何頁面底部的回饋部分。</span><span class="sxs-lookup"><span data-stu-id="9b535-160">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="9b535-161">下一步</span><span class="sxs-lookup"><span data-stu-id="9b535-161">Next</span></span>](introduction.md)
