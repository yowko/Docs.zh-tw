---
title: 211 - ParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
ms.openlocfilehash: 7027b6557520a9ccb587f8d383d3598571da5838
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279060"
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="31122-102">211 - ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="31122-102">211 - ParameterInspectorAfterCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="31122-103">屬性</span><span class="sxs-lookup"><span data-stu-id="31122-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="31122-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="31122-104">ID</span></span>|<span data-ttu-id="31122-105">211</span><span class="sxs-lookup"><span data-stu-id="31122-105">211</span></span>|  
|<span data-ttu-id="31122-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="31122-106">Keywords</span></span>|<span data-ttu-id="31122-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="31122-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="31122-108">層級</span><span class="sxs-lookup"><span data-stu-id="31122-108">Level</span></span>|<span data-ttu-id="31122-109">資訊</span><span class="sxs-lookup"><span data-stu-id="31122-109">Information</span></span>|  
|<span data-ttu-id="31122-110">通路</span><span class="sxs-lookup"><span data-stu-id="31122-110">Channel</span></span>|<span data-ttu-id="31122-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="31122-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="31122-112">描述</span><span class="sxs-lookup"><span data-stu-id="31122-112">Description</span></span>  

 <span data-ttu-id="31122-113">服務模型已在 `AfterCall` 上叫用 `ParameterInspector` 方法之後，即會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="31122-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="31122-114">訊息</span><span class="sxs-lookup"><span data-stu-id="31122-114">Message</span></span>  

 <span data-ttu-id="31122-115">發送器在型別 '%1' 的 ParameterInspector 上叫用 'AfterCall'。</span><span class="sxs-lookup"><span data-stu-id="31122-115">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="31122-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="31122-116">Details</span></span>  
  
|<span data-ttu-id="31122-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="31122-117">Data Item Name</span></span>|<span data-ttu-id="31122-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="31122-118">Data Item Type</span></span>|<span data-ttu-id="31122-119">描述</span><span class="sxs-lookup"><span data-stu-id="31122-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="31122-120">類型名稱</span><span class="sxs-lookup"><span data-stu-id="31122-120">Type Name</span></span>|`xs:string`|<span data-ttu-id="31122-121">已叫用 `ParameterInspector` 之類型的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="31122-121">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="31122-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="31122-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="31122-123">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="31122-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="31122-124">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName '。</span><span class="sxs-lookup"><span data-stu-id="31122-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="31122-125">範例： ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '。</span><span class="sxs-lookup"><span data-stu-id="31122-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="31122-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="31122-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="31122-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="31122-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
