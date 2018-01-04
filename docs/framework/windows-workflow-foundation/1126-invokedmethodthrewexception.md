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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5dc752a5c9d5bebe39a4d4be2c3642333aa041de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="37141-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="37141-102">1126 - InvokedMethodThrewException</span></span>
## <a name="properties"></a><span data-ttu-id="37141-103">屬性</span><span class="sxs-lookup"><span data-stu-id="37141-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="37141-104">ID</span><span class="sxs-lookup"><span data-stu-id="37141-104">ID</span></span>|<span data-ttu-id="37141-105">1126</span><span class="sxs-lookup"><span data-stu-id="37141-105">1126</span></span>|  
|<span data-ttu-id="37141-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="37141-106">Keywords</span></span>|<span data-ttu-id="37141-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="37141-107">WFRuntime</span></span>|  
|<span data-ttu-id="37141-108">層級</span><span class="sxs-lookup"><span data-stu-id="37141-108">Level</span></span>|<span data-ttu-id="37141-109">資訊</span><span class="sxs-lookup"><span data-stu-id="37141-109">Information</span></span>|  
|<span data-ttu-id="37141-110">通道</span><span class="sxs-lookup"><span data-stu-id="37141-110">Channel</span></span>|<span data-ttu-id="37141-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="37141-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="37141-112">描述</span><span class="sxs-lookup"><span data-stu-id="37141-112">Description</span></span>  
 <span data-ttu-id="37141-113">表示 InvokeMethod 活動所呼叫的方法擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="37141-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="37141-114">訊息</span><span class="sxs-lookup"><span data-stu-id="37141-114">Message</span></span>  
 <span data-ttu-id="37141-115">在活動 '%1' 呼叫的方法中發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="37141-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="37141-116">%2</span><span class="sxs-lookup"><span data-stu-id="37141-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="37141-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="37141-117">Details</span></span>  
  
|<span data-ttu-id="37141-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="37141-118">Data Item Name</span></span>|<span data-ttu-id="37141-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="37141-119">Data Item Type</span></span>|<span data-ttu-id="37141-120">描述</span><span class="sxs-lookup"><span data-stu-id="37141-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="37141-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="37141-121">InvokeMethod</span></span>|<span data-ttu-id="37141-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="37141-122">xs:string</span></span>|<span data-ttu-id="37141-123">InvokeMethod 活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="37141-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="37141-124">例外狀況</span><span class="sxs-lookup"><span data-stu-id="37141-124">Exception</span></span>|<span data-ttu-id="37141-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="37141-125">xs:string</span></span>|<span data-ttu-id="37141-126">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="37141-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="37141-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="37141-127">AppDomain</span></span>|<span data-ttu-id="37141-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="37141-128">xs:string</span></span>|<span data-ttu-id="37141-129">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="37141-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
