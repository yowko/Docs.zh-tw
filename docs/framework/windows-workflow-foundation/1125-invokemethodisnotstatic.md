---
title: 1125 - InvokeMethodIsNotStatic
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 934c2947e86b429e9b990c273f22c0511f209a53
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="d19eb-102">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="d19eb-102">1125 - InvokeMethodIsNotStatic</span></span>
## <a name="properties"></a><span data-ttu-id="d19eb-103">屬性</span><span class="sxs-lookup"><span data-stu-id="d19eb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d19eb-104">ID</span><span class="sxs-lookup"><span data-stu-id="d19eb-104">ID</span></span>|<span data-ttu-id="d19eb-105">1125</span><span class="sxs-lookup"><span data-stu-id="d19eb-105">1125</span></span>|  
|<span data-ttu-id="d19eb-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="d19eb-106">Keywords</span></span>|<span data-ttu-id="d19eb-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d19eb-107">WFRuntime</span></span>|  
|<span data-ttu-id="d19eb-108">層級</span><span class="sxs-lookup"><span data-stu-id="d19eb-108">Level</span></span>|<span data-ttu-id="d19eb-109">資訊</span><span class="sxs-lookup"><span data-stu-id="d19eb-109">Information</span></span>|  
|<span data-ttu-id="d19eb-110">通道</span><span class="sxs-lookup"><span data-stu-id="d19eb-110">Channel</span></span>|<span data-ttu-id="d19eb-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="d19eb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d19eb-112">描述</span><span class="sxs-lookup"><span data-stu-id="d19eb-112">Description</span></span>  
 <span data-ttu-id="d19eb-113">在 CacheMetadata 步驟期間，InvokeMethod 活動指出要叫用的方法不是靜態的。</span><span class="sxs-lookup"><span data-stu-id="d19eb-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d19eb-114">訊息</span><span class="sxs-lookup"><span data-stu-id="d19eb-114">Message</span></span>  
 <span data-ttu-id="d19eb-115">InvokeMethod '%1' - 方法不是靜態方法。</span><span class="sxs-lookup"><span data-stu-id="d19eb-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d19eb-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d19eb-116">Details</span></span>  
  
|<span data-ttu-id="d19eb-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="d19eb-117">Data Item Name</span></span>|<span data-ttu-id="d19eb-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="d19eb-118">Data Item Type</span></span>|<span data-ttu-id="d19eb-119">描述</span><span class="sxs-lookup"><span data-stu-id="d19eb-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d19eb-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="d19eb-120">InvokeMethod</span></span>|<span data-ttu-id="d19eb-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="d19eb-121">xs:string</span></span>|<span data-ttu-id="d19eb-122">InvokeMethod 活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="d19eb-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="d19eb-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d19eb-123">AppDomain</span></span>|<span data-ttu-id="d19eb-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="d19eb-124">xs:string</span></span>|<span data-ttu-id="d19eb-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="d19eb-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
