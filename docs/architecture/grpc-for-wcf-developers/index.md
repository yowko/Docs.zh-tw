---
title: ASP.NET面向 WCF 開發人員的核心 gRPC - gRPC 面向 WCF 開發人員
description: 為 WCF 開發人員ASP.NET核心 3.0 構建 gRPC 服務簡介
ms.date: 09/02/2019
ms.openlocfilehash: 40307124c521659a00339884bacf48881fa3e048
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543231"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="44fe4-103">適用於 WCF 開發人員的 ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="44fe4-103">ASP.NET Core gRPC for WCF Developers</span></span>

![封面影像](./media/cover.png)

<span data-ttu-id="44fe4-105">發行者</span><span class="sxs-lookup"><span data-stu-id="44fe4-105">PUBLISHED BY</span></span>

<span data-ttu-id="44fe4-106">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="44fe4-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="44fe4-107">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="44fe4-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="44fe4-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="44fe4-108">One Microsoft Way</span></span>

<span data-ttu-id="44fe4-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="44fe4-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="44fe4-110">Copyright © 2019 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="44fe4-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="44fe4-111">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="44fe4-111">All rights reserved.</span></span> <span data-ttu-id="44fe4-112">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="44fe4-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="44fe4-113">本書是以「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="44fe4-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="44fe4-114">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="44fe4-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="44fe4-115">此處描述的一些範例僅供說明之用，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="44fe4-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="44fe4-116">並未影射或關聯任何真實的人、事、物。</span><span class="sxs-lookup"><span data-stu-id="44fe4-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="44fe4-117">Microsoft 與列於 https://www.microsoft.com「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="44fe4-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="44fe4-118">Docker 鯨魚標誌是 Docker， Inc. 經許可使用的注冊商標。</span><span class="sxs-lookup"><span data-stu-id="44fe4-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="44fe4-119">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="44fe4-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="44fe4-120">作者：</span><span class="sxs-lookup"><span data-stu-id="44fe4-120">Authors:</span></span>

> <span data-ttu-id="44fe4-121">**馬克·倫德爾**- 首席技術官 -[視覺重碼](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="44fe4-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="44fe4-122">**米蘭達·施泰納**- 技術作者</span><span class="sxs-lookup"><span data-stu-id="44fe4-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="44fe4-123">編輯器：</span><span class="sxs-lookup"><span data-stu-id="44fe4-123">Editor:</span></span>

> <span data-ttu-id="44fe4-124">**Maira Wenzel** - Sr. 內容開發人員 - 微軟</span><span class="sxs-lookup"><span data-stu-id="44fe4-124">**Maira Wenzel** - Sr. Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="44fe4-125">簡介</span><span class="sxs-lookup"><span data-stu-id="44fe4-125">Introduction</span></span>

<span data-ttu-id="44fe4-126">gRPC 是構建網路服務和分散式應用程式的現代框架。</span><span class="sxs-lookup"><span data-stu-id="44fe4-126">gRPC is a modern framework for building networked services and distributed applications.</span></span> <span data-ttu-id="44fe4-127">想像一下 Windows 通信基礎 （WCF） NetTCP 綁定的性能，以及 SOAP 的跨平臺互通性。</span><span class="sxs-lookup"><span data-stu-id="44fe4-127">Imagine the performance of Windows Communication Foundation (WCF) NetTCP bindings, combined with the cross-platform interoperability of SOAP.</span></span> <span data-ttu-id="44fe4-128">gRPC 基於 HTTP/2 和 Protobuf 消息編碼協議構建，以便在應用程式和服務之間提供高性能、低頻寬的通信。</span><span class="sxs-lookup"><span data-stu-id="44fe4-128">gRPC builds on HTTP/2 and the Protobuf message-encoding protocol to provide high performance, low-bandwidth communication between applications and services.</span></span> <span data-ttu-id="44fe4-129">它支援在最流行的程式設計語言和平臺上生成伺服器和用戶端代碼，包括 .NET、JAVA、Python、Node.js、Go 和C++。</span><span class="sxs-lookup"><span data-stu-id="44fe4-129">It supports server and client code generation across most popular programming languages and platforms, including .NET, Java, Python, Node.js, Go, and C++.</span></span> <span data-ttu-id="44fe4-130">ASP.NET Core 3.0 中對 gRPC 的一流支援，以及現有的 gRPC 工具和 .NET 4.x 的庫，對於希望在其組織中採用 .NET Core 的開發團隊而言，它是 WCF 的絕佳替代方案。</span><span class="sxs-lookup"><span data-stu-id="44fe4-130">With the first-class support for gRPC in ASP.NET Core 3.0, alongside the existing gRPC tools and libraries for .NET 4.x, it's an excellent alternative to WCF for development teams looking to adopt .NET Core in their organizations.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="44fe4-131">誰應該使用本指南</span><span class="sxs-lookup"><span data-stu-id="44fe4-131">Who should use this guide</span></span>

<span data-ttu-id="44fe4-132">本指南是為以前使用過 WCF 的 .NET 框架或 .NET Core 工作的開發人員編寫的，這些開發人員尋求將其應用程式遷移到用於 .NET Core 3.0 和更高版本的現代 RPC 環境。</span><span class="sxs-lookup"><span data-stu-id="44fe4-132">This guide was written for developers working in .NET Framework or .NET Core who have previously used WCF, and who are seeking to migrate their applications to a modern RPC environment for .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="44fe4-133">更一般地說，如果要升級到 .NET Core 3.0，並且想要使用內置 gRPC 工具，本指南也很有用。</span><span class="sxs-lookup"><span data-stu-id="44fe4-133">More generally, if you are upgrading, or considering upgrading, to .NET Core 3.0, and you want to use the built-in gRPC tools, this guide is also useful.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="44fe4-134">此指南的使用方式</span><span class="sxs-lookup"><span data-stu-id="44fe4-134">How you can use this guide</span></span>

<span data-ttu-id="44fe4-135">這是ASP.NET核心3.0中構建 gRPC 服務的簡短介紹，其中特別提到 WCF 作為類似平臺。</span><span class="sxs-lookup"><span data-stu-id="44fe4-135">This is a short introduction to building gRPC Services in ASP.NET Core 3.0, with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="44fe4-136">它解釋了 gRPC 的原則，將每個概念與 WCF 的等效功能相關聯，並為將現有的 WCF 應用程式遷移到 gRPC 提供了指導。</span><span class="sxs-lookup"><span data-stu-id="44fe4-136">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="44fe4-137">對於具有 WCF 經驗並希望學習 gRPC 以構建新服務的開發人員來說，它也很有用。</span><span class="sxs-lookup"><span data-stu-id="44fe4-137">It's also useful for developers who have experience with WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="44fe4-138">您可以將應用程式範例用作您自己的專案的範本或參考，並且可以自由地複製和重用書籍或其示例中的代碼。</span><span class="sxs-lookup"><span data-stu-id="44fe4-138">You can use the sample applications as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="44fe4-139">請隨意將本指南轉寄給您的小組，協助確保對這些考量和機會有共同的了解。</span><span class="sxs-lookup"><span data-stu-id="44fe4-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="44fe4-140">讓每個人都從一組共同的術語和基本原則中工作，有助於確保架構模式和實踐的一致應用。</span><span class="sxs-lookup"><span data-stu-id="44fe4-140">Having everybody working from a common set of terms and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="44fe4-141">參考</span><span class="sxs-lookup"><span data-stu-id="44fe4-141">References</span></span>

- <span data-ttu-id="44fe4-142">**gRPC 網站**
  <https://grpc.io></span><span class="sxs-lookup"><span data-stu-id="44fe4-142">**gRPC website**
<https://grpc.io></span></span>
- <span data-ttu-id="44fe4-143">**在 .NET 核心和 .NET 框架之間選擇伺服器應用**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span><span class="sxs-lookup"><span data-stu-id="44fe4-143">**Choosing between .NET Core and .NET Framework for server apps**
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="44fe4-144">下一步</span><span class="sxs-lookup"><span data-stu-id="44fe4-144">Next</span></span>](introduction.md)
