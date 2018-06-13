---
title: 223 - OperationFaulted
ms.date: 03/30/2017
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
ms.openlocfilehash: cf4a455d80a1a0ac09e99bad967c1feba3653842
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459414"
---
# <a name="223---operationfaulted"></a><span data-ttu-id="db2ef-102">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="db2ef-102">223 - OperationFaulted</span></span>
## <a name="properties"></a><span data-ttu-id="db2ef-103">屬性</span><span class="sxs-lookup"><span data-stu-id="db2ef-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="db2ef-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="db2ef-104">ID</span></span>|<span data-ttu-id="db2ef-105">223</span><span class="sxs-lookup"><span data-stu-id="db2ef-105">223</span></span>|  
|<span data-ttu-id="db2ef-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="db2ef-106">Keywords</span></span>|<span data-ttu-id="db2ef-107">EndToEndMonitoring，HealthMonitoring，Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="db2ef-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="db2ef-108">層級</span><span class="sxs-lookup"><span data-stu-id="db2ef-108">Level</span></span>|<span data-ttu-id="db2ef-109">警告</span><span class="sxs-lookup"><span data-stu-id="db2ef-109">Warning</span></span>|  
|<span data-ttu-id="db2ef-110">通道</span><span class="sxs-lookup"><span data-stu-id="db2ef-110">Channel</span></span>|<span data-ttu-id="db2ef-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="db2ef-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="db2ef-112">描述</span><span class="sxs-lookup"><span data-stu-id="db2ef-112">Description</span></span>  
 <span data-ttu-id="db2ef-113">當服務模型的預設 `OperationInvoker` 在叫用其方法而遭遇衍生自 `FaultException` 的例外狀況時，便會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="db2ef-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="db2ef-114">訊息</span><span class="sxs-lookup"><span data-stu-id="db2ef-114">Message</span></span>  
 <span data-ttu-id="db2ef-115">由 OperationInvoker 叫用時，'%1' 方法擲回 FaultException。</span><span class="sxs-lookup"><span data-stu-id="db2ef-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="db2ef-116">此方法的呼叫持續時間為 '%2' 毫秒。</span><span class="sxs-lookup"><span data-stu-id="db2ef-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="db2ef-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="db2ef-117">Details</span></span>  
  
|<span data-ttu-id="db2ef-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="db2ef-118">Data Item Name</span></span>|<span data-ttu-id="db2ef-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="db2ef-119">Data Item Type</span></span>|<span data-ttu-id="db2ef-120">描述</span><span class="sxs-lookup"><span data-stu-id="db2ef-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="db2ef-121">MethodName</span><span class="sxs-lookup"><span data-stu-id="db2ef-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="db2ef-122">`OperationInvoker` 叫用之方法的 CLR 名稱。</span><span class="sxs-lookup"><span data-stu-id="db2ef-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="db2ef-123">持續期間</span><span class="sxs-lookup"><span data-stu-id="db2ef-123">Duration</span></span>|`xs:long`|<span data-ttu-id="db2ef-124">`OperationInvoker` 叫用方法所花費的時間，以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="db2ef-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="db2ef-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="db2ef-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="db2ef-126">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="db2ef-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="db2ef-127">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="db2ef-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="db2ef-128">範例: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="db2ef-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="db2ef-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="db2ef-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="db2ef-130">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="db2ef-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
