---
title: 1028 - CompleteTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
ms.openlocfilehash: 2fc509dac7e13f30f74c24d8b98cba55ed5f8e1d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275111"
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="01730-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="01730-102">1028 - CompleteTransactionContextWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="01730-103">屬性</span><span class="sxs-lookup"><span data-stu-id="01730-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="01730-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="01730-104">ID</span></span>|<span data-ttu-id="01730-105">1028</span><span class="sxs-lookup"><span data-stu-id="01730-105">1028</span></span>|  
|<span data-ttu-id="01730-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="01730-106">Keywords</span></span>|<span data-ttu-id="01730-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="01730-107">WFRuntime</span></span>|  
|<span data-ttu-id="01730-108">層級</span><span class="sxs-lookup"><span data-stu-id="01730-108">Level</span></span>|<span data-ttu-id="01730-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="01730-109">Verbose</span></span>|  
|<span data-ttu-id="01730-110">通路</span><span class="sxs-lookup"><span data-stu-id="01730-110">Channel</span></span>|<span data-ttu-id="01730-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="01730-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="01730-112">描述</span><span class="sxs-lookup"><span data-stu-id="01730-112">Description</span></span>  

 <span data-ttu-id="01730-113">表示 TransactionContextWorkItem 已完成。</span><span class="sxs-lookup"><span data-stu-id="01730-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="01730-114">訊息</span><span class="sxs-lookup"><span data-stu-id="01730-114">Message</span></span>  

 <span data-ttu-id="01730-115">已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 TransactionContextWorkItem。</span><span class="sxs-lookup"><span data-stu-id="01730-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="01730-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="01730-116">Details</span></span>  
  
|<span data-ttu-id="01730-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="01730-117">Data Item Name</span></span>|<span data-ttu-id="01730-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="01730-118">Data Item Type</span></span>|<span data-ttu-id="01730-119">描述</span><span class="sxs-lookup"><span data-stu-id="01730-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="01730-120">活動</span><span class="sxs-lookup"><span data-stu-id="01730-120">Activity</span></span>|<span data-ttu-id="01730-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="01730-121">xs:string</span></span>|<span data-ttu-id="01730-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="01730-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="01730-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="01730-123">DisplayName</span></span>|<span data-ttu-id="01730-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="01730-124">xs:string</span></span>|<span data-ttu-id="01730-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="01730-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="01730-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="01730-126">InstanceId</span></span>|<span data-ttu-id="01730-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="01730-127">xs:string</span></span>|<span data-ttu-id="01730-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="01730-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="01730-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="01730-129">AppDomain</span></span>|<span data-ttu-id="01730-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="01730-130">xs:string</span></span>|<span data-ttu-id="01730-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="01730-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
