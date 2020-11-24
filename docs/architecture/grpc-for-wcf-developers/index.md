---
title: 適用于 WCF 開發人員的 ASP.NET Core gRPC-適用于 WCF 開發人員的 gRPC
description: 在 ASP.NET Core 3.0 中為 WCF 開發人員建立 gRPC 服務的簡介
ms.date: 09/02/2019
ms.openlocfilehash: c9cc5ef9c06d5262fb85850f8a3b178d46e5c6fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689273"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="79cb6-103">適用於 WCF 開發人員的 ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="79cb6-103">ASP.NET Core gRPC for WCF Developers</span></span>

![封面影像](./media/cover.png)

<span data-ttu-id="79cb6-105">發行者</span><span class="sxs-lookup"><span data-stu-id="79cb6-105">PUBLISHED BY</span></span>

<span data-ttu-id="79cb6-106">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="79cb6-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="79cb6-107">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="79cb6-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="79cb6-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="79cb6-108">One Microsoft Way</span></span>

<span data-ttu-id="79cb6-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="79cb6-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="79cb6-110">Copyright © 2019 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="79cb6-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="79cb6-111">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="79cb6-111">All rights reserved.</span></span> <span data-ttu-id="79cb6-112">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="79cb6-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="79cb6-113">本書依照「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="79cb6-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="79cb6-114">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="79cb6-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="79cb6-115">此處描述的一些範例僅供說明之用，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="79cb6-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="79cb6-116">並未影射或關聯任何真實的人、事、物。</span><span class="sxs-lookup"><span data-stu-id="79cb6-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="79cb6-117">Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="79cb6-117">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="79cb6-118">Docker whale 標誌是 Docker，Inc. 所用的注冊商標。</span><span class="sxs-lookup"><span data-stu-id="79cb6-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="79cb6-119">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="79cb6-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="79cb6-120">作者：</span><span class="sxs-lookup"><span data-stu-id="79cb6-120">Authors:</span></span>

> <span data-ttu-id="79cb6-121">**Mark Rendle** -首席技術長- [視覺編碼](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="79cb6-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="79cb6-122">**Miranda Steiner** -技術作者</span><span class="sxs-lookup"><span data-stu-id="79cb6-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="79cb6-123">編輯器：</span><span class="sxs-lookup"><span data-stu-id="79cb6-123">Editor:</span></span>

> <span data-ttu-id="79cb6-124">**Maira Wenzel** -資深內容開發人員-Microsoft</span><span class="sxs-lookup"><span data-stu-id="79cb6-124">**Maira Wenzel** - Sr. Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="79cb6-125">簡介</span><span class="sxs-lookup"><span data-stu-id="79cb6-125">Introduction</span></span>

<span data-ttu-id="79cb6-126">gRPC 是一種現代化的架構，可用於建立網路服務和分散式應用程式。</span><span class="sxs-lookup"><span data-stu-id="79cb6-126">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="79cb6-127">想像 Windows Communication Foundation (WCF) NetTCP 系結的效能，並結合 SOAP 的跨平臺互通性。</span><span class="sxs-lookup"><span data-stu-id="79cb6-127">Imagine the performance of Windows Communication Foundation (WCF) NetTCP bindings, combined with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="79cb6-128">gRPC 建基於 HTTP/2 和 Protobuf 訊息編碼通訊協定，以提供應用程式與服務之間的高效能、低頻寬通訊。</span><span class="sxs-lookup"><span data-stu-id="79cb6-128">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="79cb6-129">它支援跨最受歡迎的程式設計語言和平臺產生伺服器和用戶端程式代碼，包括 .NET、JAVA、Python、Node.js、Go 和 c + +。</span><span class="sxs-lookup"><span data-stu-id="79cb6-129">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, and C++.</span></span> <span data-ttu-id="79cb6-130">使用 ASP.NET Core 3.0 中 gRPC 的第一層級支援，以及適用于 .NET Framework 4.x 的現有 gRPC 工具和程式庫，這是 WCF 的絕佳替代方案，適用于想要在組織中採用 .NET Core 的開發團隊。</span><span class="sxs-lookup"><span data-stu-id="79cb6-130">With the first-class support for gRPC in ASP.NET Core 3.0, alongside the existing gRPC tools and libraries for .NET Framework 4.x, it's an excellent alternative to WCF for development teams looking to adopt .NET Core in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="79cb6-131">誰應該使用本指南</span><span class="sxs-lookup"><span data-stu-id="79cb6-131">Who should use this guide</span></span>

<span data-ttu-id="79cb6-132">本指南是針對在先前使用 WCF 的 .NET Framework 或 .NET Core 中工作的開發人員，以及想要將其應用程式遷移至 .NET Core 3.0 和更新版本之新式 RPC 環境的開發人員所撰寫。</span><span class="sxs-lookup"><span data-stu-id="79cb6-132">This guide was written for developers working in .NET Framework or .NET Core who have previously used WCF, and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="79cb6-133">更常見的是，如果您要升級或考慮升級到 .NET Core 3.0，而且您想要使用內建的 gRPC 工具，本指南也很有用。</span><span class="sxs-lookup"><span data-stu-id="79cb6-133">More generally, if you are upgrading, or considering upgrading, to .NET Core 3.0, and you want to use the built-in gRPC tools, this guide is also useful.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="79cb6-134">此指南的使用方式</span><span class="sxs-lookup"><span data-stu-id="79cb6-134">How you can use this guide</span></span>

<span data-ttu-id="79cb6-135">這是在 ASP.NET Core 3.0 中建立 gRPC 服務的簡短簡介，並且將 WCF 的特定參考視為類似的平臺。</span><span class="sxs-lookup"><span data-stu-id="79cb6-135">This is a short introduction to building gRPC Services in ASP.NET Core 3.0, with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="79cb6-136">它會說明 gRPC 的原則，並將每個概念與 WCF 的對等功能產生關聯，並提供將現有 WCF 應用程式遷移至 gRPC 的指引。</span><span class="sxs-lookup"><span data-stu-id="79cb6-136">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="79cb6-137">它也適用于具有 WCF 經驗的開發人員，而且想要學習 gRPC 來建立新的服務。</span><span class="sxs-lookup"><span data-stu-id="79cb6-137">It's also useful for developers who have experience with WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="79cb6-138">您可以使用範例應用程式做為您自己的專案的範本或參考，也可以自由地複製和重複使用書籍中的程式碼或其範例。</span><span class="sxs-lookup"><span data-stu-id="79cb6-138">You can use the sample applications as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="79cb6-139">請隨意將本指南轉寄給您的小組，協助確保對這些考量和機會有共同的了解。</span><span class="sxs-lookup"><span data-stu-id="79cb6-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="79cb6-140">讓每個人都能從一組常見的條款和基礎原則中工作，有助於確保架構模式和實務的一致應用。</span><span class="sxs-lookup"><span data-stu-id="79cb6-140">Having everybody working from a common set of terms and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="79cb6-141">參考資料</span><span class="sxs-lookup"><span data-stu-id="79cb6-141">References</span></span>

- <span data-ttu-id="79cb6-142">**gRPC 網站**
  <https://grpc.io></span><span class="sxs-lookup"><span data-stu-id="79cb6-142">**gRPC website**
<https://grpc.io></span></span>
- <span data-ttu-id="79cb6-143">**針對伺服器應用程式在 .NET Core 和 .NET Framework 之間進行選擇**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="79cb6-143">**Choosing between .NET Core and .NET Framework for server apps**
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="79cb6-144">下一步</span><span class="sxs-lookup"><span data-stu-id="79cb6-144">Next</span></span>](introduction.md)
