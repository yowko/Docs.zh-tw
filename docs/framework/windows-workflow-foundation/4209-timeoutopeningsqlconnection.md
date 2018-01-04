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
ms.workload: dotnet
ms.openlocfilehash: 7528c967cbd88f00af448d6163c10e807f603bc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="77778-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="77778-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="77778-103">屬性</span><span class="sxs-lookup"><span data-stu-id="77778-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77778-104">ID</span><span class="sxs-lookup"><span data-stu-id="77778-104">ID</span></span>|<span data-ttu-id="77778-105">4209</span><span class="sxs-lookup"><span data-stu-id="77778-105">4209</span></span>|  
|<span data-ttu-id="77778-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="77778-106">Keywords</span></span>|<span data-ttu-id="77778-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="77778-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="77778-108">層級</span><span class="sxs-lookup"><span data-stu-id="77778-108">Level</span></span>|<span data-ttu-id="77778-109">錯誤</span><span class="sxs-lookup"><span data-stu-id="77778-109">Error</span></span>|  
|<span data-ttu-id="77778-110">通道</span><span class="sxs-lookup"><span data-stu-id="77778-110">Channel</span></span>|<span data-ttu-id="77778-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="77778-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="77778-112">描述</span><span class="sxs-lookup"><span data-stu-id="77778-112">Description</span></span>  
 <span data-ttu-id="77778-113">表示嘗試開啟 SQL 連接時，發生逾時。</span><span class="sxs-lookup"><span data-stu-id="77778-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="77778-114">訊息</span><span class="sxs-lookup"><span data-stu-id="77778-114">Message</span></span>  
 <span data-ttu-id="77778-115">嘗試開啟 SQL 連接時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="77778-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="77778-116">無法在分配的逾時 %1 內完成作業。</span><span class="sxs-lookup"><span data-stu-id="77778-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="77778-117">分配給此作業的時間可能是較長逾時的一部分。</span><span class="sxs-lookup"><span data-stu-id="77778-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="77778-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="77778-118">Details</span></span>  
  
|<span data-ttu-id="77778-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="77778-119">Data Item Name</span></span>|<span data-ttu-id="77778-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="77778-120">Data Item Type</span></span>|<span data-ttu-id="77778-121">描述</span><span class="sxs-lookup"><span data-stu-id="77778-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="77778-122">等候逾時</span><span class="sxs-lookup"><span data-stu-id="77778-122">Timeout</span></span>|<span data-ttu-id="77778-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="77778-123">xs:string</span></span>|<span data-ttu-id="77778-124">開啟 SQL 連接的逾時值。</span><span class="sxs-lookup"><span data-stu-id="77778-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="77778-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="77778-125">AppDomain</span></span>|<span data-ttu-id="77778-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="77778-126">xs:string</span></span>|<span data-ttu-id="77778-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="77778-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
