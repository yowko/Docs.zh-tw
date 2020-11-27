---
title: 1036 - RuntimeTransactionCompletionRequested
ms.date: 03/30/2017
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
ms.openlocfilehash: 96ea253fd61652a3719eaf8b1a4d31aa88337eeb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294257"
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="73c6b-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="73c6b-102">1036 - RuntimeTransactionCompletionRequested</span></span>

## <a name="properties"></a><span data-ttu-id="73c6b-103">屬性</span><span class="sxs-lookup"><span data-stu-id="73c6b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="73c6b-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="73c6b-104">ID</span></span>|<span data-ttu-id="73c6b-105">1036</span><span class="sxs-lookup"><span data-stu-id="73c6b-105">1036</span></span>|  
|<span data-ttu-id="73c6b-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="73c6b-106">Keywords</span></span>|<span data-ttu-id="73c6b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="73c6b-107">WFRuntime</span></span>|  
|<span data-ttu-id="73c6b-108">層級</span><span class="sxs-lookup"><span data-stu-id="73c6b-108">Level</span></span>|<span data-ttu-id="73c6b-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="73c6b-109">Verbose</span></span>|  
|<span data-ttu-id="73c6b-110">通路</span><span class="sxs-lookup"><span data-stu-id="73c6b-110">Channel</span></span>|<span data-ttu-id="73c6b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="73c6b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="73c6b-112">描述</span><span class="sxs-lookup"><span data-stu-id="73c6b-112">Description</span></span>  

 <span data-ttu-id="73c6b-113">表示活動已排程執行階段交易的完成。</span><span class="sxs-lookup"><span data-stu-id="73c6b-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="73c6b-114">訊息</span><span class="sxs-lookup"><span data-stu-id="73c6b-114">Message</span></span>  

 <span data-ttu-id="73c6b-115">活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 已排程完成執行階段異動。</span><span class="sxs-lookup"><span data-stu-id="73c6b-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="73c6b-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="73c6b-116">Details</span></span>  
  
|<span data-ttu-id="73c6b-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="73c6b-117">Data Item Name</span></span>|<span data-ttu-id="73c6b-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="73c6b-118">Data Item Type</span></span>|<span data-ttu-id="73c6b-119">描述</span><span class="sxs-lookup"><span data-stu-id="73c6b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="73c6b-120">活動</span><span class="sxs-lookup"><span data-stu-id="73c6b-120">Activity</span></span>|<span data-ttu-id="73c6b-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="73c6b-121">xs:string</span></span>|<span data-ttu-id="73c6b-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="73c6b-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="73c6b-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="73c6b-123">DisplayName</span></span>|<span data-ttu-id="73c6b-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="73c6b-124">xs:string</span></span>|<span data-ttu-id="73c6b-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="73c6b-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="73c6b-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="73c6b-126">InstanceId</span></span>|<span data-ttu-id="73c6b-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="73c6b-127">xs:string</span></span>|<span data-ttu-id="73c6b-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="73c6b-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="73c6b-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="73c6b-129">AppDomain</span></span>|<span data-ttu-id="73c6b-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="73c6b-130">xs:string</span></span>|<span data-ttu-id="73c6b-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="73c6b-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
