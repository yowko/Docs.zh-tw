---
title: 1126 - InvokedMethodThrewException
ms.date: 03/30/2017
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
ms.openlocfilehash: 714a98a300426d80c3b494d701ae1bd53a49592f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924003"
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="373b5-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="373b5-102">1126 - InvokedMethodThrewException</span></span>
## <a name="properties"></a><span data-ttu-id="373b5-103">屬性</span><span class="sxs-lookup"><span data-stu-id="373b5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="373b5-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="373b5-104">ID</span></span>|<span data-ttu-id="373b5-105">1126</span><span class="sxs-lookup"><span data-stu-id="373b5-105">1126</span></span>|  
|<span data-ttu-id="373b5-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="373b5-106">Keywords</span></span>|<span data-ttu-id="373b5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="373b5-107">WFRuntime</span></span>|  
|<span data-ttu-id="373b5-108">層級</span><span class="sxs-lookup"><span data-stu-id="373b5-108">Level</span></span>|<span data-ttu-id="373b5-109">資訊</span><span class="sxs-lookup"><span data-stu-id="373b5-109">Information</span></span>|  
|<span data-ttu-id="373b5-110">通道</span><span class="sxs-lookup"><span data-stu-id="373b5-110">Channel</span></span>|<span data-ttu-id="373b5-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="373b5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="373b5-112">描述</span><span class="sxs-lookup"><span data-stu-id="373b5-112">Description</span></span>  
 <span data-ttu-id="373b5-113">表示 InvokeMethod 活動所呼叫的方法擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="373b5-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="373b5-114">訊息</span><span class="sxs-lookup"><span data-stu-id="373b5-114">Message</span></span>  
 <span data-ttu-id="373b5-115">在活動 '%1' 呼叫的方法中發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="373b5-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="373b5-116">%2</span><span class="sxs-lookup"><span data-stu-id="373b5-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="373b5-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="373b5-117">Details</span></span>  
  
|<span data-ttu-id="373b5-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="373b5-118">Data Item Name</span></span>|<span data-ttu-id="373b5-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="373b5-119">Data Item Type</span></span>|<span data-ttu-id="373b5-120">描述</span><span class="sxs-lookup"><span data-stu-id="373b5-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="373b5-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="373b5-121">InvokeMethod</span></span>|<span data-ttu-id="373b5-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="373b5-122">xs:string</span></span>|<span data-ttu-id="373b5-123">InvokeMethod 活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="373b5-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="373b5-124">例外</span><span class="sxs-lookup"><span data-stu-id="373b5-124">Exception</span></span>|<span data-ttu-id="373b5-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="373b5-125">xs:string</span></span>|<span data-ttu-id="373b5-126">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="373b5-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="373b5-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="373b5-127">AppDomain</span></span>|<span data-ttu-id="373b5-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="373b5-128">xs:string</span></span>|<span data-ttu-id="373b5-129">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="373b5-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
