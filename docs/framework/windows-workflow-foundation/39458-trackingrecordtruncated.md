---
title: 39458 - TrackingRecordTruncated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d2bc07cff75fce7ddb50da9f54d161d7f235cab
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="997c1-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="997c1-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="997c1-103">屬性</span><span class="sxs-lookup"><span data-stu-id="997c1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="997c1-104">ID</span><span class="sxs-lookup"><span data-stu-id="997c1-104">ID</span></span>|<span data-ttu-id="997c1-105">39458</span><span class="sxs-lookup"><span data-stu-id="997c1-105">39458</span></span>|  
|<span data-ttu-id="997c1-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="997c1-106">Keywords</span></span>|<span data-ttu-id="997c1-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="997c1-107">WFTracking</span></span>|  
|<span data-ttu-id="997c1-108">層級</span><span class="sxs-lookup"><span data-stu-id="997c1-108">Level</span></span>|<span data-ttu-id="997c1-109">警告</span><span class="sxs-lookup"><span data-stu-id="997c1-109">Warning</span></span>|  
|<span data-ttu-id="997c1-110">通道</span><span class="sxs-lookup"><span data-stu-id="997c1-110">Channel</span></span>|<span data-ttu-id="997c1-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="997c1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="997c1-112">描述</span><span class="sxs-lookup"><span data-stu-id="997c1-112">Description</span></span>  
 <span data-ttu-id="997c1-113">表示追蹤記錄已被截斷。</span><span class="sxs-lookup"><span data-stu-id="997c1-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="997c1-114">變數/標註/使用者資料已移除。</span><span class="sxs-lookup"><span data-stu-id="997c1-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="997c1-115">訊息</span><span class="sxs-lookup"><span data-stu-id="997c1-115">Message</span></span>  
 <span data-ttu-id="997c1-116">已將截斷的追蹤記錄 %1 寫入提供者 %2 的 ETW 工作階段。</span><span class="sxs-lookup"><span data-stu-id="997c1-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="997c1-117">變數/附註/使用者資料已移除</span><span class="sxs-lookup"><span data-stu-id="997c1-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="997c1-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="997c1-118">Details</span></span>  
  
|<span data-ttu-id="997c1-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="997c1-119">Data Item Name</span></span>|<span data-ttu-id="997c1-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="997c1-120">Data Item Type</span></span>|<span data-ttu-id="997c1-121">描述</span><span class="sxs-lookup"><span data-stu-id="997c1-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="997c1-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="997c1-122">RecordNumber</span></span>|<span data-ttu-id="997c1-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="997c1-123">xs:string</span></span>|<span data-ttu-id="997c1-124">追蹤記錄號碼。</span><span class="sxs-lookup"><span data-stu-id="997c1-124">The tracking record number.</span></span>|  
|<span data-ttu-id="997c1-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="997c1-125">ProviderId</span></span>|<span data-ttu-id="997c1-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="997c1-126">xs:string</span></span>|<span data-ttu-id="997c1-127">ETW 提供者 ID。</span><span class="sxs-lookup"><span data-stu-id="997c1-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="997c1-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="997c1-128">AppDomain</span></span>|<span data-ttu-id="997c1-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="997c1-129">xs:string</span></span>|<span data-ttu-id="997c1-130">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="997c1-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
