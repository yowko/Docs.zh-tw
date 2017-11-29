---
title: 1028 - CompleteTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77ef22bd29c167b5be26ceb5360397d38c547c22
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="1bcae-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="1bcae-102">1028 - CompleteTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="1bcae-103">屬性</span><span class="sxs-lookup"><span data-stu-id="1bcae-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1bcae-104">ID</span><span class="sxs-lookup"><span data-stu-id="1bcae-104">ID</span></span>|<span data-ttu-id="1bcae-105">1028</span><span class="sxs-lookup"><span data-stu-id="1bcae-105">1028</span></span>|  
|<span data-ttu-id="1bcae-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="1bcae-106">Keywords</span></span>|<span data-ttu-id="1bcae-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1bcae-107">WFRuntime</span></span>|  
|<span data-ttu-id="1bcae-108">層級</span><span class="sxs-lookup"><span data-stu-id="1bcae-108">Level</span></span>|<span data-ttu-id="1bcae-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="1bcae-109">Verbose</span></span>|  
|<span data-ttu-id="1bcae-110">通道</span><span class="sxs-lookup"><span data-stu-id="1bcae-110">Channel</span></span>|<span data-ttu-id="1bcae-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="1bcae-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1bcae-112">描述</span><span class="sxs-lookup"><span data-stu-id="1bcae-112">Description</span></span>  
 <span data-ttu-id="1bcae-113">表示 TransactionContextWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="1bcae-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1bcae-114">訊息</span><span class="sxs-lookup"><span data-stu-id="1bcae-114">Message</span></span>  
 <span data-ttu-id="1bcae-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 TransactionContextWorkItem。</span><span class="sxs-lookup"><span data-stu-id="1bcae-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1bcae-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1bcae-116">Details</span></span>  
  
|<span data-ttu-id="1bcae-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="1bcae-117">Data Item Name</span></span>|<span data-ttu-id="1bcae-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="1bcae-118">Data Item Type</span></span>|<span data-ttu-id="1bcae-119">描述</span><span class="sxs-lookup"><span data-stu-id="1bcae-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1bcae-120">活動</span><span class="sxs-lookup"><span data-stu-id="1bcae-120">Activity</span></span>|<span data-ttu-id="1bcae-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="1bcae-121">xs:string</span></span>|<span data-ttu-id="1bcae-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="1bcae-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="1bcae-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1bcae-123">DisplayName</span></span>|<span data-ttu-id="1bcae-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="1bcae-124">xs:string</span></span>|<span data-ttu-id="1bcae-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="1bcae-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="1bcae-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="1bcae-126">InstanceId</span></span>|<span data-ttu-id="1bcae-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="1bcae-127">xs:string</span></span>|<span data-ttu-id="1bcae-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="1bcae-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="1bcae-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1bcae-129">AppDomain</span></span>|<span data-ttu-id="1bcae-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="1bcae-130">xs:string</span></span>|<span data-ttu-id="1bcae-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="1bcae-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
