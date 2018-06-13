---
title: 1036 - RuntimeTransactionCompletionRequested
ms.date: 03/30/2017
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
ms.openlocfilehash: 649ba542a9ed2f330ac71e447602d637530dc601
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510389"
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="375b1-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="375b1-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="375b1-103">屬性</span><span class="sxs-lookup"><span data-stu-id="375b1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="375b1-104">ID</span><span class="sxs-lookup"><span data-stu-id="375b1-104">ID</span></span>|<span data-ttu-id="375b1-105">1036</span><span class="sxs-lookup"><span data-stu-id="375b1-105">1036</span></span>|  
|<span data-ttu-id="375b1-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="375b1-106">Keywords</span></span>|<span data-ttu-id="375b1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="375b1-107">WFRuntime</span></span>|  
|<span data-ttu-id="375b1-108">層級</span><span class="sxs-lookup"><span data-stu-id="375b1-108">Level</span></span>|<span data-ttu-id="375b1-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="375b1-109">Verbose</span></span>|  
|<span data-ttu-id="375b1-110">通道</span><span class="sxs-lookup"><span data-stu-id="375b1-110">Channel</span></span>|<span data-ttu-id="375b1-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="375b1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="375b1-112">描述</span><span class="sxs-lookup"><span data-stu-id="375b1-112">Description</span></span>  
 <span data-ttu-id="375b1-113">表示活動已排程執行階段交易的完成。</span><span class="sxs-lookup"><span data-stu-id="375b1-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="375b1-114">訊息</span><span class="sxs-lookup"><span data-stu-id="375b1-114">Message</span></span>  
 <span data-ttu-id="375b1-115">活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 已排程完成執行階段交易。</span><span class="sxs-lookup"><span data-stu-id="375b1-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="375b1-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="375b1-116">Details</span></span>  
  
|<span data-ttu-id="375b1-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="375b1-117">Data Item Name</span></span>|<span data-ttu-id="375b1-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="375b1-118">Data Item Type</span></span>|<span data-ttu-id="375b1-119">描述</span><span class="sxs-lookup"><span data-stu-id="375b1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="375b1-120">活動</span><span class="sxs-lookup"><span data-stu-id="375b1-120">Activity</span></span>|<span data-ttu-id="375b1-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="375b1-121">xs:string</span></span>|<span data-ttu-id="375b1-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="375b1-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="375b1-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="375b1-123">DisplayName</span></span>|<span data-ttu-id="375b1-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="375b1-124">xs:string</span></span>|<span data-ttu-id="375b1-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="375b1-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="375b1-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="375b1-126">InstanceId</span></span>|<span data-ttu-id="375b1-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="375b1-127">xs:string</span></span>|<span data-ttu-id="375b1-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="375b1-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="375b1-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="375b1-129">AppDomain</span></span>|<span data-ttu-id="375b1-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="375b1-130">xs:string</span></span>|<span data-ttu-id="375b1-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="375b1-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
