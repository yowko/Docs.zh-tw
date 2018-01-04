---
title: 2577 - TryCatchExceptionDuringCancelation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1e851a50c9677b2f10ea3478c3599706007d4d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="5e55e-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="5e55e-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="5e55e-103">屬性</span><span class="sxs-lookup"><span data-stu-id="5e55e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5e55e-104">ID</span><span class="sxs-lookup"><span data-stu-id="5e55e-104">ID</span></span>|<span data-ttu-id="5e55e-105">2577</span><span class="sxs-lookup"><span data-stu-id="5e55e-105">2577</span></span>|  
|<span data-ttu-id="5e55e-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="5e55e-106">Keywords</span></span>|<span data-ttu-id="5e55e-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="5e55e-107">WFActivities</span></span>|  
|<span data-ttu-id="5e55e-108">層級</span><span class="sxs-lookup"><span data-stu-id="5e55e-108">Level</span></span>|<span data-ttu-id="5e55e-109">警告</span><span class="sxs-lookup"><span data-stu-id="5e55e-109">Warning</span></span>|  
|<span data-ttu-id="5e55e-110">通道</span><span class="sxs-lookup"><span data-stu-id="5e55e-110">Channel</span></span>|<span data-ttu-id="5e55e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="5e55e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5e55e-112">描述</span><span class="sxs-lookup"><span data-stu-id="5e55e-112">Description</span></span>  
 <span data-ttu-id="5e55e-113">表示 TryCatch 活動的子活動在取消期間擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5e55e-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5e55e-114">訊息</span><span class="sxs-lookup"><span data-stu-id="5e55e-114">Message</span></span>  
 <span data-ttu-id="5e55e-115">TryCatch 活動 '%1' 的子活動在取消期間擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5e55e-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5e55e-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5e55e-116">Details</span></span>  
  
|<span data-ttu-id="5e55e-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="5e55e-117">Data Item Name</span></span>|<span data-ttu-id="5e55e-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="5e55e-118">Data Item Type</span></span>|<span data-ttu-id="5e55e-119">描述</span><span class="sxs-lookup"><span data-stu-id="5e55e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5e55e-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="5e55e-120">DisplayName</span></span>|<span data-ttu-id="5e55e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="5e55e-121">xs:string</span></span>|<span data-ttu-id="5e55e-122">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="5e55e-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="5e55e-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5e55e-123">AppDomain</span></span>|<span data-ttu-id="5e55e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="5e55e-124">xs:string</span></span>|<span data-ttu-id="5e55e-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="5e55e-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
