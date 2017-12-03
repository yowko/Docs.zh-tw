---
title: 4209 - TimeoutOpeningSqlConnection
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 86d971a2e5f1257281c453e7eb0c2dc1755098d8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="73f10-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="73f10-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="73f10-103">屬性</span><span class="sxs-lookup"><span data-stu-id="73f10-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="73f10-104">ID</span><span class="sxs-lookup"><span data-stu-id="73f10-104">ID</span></span>|<span data-ttu-id="73f10-105">4209</span><span class="sxs-lookup"><span data-stu-id="73f10-105">4209</span></span>|  
|<span data-ttu-id="73f10-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="73f10-106">Keywords</span></span>|<span data-ttu-id="73f10-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="73f10-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="73f10-108">層級</span><span class="sxs-lookup"><span data-stu-id="73f10-108">Level</span></span>|<span data-ttu-id="73f10-109">錯誤</span><span class="sxs-lookup"><span data-stu-id="73f10-109">Error</span></span>|  
|<span data-ttu-id="73f10-110">通道</span><span class="sxs-lookup"><span data-stu-id="73f10-110">Channel</span></span>|<span data-ttu-id="73f10-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="73f10-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="73f10-112">描述</span><span class="sxs-lookup"><span data-stu-id="73f10-112">Description</span></span>  
 <span data-ttu-id="73f10-113">表示嘗試開啟 SQL 連接時，發生逾時。</span><span class="sxs-lookup"><span data-stu-id="73f10-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="73f10-114">訊息</span><span class="sxs-lookup"><span data-stu-id="73f10-114">Message</span></span>  
 <span data-ttu-id="73f10-115">嘗試開啟 SQL 連接時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="73f10-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="73f10-116">無法在分配的逾時 %1 內完成作業。</span><span class="sxs-lookup"><span data-stu-id="73f10-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="73f10-117">分配給此作業的時間可能是較長逾時的一部分。</span><span class="sxs-lookup"><span data-stu-id="73f10-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="73f10-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="73f10-118">Details</span></span>  
  
|<span data-ttu-id="73f10-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="73f10-119">Data Item Name</span></span>|<span data-ttu-id="73f10-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="73f10-120">Data Item Type</span></span>|<span data-ttu-id="73f10-121">描述</span><span class="sxs-lookup"><span data-stu-id="73f10-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="73f10-122">等候逾時</span><span class="sxs-lookup"><span data-stu-id="73f10-122">Timeout</span></span>|<span data-ttu-id="73f10-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="73f10-123">xs:string</span></span>|<span data-ttu-id="73f10-124">開啟 SQL 連接的逾時值。</span><span class="sxs-lookup"><span data-stu-id="73f10-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="73f10-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="73f10-125">AppDomain</span></span>|<span data-ttu-id="73f10-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="73f10-126">xs:string</span></span>|<span data-ttu-id="73f10-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="73f10-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
