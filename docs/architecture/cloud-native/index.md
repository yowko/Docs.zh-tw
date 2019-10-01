---
title: 架構適用于 Azure 的雲端原生 .NET 應用程式
description: 建立雲端原生應用程式的指南，利用 Azure 的容器、微服務和無伺服器功能。
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: 7f14a690d0153edc43f0ce7f4e91c9e9cd2c6858
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696782"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="b2d41-103">架構適用于 Azure 的雲端原生 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="b2d41-103">Architecting Cloud Native .NET Applications for Azure</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![封面影像](./media/cover.png)

<span data-ttu-id="b2d41-105">發行者</span><span class="sxs-lookup"><span data-stu-id="b2d41-105">PUBLISHED BY</span></span>

<span data-ttu-id="b2d41-106">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="b2d41-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="b2d41-107">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="b2d41-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="b2d41-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="b2d41-108">One Microsoft Way</span></span>

<span data-ttu-id="b2d41-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="b2d41-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="b2d41-110">Copyright © 2019 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="b2d41-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="b2d41-111">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="b2d41-111">All rights reserved.</span></span> <span data-ttu-id="b2d41-112">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="b2d41-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="b2d41-113">本書是以「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="b2d41-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="b2d41-114">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路的網站參考) 如有變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="b2d41-114">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="b2d41-115">此處所描述的一些範例僅供說明，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="b2d41-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="b2d41-116">任何實際關聯或連結純屬巧合。</span><span class="sxs-lookup"><span data-stu-id="b2d41-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="b2d41-117">Microsoft 與列於 https://www.microsoft.com 「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="b2d41-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="b2d41-118">Mac 與 macOS 是 Apple Inc. 的商標。</span><span class="sxs-lookup"><span data-stu-id="b2d41-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="b2d41-119">Docker 鯨魚標誌是 Docker, Inc. 的註冊商標。使用需要許可。</span><span class="sxs-lookup"><span data-stu-id="b2d41-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="b2d41-120">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="b2d41-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="b2d41-121">製作</span><span class="sxs-lookup"><span data-stu-id="b2d41-121">Authors:</span></span>

> <span data-ttu-id="b2d41-122">**Steve "ardalis" Smith** - 軟體架構設計人員和講師 - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="b2d41-122">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="b2d41-123">**Vettor** -Microsoft-主要雲端系統架構師/IP 架構設計人員- [RobVettor.com](https://robvettor.com)</span><span class="sxs-lookup"><span data-stu-id="b2d41-123">**Rob Vettor** - Microsoft - Principal Cloud System Architect/IP Architect - [RobVettor.com](https://robvettor.com)</span></span>

<span data-ttu-id="b2d41-124">參與者和審核者：</span><span class="sxs-lookup"><span data-stu-id="b2d41-124">Participants and Reviewers:</span></span>

> <span data-ttu-id="b2d41-125">**Cesar De La Torre**，首席計畫經理，.net 小組，Microsoft</span><span class="sxs-lookup"><span data-stu-id="b2d41-125">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="b2d41-126">**Nish Anil**，Microsoft NET 小組資深方案經理</span><span class="sxs-lookup"><span data-stu-id="b2d41-126">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>

<span data-ttu-id="b2d41-127">編輯者：</span><span class="sxs-lookup"><span data-stu-id="b2d41-127">Editors:</span></span>

> <span data-ttu-id="b2d41-128">**Maira Wenzel**，Microsoft 的資深內容開發人員，.net 團隊</span><span class="sxs-lookup"><span data-stu-id="b2d41-128">**Maira Wenzel**, Sr. Content Developer, .NET team, Microsoft</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="b2d41-129">誰應該使用本指南</span><span class="sxs-lookup"><span data-stu-id="b2d41-129">Who should use this guide</span></span>

<span data-ttu-id="b2d41-130">本指南的物件主要是開發人員、開發組長和架構設計人員，有興趣學習如何建立專為雲端設計的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2d41-130">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="b2d41-131">次要物件是技術決策者，他們打算選擇是否要使用雲端原生方法來建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2d41-131">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="b2d41-132">此指南的使用方式</span><span class="sxs-lookup"><span data-stu-id="b2d41-132">How you can use this guide</span></span>

<span data-ttu-id="b2d41-133">本指南一開始會定義雲端原生，並介紹使用雲端原生原則和技術建立的參考應用程式。</span><span class="sxs-lookup"><span data-stu-id="b2d41-133">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="b2d41-134">除了這前兩個章節以外，本書的其餘部分會細分為著重于大部分雲端原生應用程式常見主題的特定章節。</span><span class="sxs-lookup"><span data-stu-id="b2d41-134">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="b2d41-135">您可以跳至下列任一章節，以瞭解雲端原生方法：</span><span class="sxs-lookup"><span data-stu-id="b2d41-135">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="b2d41-136">資料和資料存取</span><span class="sxs-lookup"><span data-stu-id="b2d41-136">Data and data access</span></span>
- <span data-ttu-id="b2d41-137">通訊模式</span><span class="sxs-lookup"><span data-stu-id="b2d41-137">Communication patterns</span></span>
- <span data-ttu-id="b2d41-138">調整和擴充性</span><span class="sxs-lookup"><span data-stu-id="b2d41-138">Scaling and scalability</span></span>
- <span data-ttu-id="b2d41-139">應用程式復原</span><span class="sxs-lookup"><span data-stu-id="b2d41-139">Application resiliency</span></span>
- <span data-ttu-id="b2d41-140">監視與健康狀態</span><span class="sxs-lookup"><span data-stu-id="b2d41-140">Monitoring and health</span></span>
- <span data-ttu-id="b2d41-141">身分識別與安全性</span><span class="sxs-lookup"><span data-stu-id="b2d41-141">Identity and security</span></span>
- <span data-ttu-id="b2d41-142">DevOps</span><span class="sxs-lookup"><span data-stu-id="b2d41-142">DevOps</span></span>

<span data-ttu-id="b2d41-143">本指南以 PDF 形式和線上版本提供。</span><span class="sxs-lookup"><span data-stu-id="b2d41-143">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="b2d41-144">請隨意將本檔或其線上版本的連結轉寄給您的小組，以協助確保這些主題的一般瞭解。</span><span class="sxs-lookup"><span data-stu-id="b2d41-144">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="b2d41-145">大部分的主題都是以一致的方式瞭解基礎原則和模式，以及與這些主題相關的決策所牽涉到的取捨。</span><span class="sxs-lookup"><span data-stu-id="b2d41-145">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="b2d41-146">本檔的目標是要為小組及其領導者提供針對其應用程式架構、開發和裝載做出明智決策所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="b2d41-146">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="b2d41-147">下一個</span><span class="sxs-lookup"><span data-stu-id="b2d41-147">Next</span></span>](introduction.md)
