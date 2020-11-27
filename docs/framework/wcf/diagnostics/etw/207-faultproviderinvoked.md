---
title: 207 - FaultProviderInvoked
ms.date: 03/30/2017
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
ms.openlocfilehash: 71381c9eee6aed4792500c8558db88e239bf89f7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295167"
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="9c475-102">207 - FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="9c475-102">207 - FaultProviderInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="9c475-103">屬性</span><span class="sxs-lookup"><span data-stu-id="9c475-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9c475-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="9c475-104">ID</span></span>|<span data-ttu-id="9c475-105">207</span><span class="sxs-lookup"><span data-stu-id="9c475-105">207</span></span>|  
|<span data-ttu-id="9c475-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="9c475-106">Keywords</span></span>|<span data-ttu-id="9c475-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9c475-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="9c475-108">層級</span><span class="sxs-lookup"><span data-stu-id="9c475-108">Level</span></span>|<span data-ttu-id="9c475-109">資訊</span><span class="sxs-lookup"><span data-stu-id="9c475-109">Information</span></span>|  
|<span data-ttu-id="9c475-110">通路</span><span class="sxs-lookup"><span data-stu-id="9c475-110">Channel</span></span>|<span data-ttu-id="9c475-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="9c475-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9c475-112">描述</span><span class="sxs-lookup"><span data-stu-id="9c475-112">Description</span></span>  

 <span data-ttu-id="9c475-113">此事件是在已叫用 `FaultProvider` 之後發出。</span><span class="sxs-lookup"><span data-stu-id="9c475-113">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9c475-114">訊息</span><span class="sxs-lookup"><span data-stu-id="9c475-114">Message</span></span>  

 <span data-ttu-id="9c475-115">發送器已叫用型別為 '%1' 的 FaultProvider，其例外狀況型別為 '%2'。</span><span class="sxs-lookup"><span data-stu-id="9c475-115">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9c475-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9c475-116">Details</span></span>  
  
|<span data-ttu-id="9c475-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="9c475-117">Data Item Name</span></span>|<span data-ttu-id="9c475-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="9c475-118">Data Item Type</span></span>|<span data-ttu-id="9c475-119">描述</span><span class="sxs-lookup"><span data-stu-id="9c475-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9c475-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="9c475-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="9c475-121">已叫用 `FaultProvider` 之類型的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="9c475-121">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="9c475-122">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="9c475-122">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="9c475-123">`FaultProvider` 已處理之例外狀況的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="9c475-123">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="9c475-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="9c475-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="9c475-125">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="9c475-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9c475-126">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName '。</span><span class="sxs-lookup"><span data-stu-id="9c475-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9c475-127">範例： ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '。</span><span class="sxs-lookup"><span data-stu-id="9c475-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9c475-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9c475-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9c475-129">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="9c475-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
