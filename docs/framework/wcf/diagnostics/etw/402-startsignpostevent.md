---
title: 402 - StartSignpostEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e5be126-765d-4ac9-88e7-008e9ef4f0e5
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0cd786f78336be50ad2ef5447f74b92b2abbdc7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="402---startsignpostevent"></a><span data-ttu-id="ddc67-102">402 - StartSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="ddc67-102">402 - StartSignpostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="ddc67-103">屬性</span><span class="sxs-lookup"><span data-stu-id="ddc67-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ddc67-104">ID</span><span class="sxs-lookup"><span data-stu-id="ddc67-104">ID</span></span>|<span data-ttu-id="ddc67-105">402</span><span class="sxs-lookup"><span data-stu-id="ddc67-105">402</span></span>|  
|<span data-ttu-id="ddc67-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="ddc67-106">Keywords</span></span>|<span data-ttu-id="ddc67-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="ddc67-107">Troubleshooting</span></span>|  
|<span data-ttu-id="ddc67-108">層級</span><span class="sxs-lookup"><span data-stu-id="ddc67-108">Level</span></span>|<span data-ttu-id="ddc67-109">資訊</span><span class="sxs-lookup"><span data-stu-id="ddc67-109">Information</span></span>|  
|<span data-ttu-id="ddc67-110">通道</span><span class="sxs-lookup"><span data-stu-id="ddc67-110">Channel</span></span>|<span data-ttu-id="ddc67-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="ddc67-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ddc67-112">描述</span><span class="sxs-lookup"><span data-stu-id="ddc67-112">Description</span></span>  
 <span data-ttu-id="ddc67-113">此活動會標記端對端活動的開始。</span><span class="sxs-lookup"><span data-stu-id="ddc67-113">This event marks the beginning of an end-to-end activity.</span></span> <span data-ttu-id="ddc67-114">其中包含了活動的名稱。</span><span class="sxs-lookup"><span data-stu-id="ddc67-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ddc67-115">訊息</span><span class="sxs-lookup"><span data-stu-id="ddc67-115">Message</span></span>  
 <span data-ttu-id="ddc67-116">活動界限。</span><span class="sxs-lookup"><span data-stu-id="ddc67-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ddc67-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ddc67-117">Details</span></span>  
  
|<span data-ttu-id="ddc67-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="ddc67-118">Data Item Name</span></span>|<span data-ttu-id="ddc67-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="ddc67-119">Data Item Type</span></span>|<span data-ttu-id="ddc67-120">描述</span><span class="sxs-lookup"><span data-stu-id="ddc67-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ddc67-121">延伸資料</span><span class="sxs-lookup"><span data-stu-id="ddc67-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="ddc67-122">活動名稱。</span><span class="sxs-lookup"><span data-stu-id="ddc67-122">The name of the activity.</span></span>|  
|<span data-ttu-id="ddc67-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ddc67-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ddc67-124">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="ddc67-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
