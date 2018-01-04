---
title: 4210 - SqlExceptionCaught
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fbcb566574e38e3c4688c16bd29a33ff7048bfa4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="4210---sqlexceptioncaught"></a><span data-ttu-id="3a1e6-102">4210 - SqlExceptionCaught</span><span class="sxs-lookup"><span data-stu-id="3a1e6-102">4210 - SqlExceptionCaught</span></span>
## <a name="properties"></a><span data-ttu-id="3a1e6-103">屬性</span><span class="sxs-lookup"><span data-stu-id="3a1e6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3a1e6-104">ID</span><span class="sxs-lookup"><span data-stu-id="3a1e6-104">ID</span></span>|<span data-ttu-id="3a1e6-105">4210</span><span class="sxs-lookup"><span data-stu-id="3a1e6-105">4210</span></span>|  
|<span data-ttu-id="3a1e6-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="3a1e6-106">Keywords</span></span>|<span data-ttu-id="3a1e6-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="3a1e6-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="3a1e6-108">層級</span><span class="sxs-lookup"><span data-stu-id="3a1e6-108">Level</span></span>|<span data-ttu-id="3a1e6-109">警告</span><span class="sxs-lookup"><span data-stu-id="3a1e6-109">Warning</span></span>|  
|<span data-ttu-id="3a1e6-110">通道</span><span class="sxs-lookup"><span data-stu-id="3a1e6-110">Channel</span></span>|<span data-ttu-id="3a1e6-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3a1e6-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3a1e6-112">描述</span><span class="sxs-lookup"><span data-stu-id="3a1e6-112">Description</span></span>  
 <span data-ttu-id="3a1e6-113">表示已攔截到 SQL 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3a1e6-113">Indicates a SQL exception was caught.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3a1e6-114">訊息</span><span class="sxs-lookup"><span data-stu-id="3a1e6-114">Message</span></span>  
 <span data-ttu-id="3a1e6-115">攔截到 SQL 例外狀況編號 %1 訊息 %2。</span><span class="sxs-lookup"><span data-stu-id="3a1e6-115">Caught SQL Exception number %1 message %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3a1e6-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3a1e6-116">Details</span></span>  
  
|<span data-ttu-id="3a1e6-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="3a1e6-117">Data Item Name</span></span>|<span data-ttu-id="3a1e6-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="3a1e6-118">Data Item Type</span></span>|<span data-ttu-id="3a1e6-119">描述</span><span class="sxs-lookup"><span data-stu-id="3a1e6-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3a1e6-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="3a1e6-120">ErrorNumber</span></span>|<span data-ttu-id="3a1e6-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="3a1e6-121">xs:string</span></span>|<span data-ttu-id="3a1e6-122">SQL 錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="3a1e6-122">The SQL error number.</span></span>|  
|<span data-ttu-id="3a1e6-123">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="3a1e6-123">ExceptionMessage</span></span>|<span data-ttu-id="3a1e6-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="3a1e6-124">xs:string</span></span>|<span data-ttu-id="3a1e6-125">SQL 例外狀況的訊息。</span><span class="sxs-lookup"><span data-stu-id="3a1e6-125">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="3a1e6-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3a1e6-126">AppDomain</span></span>|<span data-ttu-id="3a1e6-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="3a1e6-127">xs:string</span></span>|<span data-ttu-id="3a1e6-128">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="3a1e6-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
