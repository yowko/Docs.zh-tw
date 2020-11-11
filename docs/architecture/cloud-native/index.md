---
title: 設計適用于 Azure 的雲端原生 .NET 應用程式
description: 利用 Azure 的容器、微服務和無伺服器功能來建立雲端原生應用程式的指南。
author: ardalis
ms.date: 11/10/2020
ms.openlocfilehash: 673bfef27c3767f68b1c30d4383cee010ba377f0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506645"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="0b1d3-103">設計適用于 Azure 的雲端原生 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="0b1d3-103">Architecting Cloud Native .NET Applications for Azure</span></span>

![封面影像](./media/cover.png)

<span data-ttu-id="0b1d3-105">**1.0 版**</span><span class="sxs-lookup"><span data-stu-id="0b1d3-105">**EDITION v1.0**</span></span>

<span data-ttu-id="0b1d3-106">請參閱 [變更記錄](https://aka.ms/cn-ebook-changelog) ，以取得書籍更新和社區貢獻。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-106">Refer [changelog](https://aka.ms/cn-ebook-changelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="0b1d3-107">發行者</span><span class="sxs-lookup"><span data-stu-id="0b1d3-107">PUBLISHED BY</span></span>

<span data-ttu-id="0b1d3-108">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="0b1d3-108">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="0b1d3-109">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="0b1d3-109">A division of Microsoft Corporation</span></span>

<span data-ttu-id="0b1d3-110">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="0b1d3-110">One Microsoft Way</span></span>

<span data-ttu-id="0b1d3-111">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="0b1d3-111">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="0b1d3-112">&copy;Microsoft Corporation 的著作權2020</span><span class="sxs-lookup"><span data-stu-id="0b1d3-112">Copyright &copy; 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="0b1d3-113">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-113">All rights reserved.</span></span> <span data-ttu-id="0b1d3-114">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-114">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="0b1d3-115">本書依照「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-115">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="0b1d3-116">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路的網站參考) 如有變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-116">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="0b1d3-117">此處描述的一些範例僅供說明之用，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-117">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="0b1d3-118">並未影射或關聯任何真實的人、事、物。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-118">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="0b1d3-119">Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-119">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="0b1d3-120">Mac 與 macOS 是 Apple Inc. 的商標。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-120">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="0b1d3-121">Docker whale 標誌是 Docker，Inc. 所用的注冊商標。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-121">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="0b1d3-122">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-122">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="0b1d3-123">作者：</span><span class="sxs-lookup"><span data-stu-id="0b1d3-123">Authors:</span></span>

> <span data-ttu-id="0b1d3-124">**Vettor** ，首席雲端系統架構設計師/IP 架構師- [thinkingincloudnative.com](https://thinkingincloudnative.com/about/)，Microsoft</span><span class="sxs-lookup"><span data-stu-id="0b1d3-124">**Rob Vettor** , Principal Cloud System Architect/IP Architect - [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft</span></span>
>
> <span data-ttu-id="0b1d3-125">**Steve "ardalis" Smith** 、軟體架構設計人員和講師- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="0b1d3-125">**Steve "ardalis" Smith** , Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="0b1d3-126">參與者和審核者：</span><span class="sxs-lookup"><span data-stu-id="0b1d3-126">Participants and Reviewers:</span></span>

> <span data-ttu-id="0b1d3-127">**Cesar De La Torre** ，首席計畫經理，.net 團隊，Microsoft</span><span class="sxs-lookup"><span data-stu-id="0b1d3-127">**Cesar De la Torre** , Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="0b1d3-128">**Nish Anil** ，Microsoft 資深專案經理，.net 團隊</span><span class="sxs-lookup"><span data-stu-id="0b1d3-128">**Nish Anil** , Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="0b1d3-129">**Jeremy Likness** ，Microsoft 資深專案經理，.net 團隊</span><span class="sxs-lookup"><span data-stu-id="0b1d3-129">**Jeremy Likness** , Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="0b1d3-130">Microsoft 資深雲端提倡者 **Cecil Phillip**</span><span class="sxs-lookup"><span data-stu-id="0b1d3-130">**Cecil Phillip** , Senior Cloud Advocate, Microsoft</span></span>

<span data-ttu-id="0b1d3-131">編輯者：</span><span class="sxs-lookup"><span data-stu-id="0b1d3-131">Editors:</span></span>

> <span data-ttu-id="0b1d3-132">**Maira Wenzel** ，Microsoft 的專案經理，.net 團隊</span><span class="sxs-lookup"><span data-stu-id="0b1d3-132">**Maira Wenzel** , Program Manager, .NET team, Microsoft</span></span>

## <a name="version"></a><span data-ttu-id="0b1d3-133">版本</span><span class="sxs-lookup"><span data-stu-id="0b1d3-133">Version</span></span>

<span data-ttu-id="0b1d3-134">本指南已撰寫成涵蓋 **.Net core 3.1** 版本，以及許多與相同「wave」技術相關的其他更新 (也就是，Azure 和其他協力廠商技術) 導致及時使用 .net Core 3.1 版本。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-134">This guide has been written to cover **.NET Core 3.1** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="0b1d3-135">誰應該使用本指南</span><span class="sxs-lookup"><span data-stu-id="0b1d3-135">Who should use this guide</span></span>

<span data-ttu-id="0b1d3-136">本指南的物件主要是開發人員、開發組長和架構設計人員，想要瞭解如何建立針對雲端設計的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-136">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="0b1d3-137">次要物件是技術決策者，其打算選擇是否要使用雲端原生方法來建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-137">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="0b1d3-138">此指南的使用方式</span><span class="sxs-lookup"><span data-stu-id="0b1d3-138">How you can use this guide</span></span>

<span data-ttu-id="0b1d3-139">本指南一開始會定義雲端原生，並介紹使用雲端原生原則和技術建立的參考應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-139">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="0b1d3-140">除了前兩個章節之外，本書的其餘部分會細分為著重于大部分雲端原生應用程式常見主題的特定章節。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-140">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="0b1d3-141">您可以跳到上述任何章節，以瞭解雲端原生方法：</span><span class="sxs-lookup"><span data-stu-id="0b1d3-141">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="0b1d3-142">資料和資料存取</span><span class="sxs-lookup"><span data-stu-id="0b1d3-142">Data and data access</span></span>
- <span data-ttu-id="0b1d3-143">通訊模式</span><span class="sxs-lookup"><span data-stu-id="0b1d3-143">Communication patterns</span></span>
- <span data-ttu-id="0b1d3-144">調整規模和擴充性</span><span class="sxs-lookup"><span data-stu-id="0b1d3-144">Scaling and scalability</span></span>
- <span data-ttu-id="0b1d3-145">應用程式復原</span><span class="sxs-lookup"><span data-stu-id="0b1d3-145">Application resiliency</span></span>
- <span data-ttu-id="0b1d3-146">監視與健康狀態</span><span class="sxs-lookup"><span data-stu-id="0b1d3-146">Monitoring and health</span></span>
- <span data-ttu-id="0b1d3-147">身分識別與安全性</span><span class="sxs-lookup"><span data-stu-id="0b1d3-147">Identity and security</span></span>
- <span data-ttu-id="0b1d3-148">DevOps</span><span class="sxs-lookup"><span data-stu-id="0b1d3-148">DevOps</span></span>

<span data-ttu-id="0b1d3-149">您可以在 [PDF](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf) 表單和線上取得本指南。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-149">This guide is available both in [PDF](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf) form and online.</span></span> <span data-ttu-id="0b1d3-150">您可以將這份檔或其線上版本的連結，提供給您的小組，以協助確保對這些主題有大致的瞭解。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-150">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="0b1d3-151">這些主題大多都是從一致瞭解基礎原則和模式，以及與這些主題相關的決策相關的取捨中獲益。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-151">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="0b1d3-152">本檔的目標是要讓小組和領導人擁有針對其應用程式架構、開發和裝載做出明智決策所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-152">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="0b1d3-153">傳送您的意見反應</span><span class="sxs-lookup"><span data-stu-id="0b1d3-153">Send your feedback</span></span>

<span data-ttu-id="0b1d3-154">本書和相關的範例不斷演進，所以您的意見反應歡迎！</span><span class="sxs-lookup"><span data-stu-id="0b1d3-154">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="0b1d3-155">如果您有關于如何改進本書的意見，請使用內建于 [GitHub 問題](https://github.com/dotnet/docs/issues)之任何頁面底部的意見反應區段。</span><span class="sxs-lookup"><span data-stu-id="0b1d3-155">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="0b1d3-156">下一步</span><span class="sxs-lookup"><span data-stu-id="0b1d3-156">Next</span></span>](introduction.md)
