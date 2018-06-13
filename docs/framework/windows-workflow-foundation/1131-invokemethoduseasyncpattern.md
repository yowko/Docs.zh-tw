---
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 150973935d12455aa671043a619fbd6fd7e77425
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512661"
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="6960c-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="6960c-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="6960c-103">屬性</span><span class="sxs-lookup"><span data-stu-id="6960c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6960c-104">ID</span><span class="sxs-lookup"><span data-stu-id="6960c-104">ID</span></span>|<span data-ttu-id="6960c-105">1131</span><span class="sxs-lookup"><span data-stu-id="6960c-105">1131</span></span>|  
|<span data-ttu-id="6960c-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="6960c-106">Keywords</span></span>|<span data-ttu-id="6960c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6960c-107">WFRuntime</span></span>|  
|<span data-ttu-id="6960c-108">層級</span><span class="sxs-lookup"><span data-stu-id="6960c-108">Level</span></span>|<span data-ttu-id="6960c-109">資訊</span><span class="sxs-lookup"><span data-stu-id="6960c-109">Information</span></span>|  
|<span data-ttu-id="6960c-110">通道</span><span class="sxs-lookup"><span data-stu-id="6960c-110">Channel</span></span>|<span data-ttu-id="6960c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="6960c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6960c-112">描述</span><span class="sxs-lookup"><span data-stu-id="6960c-112">Description</span></span>  
 <span data-ttu-id="6960c-113">在 CacheMetadata 步驟期間，InvokeMethod 活動指出其於叫用方法時，使用非同步模式。</span><span class="sxs-lookup"><span data-stu-id="6960c-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6960c-114">訊息</span><span class="sxs-lookup"><span data-stu-id="6960c-114">Message</span></span>  
 <span data-ttu-id="6960c-115">InvokeMethod '%1' - 方法使用 '%2' 和 '%3' 非同步模式。</span><span class="sxs-lookup"><span data-stu-id="6960c-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6960c-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6960c-116">Details</span></span>  
  
|<span data-ttu-id="6960c-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="6960c-117">Data Item Name</span></span>|<span data-ttu-id="6960c-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="6960c-118">Data Item Type</span></span>|<span data-ttu-id="6960c-119">描述</span><span class="sxs-lookup"><span data-stu-id="6960c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6960c-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="6960c-120">InvokeMethod</span></span>|<span data-ttu-id="6960c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="6960c-121">xs:string</span></span>|<span data-ttu-id="6960c-122">InvokeMethod 活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="6960c-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="6960c-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="6960c-123">BeginMethod</span></span>|<span data-ttu-id="6960c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="6960c-124">xs:string</span></span>|<span data-ttu-id="6960c-125">Begin 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="6960c-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="6960c-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="6960c-126">EndMethod</span></span>|<span data-ttu-id="6960c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="6960c-127">xs:string</span></span>|<span data-ttu-id="6960c-128">End 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="6960c-128">The name of the end method.</span></span>|  
|<span data-ttu-id="6960c-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6960c-129">AppDomain</span></span>|<span data-ttu-id="6960c-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="6960c-130">xs:string</span></span>|<span data-ttu-id="6960c-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="6960c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
