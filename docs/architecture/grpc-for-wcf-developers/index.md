---
title: WCF 開發人員的 ASP.NET Core gRPC-WCF 開發人員的 gRPC
description: 在 WCF 開發人員的 ASP.NET Core 3.0 中建立 gRPC 服務的簡介
ms.date: 09/02/2019
ms.openlocfilehash: 3ef513d2397b6f282591dfe6c9b25cd178372a28
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967753"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="6cf19-103">適用於 WCF 開發人員的 ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="6cf19-103">ASP.NET Core gRPC for WCF Developers</span></span>

![封面影像](./media/cover.png)

<span data-ttu-id="6cf19-105">發行者</span><span class="sxs-lookup"><span data-stu-id="6cf19-105">PUBLISHED BY</span></span>

<span data-ttu-id="6cf19-106">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="6cf19-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="6cf19-107">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="6cf19-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="6cf19-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="6cf19-108">One Microsoft Way</span></span>

<span data-ttu-id="6cf19-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="6cf19-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="6cf19-110">Copyright © 2019 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="6cf19-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="6cf19-111">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="6cf19-111">All rights reserved.</span></span> <span data-ttu-id="6cf19-112">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="6cf19-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="6cf19-113">本書是以「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="6cf19-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="6cf19-114">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="6cf19-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="6cf19-115">此處所描述的一些範例僅供說明，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="6cf19-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="6cf19-116">任何實際關聯或連結純屬巧合。</span><span class="sxs-lookup"><span data-stu-id="6cf19-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="6cf19-117">Microsoft 與列於 https://www.microsoft.com 「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="6cf19-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="6cf19-118">Docker whale 標誌是 Docker，Inc. 的注冊商標，由許可權使用。</span><span class="sxs-lookup"><span data-stu-id="6cf19-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="6cf19-119">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="6cf19-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="6cf19-120">作者:</span><span class="sxs-lookup"><span data-stu-id="6cf19-120">Author:</span></span>

> <span data-ttu-id="6cf19-121">**Mark Rendle** -首席技術長-[視覺的編碼](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="6cf19-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="6cf19-122">**Miranda Steiner** -技術作者</span><span class="sxs-lookup"><span data-stu-id="6cf19-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="6cf19-123">編輯者：</span><span class="sxs-lookup"><span data-stu-id="6cf19-123">Editors:</span></span>

> <span data-ttu-id="6cf19-124">**Maira Wenzel** -Sr 內容開發人員-Microsoft</span><span class="sxs-lookup"><span data-stu-id="6cf19-124">**Maira Wenzel** - Sr Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="6cf19-125">簡介</span><span class="sxs-lookup"><span data-stu-id="6cf19-125">Introduction</span></span>

<span data-ttu-id="6cf19-126">gRPC 是一種現代化的架構，可用於建立網路服務和分散式應用程式。</span><span class="sxs-lookup"><span data-stu-id="6cf19-126">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="6cf19-127">想像一下 WCF 的 NetTCP 系結與 SOAP 的跨平臺互通性的效能。</span><span class="sxs-lookup"><span data-stu-id="6cf19-127">Imagine the performance of WCF's NetTCP bindings with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="6cf19-128">gRPC 是以 HTTP/2 和 Protobuf 訊息編碼通訊協定為基礎，可在應用程式與服務之間提供高效能、低頻寬的通訊。</span><span class="sxs-lookup"><span data-stu-id="6cf19-128">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="6cf19-129">它支援跨最受歡迎的程式設計語言和平臺（包括 .NET、JAVA、Python、node.js、Go 等等） C++產生伺服器和用戶端程式代碼。</span><span class="sxs-lookup"><span data-stu-id="6cf19-129">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, C++ and more.</span></span> <span data-ttu-id="6cf19-130">有了 ASP.NET Core 3.0 中 gRPC 的第一級支援，除了適用于 .NET 4.x 的現有 gRPC 工具和程式庫之外，我們也認為它是 WCF 的絕佳替代方案，適用于想要在組織中採用 .NET Core 的開發團隊。</span><span class="sxs-lookup"><span data-stu-id="6cf19-130">With the first-class support for gRPC in ASP.NET Core 3.0, alongside the existing gRPC tools and libraries for .NET 4.x, we think it is an excellent alternative to WCF for development teams looking to adopt .NET Core in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="6cf19-131">誰應該使用本指南</span><span class="sxs-lookup"><span data-stu-id="6cf19-131">Who should use this guide</span></span>

<span data-ttu-id="6cf19-132">本指南是針對在先前已使用 WCF 的 .NET Framework 或 .NET Core 中工作的開發人員所撰寫，而且想要將其應用程式遷移至 .NET Core 3.0 和更新版本的新式 RPC 環境。</span><span class="sxs-lookup"><span data-stu-id="6cf19-132">This guide was written for developers working in .NET Framework or .NET Core who have previously used WCF and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="6cf19-133">本指南也可能更普遍用於升級或考慮升級至想要使用內建 gRPC 工具的 .NET Core 3.0 的開發人員。</span><span class="sxs-lookup"><span data-stu-id="6cf19-133">The guide may also be of use more generally for developers upgrading or considering upgrading to .NET Core 3.0 who want to use the built-in gRPC tools.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="6cf19-134">此指南的使用方式</span><span class="sxs-lookup"><span data-stu-id="6cf19-134">How you can use this guide</span></span>

<span data-ttu-id="6cf19-135">這是在 ASP.NET Core 3.0 中建立 gRPC 服務的簡要介紹，並特別參考 WCF 做為類似的平臺。</span><span class="sxs-lookup"><span data-stu-id="6cf19-135">This is a short introduction to building gRPC Services in ASP.NET Core 3.0 with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="6cf19-136">其中說明 gRPC 的原則，並將每個概念關聯至 WCF 的對等功能，並提供將現有 WCF 應用程式遷移至 gRPC 的指引。</span><span class="sxs-lookup"><span data-stu-id="6cf19-136">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="6cf19-137">對於有 WCF 經驗，而且想要學習 gRPC 以建立新服務的開發人員而言，這也很有用。</span><span class="sxs-lookup"><span data-stu-id="6cf19-137">It is also useful for developers who have experience of WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="6cf19-138">範例應用程式可用來作為您自己專案的範本或參考，而且您可以免費複製並重複使用本書或其範例中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6cf19-138">The sample applications can be used as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="6cf19-139">請隨意將本指南轉寄給您的小組，協助確保對這些考量和機會有共同的了解。</span><span class="sxs-lookup"><span data-stu-id="6cf19-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="6cf19-140">讓所有人都使用一組共用術語和基礎原則，有助確保套用一致的架構模式和做法。</span><span class="sxs-lookup"><span data-stu-id="6cf19-140">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="6cf19-141">reference</span><span class="sxs-lookup"><span data-stu-id="6cf19-141">References</span></span>

- <span data-ttu-id="6cf19-142">**gRPC 網站**</span><span class="sxs-lookup"><span data-stu-id="6cf19-142">**gRPC web site**</span></span>  
  <https://grpc.io>
- <span data-ttu-id="6cf19-143">**針對伺服器應用程式在 .NET Core 和 .NET Framework 之間進行選擇**</span><span class="sxs-lookup"><span data-stu-id="6cf19-143">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[<span data-ttu-id="6cf19-144">下一步</span><span class="sxs-lookup"><span data-stu-id="6cf19-144">Next</span></span>](introduction.md)
