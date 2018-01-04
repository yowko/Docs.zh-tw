---
title: 4203 - RenewLockSystemError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8fabe6f2c023bf9b997d2a4e19b4a3755c93f408
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="dcdac-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="dcdac-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="dcdac-103">屬性</span><span class="sxs-lookup"><span data-stu-id="dcdac-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dcdac-104">ID</span><span class="sxs-lookup"><span data-stu-id="dcdac-104">ID</span></span>|<span data-ttu-id="dcdac-105">4203</span><span class="sxs-lookup"><span data-stu-id="dcdac-105">4203</span></span>|  
|<span data-ttu-id="dcdac-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="dcdac-106">Keywords</span></span>|<span data-ttu-id="dcdac-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="dcdac-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="dcdac-108">層級</span><span class="sxs-lookup"><span data-stu-id="dcdac-108">Level</span></span>|<span data-ttu-id="dcdac-109">錯誤</span><span class="sxs-lookup"><span data-stu-id="dcdac-109">Error</span></span>|  
|<span data-ttu-id="dcdac-110">通道</span><span class="sxs-lookup"><span data-stu-id="dcdac-110">Channel</span></span>|<span data-ttu-id="dcdac-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="dcdac-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dcdac-112">描述</span><span class="sxs-lookup"><span data-stu-id="dcdac-112">Description</span></span>  
 <span data-ttu-id="dcdac-113">表示因為已超過鎖定期限或已刪除鎖定擁有人，所以 SQL 提供者無法延長鎖定期限。</span><span class="sxs-lookup"><span data-stu-id="dcdac-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="dcdac-114">SqlWorkflowInstanceStore 即將中止。</span><span class="sxs-lookup"><span data-stu-id="dcdac-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dcdac-115">訊息</span><span class="sxs-lookup"><span data-stu-id="dcdac-115">Message</span></span>  
 <span data-ttu-id="dcdac-116">無法延長鎖定期限，已超過鎖定期限或已刪除鎖定擁有人。</span><span class="sxs-lookup"><span data-stu-id="dcdac-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="dcdac-117">正在中止 SqlWorkflowInstanceStore。</span><span class="sxs-lookup"><span data-stu-id="dcdac-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dcdac-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dcdac-118">Details</span></span>  
  
|<span data-ttu-id="dcdac-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="dcdac-119">Data Item Name</span></span>|<span data-ttu-id="dcdac-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="dcdac-120">Data Item Type</span></span>|<span data-ttu-id="dcdac-121">描述</span><span class="sxs-lookup"><span data-stu-id="dcdac-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dcdac-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="dcdac-122">AppDomain</span></span>|<span data-ttu-id="dcdac-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="dcdac-123">xs:string</span></span>|<span data-ttu-id="dcdac-124">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="dcdac-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
