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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5ba5e4aa8e1338321838e40db7d976107315ef64
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="1e054-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="1e054-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="1e054-103">屬性</span><span class="sxs-lookup"><span data-stu-id="1e054-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1e054-104">ID</span><span class="sxs-lookup"><span data-stu-id="1e054-104">ID</span></span>|<span data-ttu-id="1e054-105">3552</span><span class="sxs-lookup"><span data-stu-id="1e054-105">3552</span></span>|  
|<span data-ttu-id="1e054-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="1e054-106">Keywords</span></span>|<span data-ttu-id="1e054-107">配額、WFServices</span><span class="sxs-lookup"><span data-stu-id="1e054-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="1e054-108">層級</span><span class="sxs-lookup"><span data-stu-id="1e054-108">Level</span></span>|<span data-ttu-id="1e054-109">警告</span><span class="sxs-lookup"><span data-stu-id="1e054-109">Warning</span></span>|  
|<span data-ttu-id="1e054-110">通道</span><span class="sxs-lookup"><span data-stu-id="1e054-110">Channel</span></span>|<span data-ttu-id="1e054-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="1e054-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1e054-112">描述</span><span class="sxs-lookup"><span data-stu-id="1e054-112">Description</span></span>  
 <span data-ttu-id="1e054-113">表示已達到節流 'MaxPendingMessagesPerChannel' 限制。</span><span class="sxs-lookup"><span data-stu-id="1e054-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1e054-114">訊息</span><span class="sxs-lookup"><span data-stu-id="1e054-114">Message</span></span>  
 <span data-ttu-id="1e054-115">已達到節流 'MaxPendingMessagesPerChannel' 限制為 '%1'。</span><span class="sxs-lookup"><span data-stu-id="1e054-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="1e054-116">若要增加此限制，請調整 BufferedReceiveServiceBehavior 上的 MaxPendingMessagesPerChannel 屬性。</span><span class="sxs-lookup"><span data-stu-id="1e054-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1e054-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1e054-117">Details</span></span>  
  
|<span data-ttu-id="1e054-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="1e054-118">Data Item Name</span></span>|<span data-ttu-id="1e054-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="1e054-119">Data Item Type</span></span>|<span data-ttu-id="1e054-120">描述</span><span class="sxs-lookup"><span data-stu-id="1e054-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1e054-121">限制</span><span class="sxs-lookup"><span data-stu-id="1e054-121">Limit</span></span>|<span data-ttu-id="1e054-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e054-122">xs:string</span></span>|<span data-ttu-id="1e054-123">已達到 MaxPendingMessagesPerChannel 節流的限制。</span><span class="sxs-lookup"><span data-stu-id="1e054-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="1e054-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1e054-124">AppDomain</span></span>|<span data-ttu-id="1e054-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e054-125">xs:string</span></span>|<span data-ttu-id="1e054-126">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="1e054-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
