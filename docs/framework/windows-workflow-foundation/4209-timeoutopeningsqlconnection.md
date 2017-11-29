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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f87e99585ccbdf3b89653f026860e7b66dc6c9b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="58a58-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="58a58-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="58a58-103">屬性</span><span class="sxs-lookup"><span data-stu-id="58a58-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="58a58-104">ID</span><span class="sxs-lookup"><span data-stu-id="58a58-104">ID</span></span>|<span data-ttu-id="58a58-105">4209</span><span class="sxs-lookup"><span data-stu-id="58a58-105">4209</span></span>|  
|<span data-ttu-id="58a58-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="58a58-106">Keywords</span></span>|<span data-ttu-id="58a58-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="58a58-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="58a58-108">層級</span><span class="sxs-lookup"><span data-stu-id="58a58-108">Level</span></span>|<span data-ttu-id="58a58-109">錯誤</span><span class="sxs-lookup"><span data-stu-id="58a58-109">Error</span></span>|  
|<span data-ttu-id="58a58-110">通道</span><span class="sxs-lookup"><span data-stu-id="58a58-110">Channel</span></span>|<span data-ttu-id="58a58-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="58a58-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="58a58-112">描述</span><span class="sxs-lookup"><span data-stu-id="58a58-112">Description</span></span>  
 <span data-ttu-id="58a58-113">表示嘗試開啟 SQL 連接時，發生逾時。</span><span class="sxs-lookup"><span data-stu-id="58a58-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="58a58-114">訊息</span><span class="sxs-lookup"><span data-stu-id="58a58-114">Message</span></span>  
 <span data-ttu-id="58a58-115">嘗試開啟 SQL 連接時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="58a58-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="58a58-116">無法在分配的逾時 %1 內完成作業。</span><span class="sxs-lookup"><span data-stu-id="58a58-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="58a58-117">分配給此作業的時間可能是較長逾時的一部分。</span><span class="sxs-lookup"><span data-stu-id="58a58-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="58a58-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="58a58-118">Details</span></span>  
  
|<span data-ttu-id="58a58-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="58a58-119">Data Item Name</span></span>|<span data-ttu-id="58a58-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="58a58-120">Data Item Type</span></span>|<span data-ttu-id="58a58-121">描述</span><span class="sxs-lookup"><span data-stu-id="58a58-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="58a58-122">等候逾時</span><span class="sxs-lookup"><span data-stu-id="58a58-122">Timeout</span></span>|<span data-ttu-id="58a58-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="58a58-123">xs:string</span></span>|<span data-ttu-id="58a58-124">開啟 SQL 連接的逾時值。</span><span class="sxs-lookup"><span data-stu-id="58a58-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="58a58-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="58a58-125">AppDomain</span></span>|<span data-ttu-id="58a58-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="58a58-126">xs:string</span></span>|<span data-ttu-id="58a58-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="58a58-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
