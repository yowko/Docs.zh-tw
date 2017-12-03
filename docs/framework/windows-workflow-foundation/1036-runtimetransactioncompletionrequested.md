---
title: 1036 - RuntimeTransactionCompletionRequested
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 112063d5cd550f438541b2d775eaa49124d9cc02
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="45375-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="45375-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="45375-103">屬性</span><span class="sxs-lookup"><span data-stu-id="45375-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="45375-104">ID</span><span class="sxs-lookup"><span data-stu-id="45375-104">ID</span></span>|<span data-ttu-id="45375-105">1036</span><span class="sxs-lookup"><span data-stu-id="45375-105">1036</span></span>|  
|<span data-ttu-id="45375-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="45375-106">Keywords</span></span>|<span data-ttu-id="45375-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="45375-107">WFRuntime</span></span>|  
|<span data-ttu-id="45375-108">層級</span><span class="sxs-lookup"><span data-stu-id="45375-108">Level</span></span>|<span data-ttu-id="45375-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="45375-109">Verbose</span></span>|  
|<span data-ttu-id="45375-110">通道</span><span class="sxs-lookup"><span data-stu-id="45375-110">Channel</span></span>|<span data-ttu-id="45375-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="45375-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="45375-112">描述</span><span class="sxs-lookup"><span data-stu-id="45375-112">Description</span></span>  
 <span data-ttu-id="45375-113">表示活動已排程執行階段交易的完成。</span><span class="sxs-lookup"><span data-stu-id="45375-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="45375-114">訊息</span><span class="sxs-lookup"><span data-stu-id="45375-114">Message</span></span>  
 <span data-ttu-id="45375-115">活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 已排程完成執行階段交易。</span><span class="sxs-lookup"><span data-stu-id="45375-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="45375-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="45375-116">Details</span></span>  
  
|<span data-ttu-id="45375-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="45375-117">Data Item Name</span></span>|<span data-ttu-id="45375-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="45375-118">Data Item Type</span></span>|<span data-ttu-id="45375-119">描述</span><span class="sxs-lookup"><span data-stu-id="45375-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="45375-120">活動</span><span class="sxs-lookup"><span data-stu-id="45375-120">Activity</span></span>|<span data-ttu-id="45375-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="45375-121">xs:string</span></span>|<span data-ttu-id="45375-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="45375-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="45375-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="45375-123">DisplayName</span></span>|<span data-ttu-id="45375-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="45375-124">xs:string</span></span>|<span data-ttu-id="45375-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="45375-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="45375-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="45375-126">InstanceId</span></span>|<span data-ttu-id="45375-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="45375-127">xs:string</span></span>|<span data-ttu-id="45375-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="45375-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="45375-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="45375-129">AppDomain</span></span>|<span data-ttu-id="45375-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="45375-130">xs:string</span></span>|<span data-ttu-id="45375-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="45375-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
