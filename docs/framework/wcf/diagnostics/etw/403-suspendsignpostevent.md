---
title: 403 - SuspendSignpostEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb2e6f29-e556-47b4-b4c1-acd6b8879702
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 10e745ded72caa493119d7e27a5c777b2185b96e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="403---suspendsignpostevent"></a><span data-ttu-id="389db-102">403 - SuspendSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="389db-102">403 - SuspendSignpostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="389db-103">屬性</span><span class="sxs-lookup"><span data-stu-id="389db-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="389db-104">ID</span><span class="sxs-lookup"><span data-stu-id="389db-104">ID</span></span>|<span data-ttu-id="389db-105">403</span><span class="sxs-lookup"><span data-stu-id="389db-105">403</span></span>|  
|<span data-ttu-id="389db-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="389db-106">Keywords</span></span>|<span data-ttu-id="389db-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="389db-107">Troubleshooting</span></span>|  
|<span data-ttu-id="389db-108">層級</span><span class="sxs-lookup"><span data-stu-id="389db-108">Level</span></span>|<span data-ttu-id="389db-109">資訊</span><span class="sxs-lookup"><span data-stu-id="389db-109">Information</span></span>|  
|<span data-ttu-id="389db-110">通道</span><span class="sxs-lookup"><span data-stu-id="389db-110">Channel</span></span>|<span data-ttu-id="389db-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="389db-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="389db-112">描述</span><span class="sxs-lookup"><span data-stu-id="389db-112">Description</span></span>  
 <span data-ttu-id="389db-113">此活動會標記端對端活動的暫停。</span><span class="sxs-lookup"><span data-stu-id="389db-113">This event marks the suspension of an end-to-end activity.</span></span> <span data-ttu-id="389db-114">其中包含了活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="389db-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="389db-115">訊息</span><span class="sxs-lookup"><span data-stu-id="389db-115">Message</span></span>  
 <span data-ttu-id="389db-116">活動界限。</span><span class="sxs-lookup"><span data-stu-id="389db-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="389db-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="389db-117">Details</span></span>  
  
|<span data-ttu-id="389db-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="389db-118">Data Item Name</span></span>|<span data-ttu-id="389db-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="389db-119">Data Item Type</span></span>|<span data-ttu-id="389db-120">描述</span><span class="sxs-lookup"><span data-stu-id="389db-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="389db-121">延伸資料</span><span class="sxs-lookup"><span data-stu-id="389db-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="389db-122">活動名稱。</span><span class="sxs-lookup"><span data-stu-id="389db-122">The name of the activity.</span></span>|  
|<span data-ttu-id="389db-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="389db-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="389db-124">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="389db-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
