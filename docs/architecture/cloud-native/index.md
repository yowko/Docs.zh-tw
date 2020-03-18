---
title: 為 Azure 構建雲本機 .NET 應用程式
description: 利用 Azure 的容器、微服務和無伺服器功能構建雲本機應用程式的指南。
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: 7f14a690d0153edc43f0ce7f4e91c9e9cd2c6858
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "71696782"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="4d6a6-103">為 Azure 構建雲本機 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="4d6a6-103">Architecting Cloud Native .NET Applications for Azure</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![封面影像](./media/cover.png)

<span data-ttu-id="4d6a6-105">發行者</span><span class="sxs-lookup"><span data-stu-id="4d6a6-105">PUBLISHED BY</span></span>

<span data-ttu-id="4d6a6-106">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="4d6a6-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="4d6a6-107">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="4d6a6-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="4d6a6-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="4d6a6-108">One Microsoft Way</span></span>

<span data-ttu-id="4d6a6-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="4d6a6-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="4d6a6-110">Copyright © 2019 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="4d6a6-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="4d6a6-111">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="4d6a6-111">All rights reserved.</span></span> <span data-ttu-id="4d6a6-112">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="4d6a6-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="4d6a6-113">本書是以「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="4d6a6-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="4d6a6-114">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路的網站參考) 如有變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="4d6a6-114">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="4d6a6-115">此處描述的一些範例僅供說明之用，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="4d6a6-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="4d6a6-116">並未影射或關聯任何真實的人、事、物。</span><span class="sxs-lookup"><span data-stu-id="4d6a6-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="4d6a6-117">Microsoft 與列於 https://www.microsoft.com「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="4d6a6-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="4d6a6-118">Mac 與 macOS 是 Apple Inc. 的商標。</span><span class="sxs-lookup"><span data-stu-id="4d6a6-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="4d6a6-119">Docker 鯨魚標誌是 Docker， Inc. 經許可使用的注冊商標。</span><span class="sxs-lookup"><span data-stu-id="4d6a6-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="4d6a6-120">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="4d6a6-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="4d6a6-121">作者：</span><span class="sxs-lookup"><span data-stu-id="4d6a6-121">Authors:</span></span>

> <span data-ttu-id="4d6a6-122">**Steve "ardalis" Smith** - 軟體架構設計人員和講師 - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="4d6a6-122">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="4d6a6-123">**羅布·維托 -** 微軟 - 首席雲系統架構師/IP 架構師 - [RobVettor.com](https://robvettor.com)</span><span class="sxs-lookup"><span data-stu-id="4d6a6-123">**Rob Vettor** - Microsoft - Principal Cloud System Architect/IP Architect - [RobVettor.com](https://robvettor.com)</span></span>

<span data-ttu-id="4d6a6-124">參與者和檢閱者：</span><span class="sxs-lookup"><span data-stu-id="4d6a6-124">Participants and Reviewers:</span></span>

> <span data-ttu-id="4d6a6-125">**塞薩爾·德拉托雷**，微軟.NET團隊首席專案經理</span><span class="sxs-lookup"><span data-stu-id="4d6a6-125">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="4d6a6-126">**Nish Anil**，Microsoft NET 小組資深方案經理</span><span class="sxs-lookup"><span data-stu-id="4d6a6-126">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>

<span data-ttu-id="4d6a6-127">編輯者：</span><span class="sxs-lookup"><span data-stu-id="4d6a6-127">Editors:</span></span>

> <span data-ttu-id="4d6a6-128">**Maira Wenzel**， Sr. 內容開發人員， .NET 團隊， 微軟</span><span class="sxs-lookup"><span data-stu-id="4d6a6-128">**Maira Wenzel**, Sr. Content Developer, .NET team, Microsoft</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="4d6a6-129">誰應該使用本指南</span><span class="sxs-lookup"><span data-stu-id="4d6a6-129">Who should use this guide</span></span>

<span data-ttu-id="4d6a6-130">本指南的讀者主要是開發人員、開發主管和架構師，他們有興趣學習如何構建專為雲設計的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4d6a6-130">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="4d6a6-131">次要受眾是計畫選擇是否使用雲原生方法構建應用程式的技術決策者。</span><span class="sxs-lookup"><span data-stu-id="4d6a6-131">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="4d6a6-132">此指南的使用方式</span><span class="sxs-lookup"><span data-stu-id="4d6a6-132">How you can use this guide</span></span>

<span data-ttu-id="4d6a6-133">本指南首先定義雲本機，並介紹使用雲原生原則和技術構建的參考應用程式。</span><span class="sxs-lookup"><span data-stu-id="4d6a6-133">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="4d6a6-134">除了前兩章之外，本書的其餘部分被分解為特定章節，重點討論大多數雲原生應用程式共有的主題。</span><span class="sxs-lookup"><span data-stu-id="4d6a6-134">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="4d6a6-135">您可以跳轉到以下任一章節，瞭解雲本機方法：</span><span class="sxs-lookup"><span data-stu-id="4d6a6-135">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="4d6a6-136">資料和資料訪問</span><span class="sxs-lookup"><span data-stu-id="4d6a6-136">Data and data access</span></span>
- <span data-ttu-id="4d6a6-137">通訊模式</span><span class="sxs-lookup"><span data-stu-id="4d6a6-137">Communication patterns</span></span>
- <span data-ttu-id="4d6a6-138">擴展和可擴充性</span><span class="sxs-lookup"><span data-stu-id="4d6a6-138">Scaling and scalability</span></span>
- <span data-ttu-id="4d6a6-139">應用程式恢復能力</span><span class="sxs-lookup"><span data-stu-id="4d6a6-139">Application resiliency</span></span>
- <span data-ttu-id="4d6a6-140">監視與健康狀態</span><span class="sxs-lookup"><span data-stu-id="4d6a6-140">Monitoring and health</span></span>
- <span data-ttu-id="4d6a6-141">身份和安全</span><span class="sxs-lookup"><span data-stu-id="4d6a6-141">Identity and security</span></span>
- <span data-ttu-id="4d6a6-142">DevOps</span><span class="sxs-lookup"><span data-stu-id="4d6a6-142">DevOps</span></span>

<span data-ttu-id="4d6a6-143">本指南以 PDF 格式和連線形式提供。</span><span class="sxs-lookup"><span data-stu-id="4d6a6-143">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="4d6a6-144">請隨時將本文檔或指向其線上版本的連結轉發給您的團隊，以説明確保對這些主題達成共識。</span><span class="sxs-lookup"><span data-stu-id="4d6a6-144">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="4d6a6-145">這些主題大多得益于對基本原則和模式的一致理解，以及與這些主題相關的決策所涉及的權衡。</span><span class="sxs-lookup"><span data-stu-id="4d6a6-145">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="4d6a6-146">本文檔的目標是為團隊及其領導者提供所需的資訊，以便對其應用程式的體系結構、開發和託管做出明智的決策。</span><span class="sxs-lookup"><span data-stu-id="4d6a6-146">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="4d6a6-147">下一步</span><span class="sxs-lookup"><span data-stu-id="4d6a6-147">Next</span></span>](introduction.md)
