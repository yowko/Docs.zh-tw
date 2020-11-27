---
title: 1126 - InvokedMethodThrewException
ms.date: 03/30/2017
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
ms.openlocfilehash: 7caaebe42f49a62fec61ba17a4d3fe3a538e2ab4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262836"
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="b40fe-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="b40fe-102">1126 - InvokedMethodThrewException</span></span>

## <a name="properties"></a><span data-ttu-id="b40fe-103">屬性</span><span class="sxs-lookup"><span data-stu-id="b40fe-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b40fe-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="b40fe-104">ID</span></span>|<span data-ttu-id="b40fe-105">1126</span><span class="sxs-lookup"><span data-stu-id="b40fe-105">1126</span></span>|  
|<span data-ttu-id="b40fe-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="b40fe-106">Keywords</span></span>|<span data-ttu-id="b40fe-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b40fe-107">WFRuntime</span></span>|  
|<span data-ttu-id="b40fe-108">層級</span><span class="sxs-lookup"><span data-stu-id="b40fe-108">Level</span></span>|<span data-ttu-id="b40fe-109">資訊</span><span class="sxs-lookup"><span data-stu-id="b40fe-109">Information</span></span>|  
|<span data-ttu-id="b40fe-110">通路</span><span class="sxs-lookup"><span data-stu-id="b40fe-110">Channel</span></span>|<span data-ttu-id="b40fe-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="b40fe-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b40fe-112">描述</span><span class="sxs-lookup"><span data-stu-id="b40fe-112">Description</span></span>  

 <span data-ttu-id="b40fe-113">表示 InvokeMethod 活動所呼叫的方法擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b40fe-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b40fe-114">訊息</span><span class="sxs-lookup"><span data-stu-id="b40fe-114">Message</span></span>  

 <span data-ttu-id="b40fe-115">在活動 '%1' 呼叫的方法中發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b40fe-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="b40fe-116">%2</span><span class="sxs-lookup"><span data-stu-id="b40fe-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="b40fe-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b40fe-117">Details</span></span>  
  
|<span data-ttu-id="b40fe-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="b40fe-118">Data Item Name</span></span>|<span data-ttu-id="b40fe-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="b40fe-119">Data Item Type</span></span>|<span data-ttu-id="b40fe-120">描述</span><span class="sxs-lookup"><span data-stu-id="b40fe-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b40fe-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="b40fe-121">InvokeMethod</span></span>|<span data-ttu-id="b40fe-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="b40fe-122">xs:string</span></span>|<span data-ttu-id="b40fe-123">InvokeMethod 活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="b40fe-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="b40fe-124">例外狀況</span><span class="sxs-lookup"><span data-stu-id="b40fe-124">Exception</span></span>|<span data-ttu-id="b40fe-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="b40fe-125">xs:string</span></span>|<span data-ttu-id="b40fe-126">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="b40fe-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="b40fe-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b40fe-127">AppDomain</span></span>|<span data-ttu-id="b40fe-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="b40fe-128">xs:string</span></span>|<span data-ttu-id="b40fe-129">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="b40fe-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
