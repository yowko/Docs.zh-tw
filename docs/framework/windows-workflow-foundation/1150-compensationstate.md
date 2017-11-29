---
title: 1150 - CompensationState
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb015842-cc5a-47be-bce5-6af39e567723
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5debccf664768b84a7b213cd012b484df8fe3ef8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1150---compensationstate"></a><span data-ttu-id="99a03-102">1150 - CompensationState</span><span class="sxs-lookup"><span data-stu-id="99a03-102">1150 - CompensationState</span></span>
## <a name="properties"></a><span data-ttu-id="99a03-103">屬性</span><span class="sxs-lookup"><span data-stu-id="99a03-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="99a03-104">ID</span><span class="sxs-lookup"><span data-stu-id="99a03-104">ID</span></span>|<span data-ttu-id="99a03-105">1150</span><span class="sxs-lookup"><span data-stu-id="99a03-105">1150</span></span>|  
|<span data-ttu-id="99a03-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="99a03-106">Keywords</span></span>|<span data-ttu-id="99a03-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="99a03-107">WFActivities</span></span>|  
|<span data-ttu-id="99a03-108">層級</span><span class="sxs-lookup"><span data-stu-id="99a03-108">Level</span></span>|<span data-ttu-id="99a03-109">資訊</span><span class="sxs-lookup"><span data-stu-id="99a03-109">Information</span></span>|  
|<span data-ttu-id="99a03-110">通道</span><span class="sxs-lookup"><span data-stu-id="99a03-110">Channel</span></span>|<span data-ttu-id="99a03-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="99a03-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="99a03-112">描述</span><span class="sxs-lookup"><span data-stu-id="99a03-112">Description</span></span>  
 <span data-ttu-id="99a03-113">表示 CompensableActivity 中的狀態變更。</span><span class="sxs-lookup"><span data-stu-id="99a03-113">Indicates a change of state in a CompensableActivity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="99a03-114">訊息</span><span class="sxs-lookup"><span data-stu-id="99a03-114">Message</span></span>  
 <span data-ttu-id="99a03-115">CompensableActivity '%1' 處於 '%2' 狀態。</span><span class="sxs-lookup"><span data-stu-id="99a03-115">CompensableActivity '%1' is in the '%2' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="99a03-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="99a03-116">Details</span></span>  
  
|<span data-ttu-id="99a03-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="99a03-117">Data Item Name</span></span>|<span data-ttu-id="99a03-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="99a03-118">Data Item Type</span></span>|<span data-ttu-id="99a03-119">描述</span><span class="sxs-lookup"><span data-stu-id="99a03-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="99a03-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="99a03-120">DisplayName</span></span>|<span data-ttu-id="99a03-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="99a03-121">xs:string</span></span>|<span data-ttu-id="99a03-122">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="99a03-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="99a03-123">狀態</span><span class="sxs-lookup"><span data-stu-id="99a03-123">State</span></span>|<span data-ttu-id="99a03-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="99a03-124">xs:string</span></span>|<span data-ttu-id="99a03-125">補償狀態。</span><span class="sxs-lookup"><span data-stu-id="99a03-125">The compensation state.</span></span>|  
|<span data-ttu-id="99a03-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="99a03-126">AppDomain</span></span>|<span data-ttu-id="99a03-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="99a03-127">xs:string</span></span>|<span data-ttu-id="99a03-128">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="99a03-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
