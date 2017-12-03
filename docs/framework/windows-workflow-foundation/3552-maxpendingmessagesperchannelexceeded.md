---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5455472a5b9ebdba7aea7d0384ce9cd4a9a2849d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="c13de-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="c13de-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="c13de-103">屬性</span><span class="sxs-lookup"><span data-stu-id="c13de-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c13de-104">ID</span><span class="sxs-lookup"><span data-stu-id="c13de-104">ID</span></span>|<span data-ttu-id="c13de-105">3552</span><span class="sxs-lookup"><span data-stu-id="c13de-105">3552</span></span>|  
|<span data-ttu-id="c13de-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c13de-106">Keywords</span></span>|<span data-ttu-id="c13de-107">配額、WFServices</span><span class="sxs-lookup"><span data-stu-id="c13de-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="c13de-108">層級</span><span class="sxs-lookup"><span data-stu-id="c13de-108">Level</span></span>|<span data-ttu-id="c13de-109">警告</span><span class="sxs-lookup"><span data-stu-id="c13de-109">Warning</span></span>|  
|<span data-ttu-id="c13de-110">通道</span><span class="sxs-lookup"><span data-stu-id="c13de-110">Channel</span></span>|<span data-ttu-id="c13de-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c13de-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c13de-112">描述</span><span class="sxs-lookup"><span data-stu-id="c13de-112">Description</span></span>  
 <span data-ttu-id="c13de-113">表示已達到節流 'MaxPendingMessagesPerChannel' 限制。</span><span class="sxs-lookup"><span data-stu-id="c13de-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c13de-114">訊息</span><span class="sxs-lookup"><span data-stu-id="c13de-114">Message</span></span>  
 <span data-ttu-id="c13de-115">已達到節流 'MaxPendingMessagesPerChannel' 限制為 '%1'。</span><span class="sxs-lookup"><span data-stu-id="c13de-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="c13de-116">若要增加此限制，請調整 BufferedReceiveServiceBehavior 上的 MaxPendingMessagesPerChannel 屬性。</span><span class="sxs-lookup"><span data-stu-id="c13de-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c13de-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c13de-117">Details</span></span>  
  
|<span data-ttu-id="c13de-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="c13de-118">Data Item Name</span></span>|<span data-ttu-id="c13de-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="c13de-119">Data Item Type</span></span>|<span data-ttu-id="c13de-120">描述</span><span class="sxs-lookup"><span data-stu-id="c13de-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c13de-121">限制</span><span class="sxs-lookup"><span data-stu-id="c13de-121">Limit</span></span>|<span data-ttu-id="c13de-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="c13de-122">xs:string</span></span>|<span data-ttu-id="c13de-123">已達到 MaxPendingMessagesPerChannel 節流的限制。</span><span class="sxs-lookup"><span data-stu-id="c13de-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="c13de-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c13de-124">AppDomain</span></span>|<span data-ttu-id="c13de-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="c13de-125">xs:string</span></span>|<span data-ttu-id="c13de-126">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="c13de-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
