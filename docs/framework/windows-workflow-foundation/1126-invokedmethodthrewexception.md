---
title: 1126 - InvokedMethodThrewException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b11c2f167ce7afce992cddb2f32f840212d4ac8d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="a6cc5-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="a6cc5-102">1126 - InvokedMethodThrewException</span></span>
## <a name="properties"></a><span data-ttu-id="a6cc5-103">屬性</span><span class="sxs-lookup"><span data-stu-id="a6cc5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a6cc5-104">ID</span><span class="sxs-lookup"><span data-stu-id="a6cc5-104">ID</span></span>|<span data-ttu-id="a6cc5-105">1126</span><span class="sxs-lookup"><span data-stu-id="a6cc5-105">1126</span></span>|  
|<span data-ttu-id="a6cc5-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a6cc5-106">Keywords</span></span>|<span data-ttu-id="a6cc5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a6cc5-107">WFRuntime</span></span>|  
|<span data-ttu-id="a6cc5-108">層級</span><span class="sxs-lookup"><span data-stu-id="a6cc5-108">Level</span></span>|<span data-ttu-id="a6cc5-109">資訊</span><span class="sxs-lookup"><span data-stu-id="a6cc5-109">Information</span></span>|  
|<span data-ttu-id="a6cc5-110">通道</span><span class="sxs-lookup"><span data-stu-id="a6cc5-110">Channel</span></span>|<span data-ttu-id="a6cc5-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="a6cc5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a6cc5-112">描述</span><span class="sxs-lookup"><span data-stu-id="a6cc5-112">Description</span></span>  
 <span data-ttu-id="a6cc5-113">表示 InvokeMethod 活動所呼叫的方法擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a6cc5-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a6cc5-114">訊息</span><span class="sxs-lookup"><span data-stu-id="a6cc5-114">Message</span></span>  
 <span data-ttu-id="a6cc5-115">在活動 '%1' 呼叫的方法中發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a6cc5-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="a6cc5-116">%2</span><span class="sxs-lookup"><span data-stu-id="a6cc5-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="a6cc5-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a6cc5-117">Details</span></span>  
  
|<span data-ttu-id="a6cc5-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="a6cc5-118">Data Item Name</span></span>|<span data-ttu-id="a6cc5-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="a6cc5-119">Data Item Type</span></span>|<span data-ttu-id="a6cc5-120">描述</span><span class="sxs-lookup"><span data-stu-id="a6cc5-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a6cc5-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="a6cc5-121">InvokeMethod</span></span>|<span data-ttu-id="a6cc5-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="a6cc5-122">xs:string</span></span>|<span data-ttu-id="a6cc5-123">InvokeMethod 活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="a6cc5-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="a6cc5-124">例外狀況</span><span class="sxs-lookup"><span data-stu-id="a6cc5-124">Exception</span></span>|<span data-ttu-id="a6cc5-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="a6cc5-125">xs:string</span></span>|<span data-ttu-id="a6cc5-126">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="a6cc5-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="a6cc5-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a6cc5-127">AppDomain</span></span>|<span data-ttu-id="a6cc5-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="a6cc5-128">xs:string</span></span>|<span data-ttu-id="a6cc5-129">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="a6cc5-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
