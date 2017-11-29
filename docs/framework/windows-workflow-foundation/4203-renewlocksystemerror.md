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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 06d4695eb125475f41a94c7f2266df6d2c3f400d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="0c970-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="0c970-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="0c970-103">屬性</span><span class="sxs-lookup"><span data-stu-id="0c970-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0c970-104">ID</span><span class="sxs-lookup"><span data-stu-id="0c970-104">ID</span></span>|<span data-ttu-id="0c970-105">4203</span><span class="sxs-lookup"><span data-stu-id="0c970-105">4203</span></span>|  
|<span data-ttu-id="0c970-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="0c970-106">Keywords</span></span>|<span data-ttu-id="0c970-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="0c970-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="0c970-108">層級</span><span class="sxs-lookup"><span data-stu-id="0c970-108">Level</span></span>|<span data-ttu-id="0c970-109">錯誤</span><span class="sxs-lookup"><span data-stu-id="0c970-109">Error</span></span>|  
|<span data-ttu-id="0c970-110">通道</span><span class="sxs-lookup"><span data-stu-id="0c970-110">Channel</span></span>|<span data-ttu-id="0c970-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0c970-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0c970-112">描述</span><span class="sxs-lookup"><span data-stu-id="0c970-112">Description</span></span>  
 <span data-ttu-id="0c970-113">表示因為已超過鎖定期限或已刪除鎖定擁有人，所以 SQL 提供者無法延長鎖定期限。</span><span class="sxs-lookup"><span data-stu-id="0c970-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="0c970-114">SqlWorkflowInstanceStore 即將中止。</span><span class="sxs-lookup"><span data-stu-id="0c970-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0c970-115">訊息</span><span class="sxs-lookup"><span data-stu-id="0c970-115">Message</span></span>  
 <span data-ttu-id="0c970-116">無法延長鎖定期限，已超過鎖定期限或已刪除鎖定擁有人。</span><span class="sxs-lookup"><span data-stu-id="0c970-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="0c970-117">正在中止 SqlWorkflowInstanceStore。</span><span class="sxs-lookup"><span data-stu-id="0c970-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0c970-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0c970-118">Details</span></span>  
  
|<span data-ttu-id="0c970-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="0c970-119">Data Item Name</span></span>|<span data-ttu-id="0c970-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="0c970-120">Data Item Type</span></span>|<span data-ttu-id="0c970-121">描述</span><span class="sxs-lookup"><span data-stu-id="0c970-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0c970-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0c970-122">AppDomain</span></span>|<span data-ttu-id="0c970-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="0c970-123">xs:string</span></span>|<span data-ttu-id="0c970-124">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="0c970-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
