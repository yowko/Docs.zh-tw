---
title: 1027 - StartTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
ms.openlocfilehash: 231a7607f2ce9a38e8dd6c1486a68bc9eb459e5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510805"
---
# <a name="1027---starttransactioncontextworkitem"></a><span data-ttu-id="58a84-102">1027 - StartTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="58a84-102">1027 - StartTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="58a84-103">屬性</span><span class="sxs-lookup"><span data-stu-id="58a84-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="58a84-104">ID</span><span class="sxs-lookup"><span data-stu-id="58a84-104">ID</span></span>|<span data-ttu-id="58a84-105">1027</span><span class="sxs-lookup"><span data-stu-id="58a84-105">1027</span></span>|  
|<span data-ttu-id="58a84-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="58a84-106">Keywords</span></span>|<span data-ttu-id="58a84-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="58a84-107">WFRuntime</span></span>|  
|<span data-ttu-id="58a84-108">層級</span><span class="sxs-lookup"><span data-stu-id="58a84-108">Level</span></span>|<span data-ttu-id="58a84-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="58a84-109">Verbose</span></span>|  
|<span data-ttu-id="58a84-110">通道</span><span class="sxs-lookup"><span data-stu-id="58a84-110">Channel</span></span>|<span data-ttu-id="58a84-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="58a84-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="58a84-112">描述</span><span class="sxs-lookup"><span data-stu-id="58a84-112">Description</span></span>  
 <span data-ttu-id="58a84-113">表示 TransactionContextWorkItem 開始執行。</span><span class="sxs-lookup"><span data-stu-id="58a84-113">Indicates a TransactionContextWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="58a84-114">訊息</span><span class="sxs-lookup"><span data-stu-id="58a84-114">Message</span></span>  
 <span data-ttu-id="58a84-115">開始執行活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 TransactionContextWorkItem。</span><span class="sxs-lookup"><span data-stu-id="58a84-115">Starting execution of a TransactionContextWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="58a84-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="58a84-116">Details</span></span>  
  
|<span data-ttu-id="58a84-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="58a84-117">Data Item Name</span></span>|<span data-ttu-id="58a84-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="58a84-118">Data Item Type</span></span>|<span data-ttu-id="58a84-119">描述</span><span class="sxs-lookup"><span data-stu-id="58a84-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="58a84-120">活動</span><span class="sxs-lookup"><span data-stu-id="58a84-120">Activity</span></span>|<span data-ttu-id="58a84-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="58a84-121">xs:string</span></span>|<span data-ttu-id="58a84-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="58a84-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="58a84-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="58a84-123">DisplayName</span></span>|<span data-ttu-id="58a84-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="58a84-124">xs:string</span></span>|<span data-ttu-id="58a84-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="58a84-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="58a84-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="58a84-126">InstanceId</span></span>|<span data-ttu-id="58a84-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="58a84-127">xs:string</span></span>|<span data-ttu-id="58a84-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="58a84-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="58a84-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="58a84-129">AppDomain</span></span>|<span data-ttu-id="58a84-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="58a84-130">xs:string</span></span>|<span data-ttu-id="58a84-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="58a84-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
