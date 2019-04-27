---
title: 1036 - RuntimeTransactionCompletionRequested
ms.date: 03/30/2017
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
ms.openlocfilehash: 649ba542a9ed2f330ac71e447602d637530dc601
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924835"
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="14031-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="14031-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="14031-103">屬性</span><span class="sxs-lookup"><span data-stu-id="14031-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14031-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="14031-104">ID</span></span>|<span data-ttu-id="14031-105">1036</span><span class="sxs-lookup"><span data-stu-id="14031-105">1036</span></span>|  
|<span data-ttu-id="14031-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="14031-106">Keywords</span></span>|<span data-ttu-id="14031-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="14031-107">WFRuntime</span></span>|  
|<span data-ttu-id="14031-108">層級</span><span class="sxs-lookup"><span data-stu-id="14031-108">Level</span></span>|<span data-ttu-id="14031-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="14031-109">Verbose</span></span>|  
|<span data-ttu-id="14031-110">通道</span><span class="sxs-lookup"><span data-stu-id="14031-110">Channel</span></span>|<span data-ttu-id="14031-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="14031-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="14031-112">描述</span><span class="sxs-lookup"><span data-stu-id="14031-112">Description</span></span>  
 <span data-ttu-id="14031-113">表示活動已排程執行階段交易的完成。</span><span class="sxs-lookup"><span data-stu-id="14031-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="14031-114">訊息</span><span class="sxs-lookup"><span data-stu-id="14031-114">Message</span></span>  
 <span data-ttu-id="14031-115">活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 已排程完成執行階段異動。</span><span class="sxs-lookup"><span data-stu-id="14031-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="14031-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="14031-116">Details</span></span>  
  
|<span data-ttu-id="14031-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="14031-117">Data Item Name</span></span>|<span data-ttu-id="14031-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="14031-118">Data Item Type</span></span>|<span data-ttu-id="14031-119">描述</span><span class="sxs-lookup"><span data-stu-id="14031-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="14031-120">活動</span><span class="sxs-lookup"><span data-stu-id="14031-120">Activity</span></span>|<span data-ttu-id="14031-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="14031-121">xs:string</span></span>|<span data-ttu-id="14031-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="14031-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="14031-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="14031-123">DisplayName</span></span>|<span data-ttu-id="14031-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="14031-124">xs:string</span></span>|<span data-ttu-id="14031-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="14031-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="14031-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="14031-126">InstanceId</span></span>|<span data-ttu-id="14031-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="14031-127">xs:string</span></span>|<span data-ttu-id="14031-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="14031-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="14031-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="14031-129">AppDomain</span></span>|<span data-ttu-id="14031-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="14031-130">xs:string</span></span>|<span data-ttu-id="14031-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="14031-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
