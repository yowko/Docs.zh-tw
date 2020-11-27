---
title: 2577 - TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: 33c68984e88eaa5e3028899a7c3066c94a65e8eb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271235"
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="a1037-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="a1037-102">2577 - TryCatchExceptionDuringCancelation</span></span>

## <a name="properties"></a><span data-ttu-id="a1037-103">屬性</span><span class="sxs-lookup"><span data-stu-id="a1037-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a1037-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="a1037-104">ID</span></span>|<span data-ttu-id="a1037-105">2577</span><span class="sxs-lookup"><span data-stu-id="a1037-105">2577</span></span>|  
|<span data-ttu-id="a1037-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a1037-106">Keywords</span></span>|<span data-ttu-id="a1037-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="a1037-107">WFActivities</span></span>|  
|<span data-ttu-id="a1037-108">層級</span><span class="sxs-lookup"><span data-stu-id="a1037-108">Level</span></span>|<span data-ttu-id="a1037-109">警告</span><span class="sxs-lookup"><span data-stu-id="a1037-109">Warning</span></span>|  
|<span data-ttu-id="a1037-110">通路</span><span class="sxs-lookup"><span data-stu-id="a1037-110">Channel</span></span>|<span data-ttu-id="a1037-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="a1037-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a1037-112">描述</span><span class="sxs-lookup"><span data-stu-id="a1037-112">Description</span></span>  

 <span data-ttu-id="a1037-113">表示 TryCatch 活動的子活動在取消期間擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a1037-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a1037-114">訊息</span><span class="sxs-lookup"><span data-stu-id="a1037-114">Message</span></span>  

 <span data-ttu-id="a1037-115">TryCatch 活動 '%1' 的子活動在取消期間擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a1037-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a1037-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a1037-116">Details</span></span>  
  
|<span data-ttu-id="a1037-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="a1037-117">Data Item Name</span></span>|<span data-ttu-id="a1037-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="a1037-118">Data Item Type</span></span>|<span data-ttu-id="a1037-119">描述</span><span class="sxs-lookup"><span data-stu-id="a1037-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a1037-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="a1037-120">DisplayName</span></span>|<span data-ttu-id="a1037-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="a1037-121">xs:string</span></span>|<span data-ttu-id="a1037-122">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="a1037-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="a1037-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a1037-123">AppDomain</span></span>|<span data-ttu-id="a1037-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="a1037-124">xs:string</span></span>|<span data-ttu-id="a1037-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="a1037-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
