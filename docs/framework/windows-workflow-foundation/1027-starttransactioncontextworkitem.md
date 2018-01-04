---
title: 1027 - StartTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: baa644cb7693b8608f119cf211b3b08ab4b1a2b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1027---starttransactioncontextworkitem"></a><span data-ttu-id="49790-102">1027 - StartTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="49790-102">1027 - StartTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="49790-103">屬性</span><span class="sxs-lookup"><span data-stu-id="49790-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="49790-104">ID</span><span class="sxs-lookup"><span data-stu-id="49790-104">ID</span></span>|<span data-ttu-id="49790-105">1027</span><span class="sxs-lookup"><span data-stu-id="49790-105">1027</span></span>|  
|<span data-ttu-id="49790-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="49790-106">Keywords</span></span>|<span data-ttu-id="49790-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="49790-107">WFRuntime</span></span>|  
|<span data-ttu-id="49790-108">層級</span><span class="sxs-lookup"><span data-stu-id="49790-108">Level</span></span>|<span data-ttu-id="49790-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="49790-109">Verbose</span></span>|  
|<span data-ttu-id="49790-110">通道</span><span class="sxs-lookup"><span data-stu-id="49790-110">Channel</span></span>|<span data-ttu-id="49790-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="49790-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="49790-112">描述</span><span class="sxs-lookup"><span data-stu-id="49790-112">Description</span></span>  
 <span data-ttu-id="49790-113">表示 TransactionContextWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="49790-113">Indicates a TransactionContextWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="49790-114">訊息</span><span class="sxs-lookup"><span data-stu-id="49790-114">Message</span></span>  
 <span data-ttu-id="49790-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 TransactionContextWorkItem。</span><span class="sxs-lookup"><span data-stu-id="49790-115">Starting execution of a TransactionContextWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="49790-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="49790-116">Details</span></span>  
  
|<span data-ttu-id="49790-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="49790-117">Data Item Name</span></span>|<span data-ttu-id="49790-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="49790-118">Data Item Type</span></span>|<span data-ttu-id="49790-119">描述</span><span class="sxs-lookup"><span data-stu-id="49790-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="49790-120">活動</span><span class="sxs-lookup"><span data-stu-id="49790-120">Activity</span></span>|<span data-ttu-id="49790-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="49790-121">xs:string</span></span>|<span data-ttu-id="49790-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="49790-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="49790-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="49790-123">DisplayName</span></span>|<span data-ttu-id="49790-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="49790-124">xs:string</span></span>|<span data-ttu-id="49790-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="49790-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="49790-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="49790-126">InstanceId</span></span>|<span data-ttu-id="49790-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="49790-127">xs:string</span></span>|<span data-ttu-id="49790-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="49790-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="49790-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="49790-129">AppDomain</span></span>|<span data-ttu-id="49790-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="49790-130">xs:string</span></span>|<span data-ttu-id="49790-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="49790-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
