---
title: WCF 開發人員的 ASP.NET Core gRPC-WCF 開發人員的 gRPC
description: 要寫入的
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: dc39fc96e7154fb50acd0b65a58586b3fa12ab50
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696912"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a><span data-ttu-id="b1b96-103">適用於 WCF 開發人員的 ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="b1b96-103">ASP.NET Core gRPC for WCF Developers</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![封面影像](./media/cover.png)

<span data-ttu-id="b1b96-105">發行者</span><span class="sxs-lookup"><span data-stu-id="b1b96-105">PUBLISHED BY</span></span>

<span data-ttu-id="b1b96-106">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="b1b96-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="b1b96-107">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="b1b96-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="b1b96-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="b1b96-108">One Microsoft Way</span></span>

<span data-ttu-id="b1b96-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="b1b96-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="b1b96-110">Copyright © 2019 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="b1b96-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="b1b96-111">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="b1b96-111">All rights reserved.</span></span> <span data-ttu-id="b1b96-112">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="b1b96-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="b1b96-113">本書是以「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="b1b96-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="b1b96-114">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="b1b96-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="b1b96-115">此處所描述的一些範例僅供說明，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="b1b96-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="b1b96-116">任何實際關聯或連結純屬巧合。</span><span class="sxs-lookup"><span data-stu-id="b1b96-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="b1b96-117">Microsoft 與列於 https://www.microsoft.com 「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="b1b96-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="b1b96-118">Docker 鯨魚標誌是 Docker, Inc. 的註冊商標。使用需要許可。</span><span class="sxs-lookup"><span data-stu-id="b1b96-118">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="b1b96-119">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="b1b96-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="b1b96-120">作者:</span><span class="sxs-lookup"><span data-stu-id="b1b96-120">Author:</span></span>

> <span data-ttu-id="b1b96-121">**Mark Rendle** -首席技術長-[視覺的編碼](https://visualrecode.com)</span><span class="sxs-lookup"><span data-stu-id="b1b96-121">**Mark Rendle** - Chief Technical Officer - [Visual Recode](https://visualrecode.com)</span></span>
>
> <span data-ttu-id="b1b96-122">**Miranda Steiner** -技術作者</span><span class="sxs-lookup"><span data-stu-id="b1b96-122">**Miranda Steiner** - Technical Author</span></span>

<span data-ttu-id="b1b96-123">編輯者：</span><span class="sxs-lookup"><span data-stu-id="b1b96-123">Editors:</span></span>

> <span data-ttu-id="b1b96-124">**Maira Wenzel** -Sr 內容開發人員-Microsoft</span><span class="sxs-lookup"><span data-stu-id="b1b96-124">**Maira Wenzel** - Sr Content Developer - Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="b1b96-125">簡介</span><span class="sxs-lookup"><span data-stu-id="b1b96-125">Introduction</span></span>

<span data-ttu-id="b1b96-126">TODO</span><span class="sxs-lookup"><span data-stu-id="b1b96-126">TODO</span></span>

## <a name="purpose"></a><span data-ttu-id="b1b96-127">用途</span><span class="sxs-lookup"><span data-stu-id="b1b96-127">Purpose</span></span>

<span data-ttu-id="b1b96-128">TODO</span><span class="sxs-lookup"><span data-stu-id="b1b96-128">TODO</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="b1b96-129">誰應該使用本指南</span><span class="sxs-lookup"><span data-stu-id="b1b96-129">Who should use this guide</span></span>

<span data-ttu-id="b1b96-130">**更新此**</span><span class="sxs-lookup"><span data-stu-id="b1b96-130">**UPDATE THIS**</span></span>

<span data-ttu-id="b1b96-131">本指南的物件是 WCF 開發人員、開發組長和架構設計人員，有興趣將 .NET 4 和更早版本的 WCF 方案遷移到使用 gRPC services ASP.NET Core 3.0。</span><span class="sxs-lookup"><span data-stu-id="b1b96-131">The audience for this guide is WCF developers, development leads, and architects who are interested in migrating WCF solutions on .NET 4 and earlier to ASP.NET Core 3.0 using gRPC services.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="b1b96-132">此指南的使用方式</span><span class="sxs-lookup"><span data-stu-id="b1b96-132">How you can use this guide</span></span>

<span data-ttu-id="b1b96-133">**更新此**</span><span class="sxs-lookup"><span data-stu-id="b1b96-133">**UPDATE THIS**</span></span>

<span data-ttu-id="b1b96-134">這是在 ASP.NET Core 3.0 中建立 gRPC 服務的簡要介紹，並特別參考 WCF 做為類似的平臺。</span><span class="sxs-lookup"><span data-stu-id="b1b96-134">This is a short introduction to building gRPC Services in ASP.NET Core 3.0 with particular reference to WCF as an analogous platform.</span></span> <span data-ttu-id="b1b96-135">其中說明 gRPC 的原則，並將每個概念關聯至 WCF 的對等功能，並提供將現有 WCF 應用程式遷移至 gRPC 的指引。</span><span class="sxs-lookup"><span data-stu-id="b1b96-135">It explains the principles of gRPC, relating each concept to the equivalent features of WCF, and offers guidance for migrating an existing WCF application to gRPC.</span></span> <span data-ttu-id="b1b96-136">對於有 WCF 經驗，而且想要學習 gRPC 以建立新服務的開發人員而言，這也很有用。</span><span class="sxs-lookup"><span data-stu-id="b1b96-136">It is also useful for developers who have experience of WCF and are looking to learn gRPC to build new services.</span></span> <span data-ttu-id="b1b96-137">範例應用程式可用來作為您自己專案的範本或參考，而且您可以免費複製並重複使用本書或其範例中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b1b96-137">The sample application can be used as a template or reference for your own projects, and you are free to copy and reuse code from the book or its samples.</span></span>

<span data-ttu-id="b1b96-138">請隨意將本指南轉寄給您的小組，協助確保對這些考量和機會有共同的了解。</span><span class="sxs-lookup"><span data-stu-id="b1b96-138">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="b1b96-139">讓所有人都使用一組共用術語和基礎原則，有助確保套用一致的架構模式和做法。</span><span class="sxs-lookup"><span data-stu-id="b1b96-139">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="b1b96-140">參考</span><span class="sxs-lookup"><span data-stu-id="b1b96-140">References</span></span>

- <span data-ttu-id="b1b96-141">**gRPC 網站**</span><span class="sxs-lookup"><span data-stu-id="b1b96-141">**gRPC web site**</span></span>  
  <https://grpc.io>
- <span data-ttu-id="b1b96-142">**針對伺服器應用程式在 .NET Core 和 .NET Framework 之間進行選擇**</span><span class="sxs-lookup"><span data-stu-id="b1b96-142">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[<span data-ttu-id="b1b96-143">下一步</span><span class="sxs-lookup"><span data-stu-id="b1b96-143">Next</span></span>](introduction.md)
