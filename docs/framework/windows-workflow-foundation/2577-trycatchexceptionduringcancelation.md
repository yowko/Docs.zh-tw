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
ms.openlocfilehash: 11781bcab37a5034f3bbfadf2c50cbc1c6d378a2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="3d527-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="3d527-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="3d527-103">屬性</span><span class="sxs-lookup"><span data-stu-id="3d527-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3d527-104">ID</span><span class="sxs-lookup"><span data-stu-id="3d527-104">ID</span></span>|<span data-ttu-id="3d527-105">2577</span><span class="sxs-lookup"><span data-stu-id="3d527-105">2577</span></span>|  
|<span data-ttu-id="3d527-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="3d527-106">Keywords</span></span>|<span data-ttu-id="3d527-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="3d527-107">WFActivities</span></span>|  
|<span data-ttu-id="3d527-108">層級</span><span class="sxs-lookup"><span data-stu-id="3d527-108">Level</span></span>|<span data-ttu-id="3d527-109">警告</span><span class="sxs-lookup"><span data-stu-id="3d527-109">Warning</span></span>|  
|<span data-ttu-id="3d527-110">通道</span><span class="sxs-lookup"><span data-stu-id="3d527-110">Channel</span></span>|<span data-ttu-id="3d527-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3d527-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3d527-112">描述</span><span class="sxs-lookup"><span data-stu-id="3d527-112">Description</span></span>  
 <span data-ttu-id="3d527-113">表示 TryCatch 活動的子活動在取消期間擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3d527-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3d527-114">訊息</span><span class="sxs-lookup"><span data-stu-id="3d527-114">Message</span></span>  
 <span data-ttu-id="3d527-115">TryCatch 活動 '%1' 的子活動在取消期間擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3d527-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3d527-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3d527-116">Details</span></span>  
  
|<span data-ttu-id="3d527-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="3d527-117">Data Item Name</span></span>|<span data-ttu-id="3d527-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="3d527-118">Data Item Type</span></span>|<span data-ttu-id="3d527-119">描述</span><span class="sxs-lookup"><span data-stu-id="3d527-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3d527-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="3d527-120">DisplayName</span></span>|<span data-ttu-id="3d527-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="3d527-121">xs:string</span></span>|<span data-ttu-id="3d527-122">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="3d527-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="3d527-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3d527-123">AppDomain</span></span>|<span data-ttu-id="3d527-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="3d527-124">xs:string</span></span>|<span data-ttu-id="3d527-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="3d527-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
