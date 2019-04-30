---
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: d644c25ec2dee06eea4a5fb66c30792bb650f252
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945960"
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="06571-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="06571-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="06571-103">屬性</span><span class="sxs-lookup"><span data-stu-id="06571-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="06571-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="06571-104">ID</span></span>|<span data-ttu-id="06571-105">57398</span><span class="sxs-lookup"><span data-stu-id="06571-105">57398</span></span>|  
|<span data-ttu-id="06571-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="06571-106">Keywords</span></span>|<span data-ttu-id="06571-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="06571-107">WFServices</span></span>|  
|<span data-ttu-id="06571-108">層級</span><span class="sxs-lookup"><span data-stu-id="06571-108">Level</span></span>|<span data-ttu-id="06571-109">警告</span><span class="sxs-lookup"><span data-stu-id="06571-109">Warning</span></span>|  
|<span data-ttu-id="06571-110">通道</span><span class="sxs-lookup"><span data-stu-id="06571-110">Channel</span></span>|<span data-ttu-id="06571-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="06571-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="06571-112">描述</span><span class="sxs-lookup"><span data-stu-id="06571-112">Description</span></span>  
 <span data-ttu-id="06571-113">表示系統已到達針對 'MaxConcurrentInstances' 節流所設定的限制。</span><span class="sxs-lookup"><span data-stu-id="06571-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="06571-114">訊息</span><span class="sxs-lookup"><span data-stu-id="06571-114">Message</span></span>  
 <span data-ttu-id="06571-115">系統已到達針對 'MaxConcurrentInstances' 節流所設定的限制。</span><span class="sxs-lookup"><span data-stu-id="06571-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="06571-116">此節流的限制設為 %1。</span><span class="sxs-lookup"><span data-stu-id="06571-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="06571-117">若要變更節流值，請修改 serviceThrottle 元素中的屬性 'maxConcurrentInstances'，或修改行為 ServiceThrottlingBehavior 的 'MaxConcurrentInstances' 屬性。</span><span class="sxs-lookup"><span data-stu-id="06571-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="06571-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="06571-118">Details</span></span>  
  
|<span data-ttu-id="06571-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="06571-119">Data Item Name</span></span>|<span data-ttu-id="06571-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="06571-120">Data Item Type</span></span>|<span data-ttu-id="06571-121">描述</span><span class="sxs-lookup"><span data-stu-id="06571-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="06571-122">名稱</span><span class="sxs-lookup"><span data-stu-id="06571-122">Name</span></span>|<span data-ttu-id="06571-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="06571-123">xs:string</span></span>|<span data-ttu-id="06571-124">項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="06571-124">The name of the item.</span></span>|  
|<span data-ttu-id="06571-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="06571-125">AppDomain</span></span>|<span data-ttu-id="06571-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="06571-126">xs:string</span></span>|<span data-ttu-id="06571-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="06571-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
