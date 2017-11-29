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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a4bc0d9ab45fe8e2f025c651fce137d6a4255bc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="e7c03-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="e7c03-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="e7c03-103">屬性</span><span class="sxs-lookup"><span data-stu-id="e7c03-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e7c03-104">ID</span><span class="sxs-lookup"><span data-stu-id="e7c03-104">ID</span></span>|<span data-ttu-id="e7c03-105">2577</span><span class="sxs-lookup"><span data-stu-id="e7c03-105">2577</span></span>|  
|<span data-ttu-id="e7c03-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="e7c03-106">Keywords</span></span>|<span data-ttu-id="e7c03-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="e7c03-107">WFActivities</span></span>|  
|<span data-ttu-id="e7c03-108">層級</span><span class="sxs-lookup"><span data-stu-id="e7c03-108">Level</span></span>|<span data-ttu-id="e7c03-109">警告</span><span class="sxs-lookup"><span data-stu-id="e7c03-109">Warning</span></span>|  
|<span data-ttu-id="e7c03-110">通道</span><span class="sxs-lookup"><span data-stu-id="e7c03-110">Channel</span></span>|<span data-ttu-id="e7c03-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e7c03-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e7c03-112">描述</span><span class="sxs-lookup"><span data-stu-id="e7c03-112">Description</span></span>  
 <span data-ttu-id="e7c03-113">表示 TryCatch 活動的子活動在取消期間擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e7c03-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e7c03-114">訊息</span><span class="sxs-lookup"><span data-stu-id="e7c03-114">Message</span></span>  
 <span data-ttu-id="e7c03-115">TryCatch 活動 '%1' 的子活動在取消期間擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e7c03-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e7c03-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e7c03-116">Details</span></span>  
  
|<span data-ttu-id="e7c03-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="e7c03-117">Data Item Name</span></span>|<span data-ttu-id="e7c03-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="e7c03-118">Data Item Type</span></span>|<span data-ttu-id="e7c03-119">描述</span><span class="sxs-lookup"><span data-stu-id="e7c03-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e7c03-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e7c03-120">DisplayName</span></span>|<span data-ttu-id="e7c03-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e7c03-121">xs:string</span></span>|<span data-ttu-id="e7c03-122">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="e7c03-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="e7c03-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e7c03-123">AppDomain</span></span>|<span data-ttu-id="e7c03-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e7c03-124">xs:string</span></span>|<span data-ttu-id="e7c03-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="e7c03-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
