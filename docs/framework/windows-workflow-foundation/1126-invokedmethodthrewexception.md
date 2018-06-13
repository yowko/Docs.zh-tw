---
title: 1126 - InvokedMethodThrewException
ms.date: 03/30/2017
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
ms.openlocfilehash: 714a98a300426d80c3b494d701ae1bd53a49592f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512290"
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="d42ed-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="d42ed-102">1126 - InvokedMethodThrewException</span></span>
## <a name="properties"></a><span data-ttu-id="d42ed-103">屬性</span><span class="sxs-lookup"><span data-stu-id="d42ed-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d42ed-104">ID</span><span class="sxs-lookup"><span data-stu-id="d42ed-104">ID</span></span>|<span data-ttu-id="d42ed-105">1126</span><span class="sxs-lookup"><span data-stu-id="d42ed-105">1126</span></span>|  
|<span data-ttu-id="d42ed-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="d42ed-106">Keywords</span></span>|<span data-ttu-id="d42ed-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d42ed-107">WFRuntime</span></span>|  
|<span data-ttu-id="d42ed-108">層級</span><span class="sxs-lookup"><span data-stu-id="d42ed-108">Level</span></span>|<span data-ttu-id="d42ed-109">資訊</span><span class="sxs-lookup"><span data-stu-id="d42ed-109">Information</span></span>|  
|<span data-ttu-id="d42ed-110">通道</span><span class="sxs-lookup"><span data-stu-id="d42ed-110">Channel</span></span>|<span data-ttu-id="d42ed-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="d42ed-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d42ed-112">描述</span><span class="sxs-lookup"><span data-stu-id="d42ed-112">Description</span></span>  
 <span data-ttu-id="d42ed-113">表示 InvokeMethod 活動所呼叫的方法擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d42ed-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d42ed-114">訊息</span><span class="sxs-lookup"><span data-stu-id="d42ed-114">Message</span></span>  
 <span data-ttu-id="d42ed-115">在活動 '%1' 呼叫的方法中發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d42ed-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="d42ed-116">%2</span><span class="sxs-lookup"><span data-stu-id="d42ed-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="d42ed-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d42ed-117">Details</span></span>  
  
|<span data-ttu-id="d42ed-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="d42ed-118">Data Item Name</span></span>|<span data-ttu-id="d42ed-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="d42ed-119">Data Item Type</span></span>|<span data-ttu-id="d42ed-120">描述</span><span class="sxs-lookup"><span data-stu-id="d42ed-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d42ed-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="d42ed-121">InvokeMethod</span></span>|<span data-ttu-id="d42ed-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="d42ed-122">xs:string</span></span>|<span data-ttu-id="d42ed-123">InvokeMethod 活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="d42ed-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="d42ed-124">例外狀況</span><span class="sxs-lookup"><span data-stu-id="d42ed-124">Exception</span></span>|<span data-ttu-id="d42ed-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="d42ed-125">xs:string</span></span>|<span data-ttu-id="d42ed-126">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="d42ed-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="d42ed-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d42ed-127">AppDomain</span></span>|<span data-ttu-id="d42ed-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="d42ed-128">xs:string</span></span>|<span data-ttu-id="d42ed-129">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="d42ed-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
