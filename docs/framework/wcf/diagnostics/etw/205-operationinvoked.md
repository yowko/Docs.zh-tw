---
title: 205 - OperationInvoked
ms.date: 03/30/2017
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
ms.openlocfilehash: e95b6923d21307b2ef68d4a5369b3cee86540239
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781975"
---
# <a name="205---operationinvoked"></a><span data-ttu-id="25af3-102">205 - OperationInvoked</span><span class="sxs-lookup"><span data-stu-id="25af3-102">205 - OperationInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="25af3-103">屬性</span><span class="sxs-lookup"><span data-stu-id="25af3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="25af3-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="25af3-104">ID</span></span>|<span data-ttu-id="25af3-105">205</span><span class="sxs-lookup"><span data-stu-id="25af3-105">205</span></span>|  
|<span data-ttu-id="25af3-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="25af3-106">Keywords</span></span>|<span data-ttu-id="25af3-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="25af3-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="25af3-108">層級</span><span class="sxs-lookup"><span data-stu-id="25af3-108">Level</span></span>|<span data-ttu-id="25af3-109">資訊</span><span class="sxs-lookup"><span data-stu-id="25af3-109">Information</span></span>|  
|<span data-ttu-id="25af3-110">通道</span><span class="sxs-lookup"><span data-stu-id="25af3-110">Channel</span></span>|<span data-ttu-id="25af3-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="25af3-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="25af3-112">描述</span><span class="sxs-lookup"><span data-stu-id="25af3-112">Description</span></span>  
 <span data-ttu-id="25af3-113">此事件會在服務模型的預設 `OperationInvoker` 開始呼叫方法之前發出。</span><span class="sxs-lookup"><span data-stu-id="25af3-113">This event is emitted just before the Service Model's default `OperationInvoker` begins a call to a method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="25af3-114">訊息</span><span class="sxs-lookup"><span data-stu-id="25af3-114">Message</span></span>  
 <span data-ttu-id="25af3-115">OperationInvoker 已叫用 '%1' 方法。</span><span class="sxs-lookup"><span data-stu-id="25af3-115">An OperationInvoker invoked the '%1' method.</span></span> <span data-ttu-id="25af3-116">呼叫端資訊: '%2'。</span><span class="sxs-lookup"><span data-stu-id="25af3-116">Caller information: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="25af3-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="25af3-117">Details</span></span>  
  
|<span data-ttu-id="25af3-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="25af3-118">Data Item Name</span></span>|<span data-ttu-id="25af3-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="25af3-119">Data Item Type</span></span>|<span data-ttu-id="25af3-120">描述</span><span class="sxs-lookup"><span data-stu-id="25af3-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="25af3-121">方法名稱</span><span class="sxs-lookup"><span data-stu-id="25af3-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="25af3-122">`OperationInvoker` 叫用之方法的 CLR 名稱。</span><span class="sxs-lookup"><span data-stu-id="25af3-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="25af3-123">呼叫端資訊</span><span class="sxs-lookup"><span data-stu-id="25af3-123">Caller Information</span></span>|`xs:string`|<span data-ttu-id="25af3-124">用戶端的 IP 位址和連接埠號碼，格式為 'IPAddress:PortNumber'。</span><span class="sxs-lookup"><span data-stu-id="25af3-124">The IP address and port number of the client in the format 'IPAddress:PortNumber'.</span></span> <span data-ttu-id="25af3-125">這兩個值都是從作業內容內的 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' 訊息屬性擷取。</span><span class="sxs-lookup"><span data-stu-id="25af3-125">The two values are retrieved from the 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' message property within the operation context.</span></span> <span data-ttu-id="25af3-126">請注意，針對非 TCP 繫結，此值為 `null`。</span><span class="sxs-lookup"><span data-stu-id="25af3-126">Note that for non-TCP bindings this value `null`.</span></span>|  
|<span data-ttu-id="25af3-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="25af3-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="25af3-128">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="25af3-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="25af3-129">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="25af3-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="25af3-130">範例：' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="25af3-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="25af3-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="25af3-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="25af3-132">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="25af3-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
