---
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 150973935d12455aa671043a619fbd6fd7e77425
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009951"
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="3a89f-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="3a89f-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="3a89f-103">屬性</span><span class="sxs-lookup"><span data-stu-id="3a89f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3a89f-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="3a89f-104">ID</span></span>|<span data-ttu-id="3a89f-105">1131</span><span class="sxs-lookup"><span data-stu-id="3a89f-105">1131</span></span>|  
|<span data-ttu-id="3a89f-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="3a89f-106">Keywords</span></span>|<span data-ttu-id="3a89f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3a89f-107">WFRuntime</span></span>|  
|<span data-ttu-id="3a89f-108">層級</span><span class="sxs-lookup"><span data-stu-id="3a89f-108">Level</span></span>|<span data-ttu-id="3a89f-109">資訊</span><span class="sxs-lookup"><span data-stu-id="3a89f-109">Information</span></span>|  
|<span data-ttu-id="3a89f-110">通道</span><span class="sxs-lookup"><span data-stu-id="3a89f-110">Channel</span></span>|<span data-ttu-id="3a89f-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3a89f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3a89f-112">描述</span><span class="sxs-lookup"><span data-stu-id="3a89f-112">Description</span></span>  
 <span data-ttu-id="3a89f-113">在 CacheMetadata 步驟期間，InvokeMethod 活動指出其於叫用方法時，使用非同步模式。</span><span class="sxs-lookup"><span data-stu-id="3a89f-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3a89f-114">訊息</span><span class="sxs-lookup"><span data-stu-id="3a89f-114">Message</span></span>  
 <span data-ttu-id="3a89f-115">InvokeMethod '%1' - 方法使用 '%2' 和 '%3' 非同步模式。</span><span class="sxs-lookup"><span data-stu-id="3a89f-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3a89f-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3a89f-116">Details</span></span>  
  
|<span data-ttu-id="3a89f-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="3a89f-117">Data Item Name</span></span>|<span data-ttu-id="3a89f-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="3a89f-118">Data Item Type</span></span>|<span data-ttu-id="3a89f-119">描述</span><span class="sxs-lookup"><span data-stu-id="3a89f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3a89f-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="3a89f-120">InvokeMethod</span></span>|<span data-ttu-id="3a89f-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="3a89f-121">xs:string</span></span>|<span data-ttu-id="3a89f-122">InvokeMethod 活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="3a89f-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="3a89f-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="3a89f-123">BeginMethod</span></span>|<span data-ttu-id="3a89f-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="3a89f-124">xs:string</span></span>|<span data-ttu-id="3a89f-125">Begin 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a89f-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="3a89f-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="3a89f-126">EndMethod</span></span>|<span data-ttu-id="3a89f-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="3a89f-127">xs:string</span></span>|<span data-ttu-id="3a89f-128">End 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a89f-128">The name of the end method.</span></span>|  
|<span data-ttu-id="3a89f-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3a89f-129">AppDomain</span></span>|<span data-ttu-id="3a89f-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="3a89f-130">xs:string</span></span>|<span data-ttu-id="3a89f-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="3a89f-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
