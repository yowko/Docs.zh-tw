---
title: 212 - ParameterInspectorBeforeCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d043bbf4b6484e2d2bcc7840fa08ebc371dca02a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="ffb86-102">212 - ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="ffb86-102">212 - ParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="ffb86-103">屬性</span><span class="sxs-lookup"><span data-stu-id="ffb86-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ffb86-104">ID</span><span class="sxs-lookup"><span data-stu-id="ffb86-104">ID</span></span>|<span data-ttu-id="ffb86-105">212</span><span class="sxs-lookup"><span data-stu-id="ffb86-105">212</span></span>|  
|<span data-ttu-id="ffb86-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="ffb86-106">Keywords</span></span>|<span data-ttu-id="ffb86-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ffb86-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="ffb86-108">層級</span><span class="sxs-lookup"><span data-stu-id="ffb86-108">Level</span></span>|<span data-ttu-id="ffb86-109">資訊</span><span class="sxs-lookup"><span data-stu-id="ffb86-109">Information</span></span>|  
|<span data-ttu-id="ffb86-110">通道</span><span class="sxs-lookup"><span data-stu-id="ffb86-110">Channel</span></span>|<span data-ttu-id="ffb86-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="ffb86-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ffb86-112">描述</span><span class="sxs-lookup"><span data-stu-id="ffb86-112">Description</span></span>  
 <span data-ttu-id="ffb86-113">服務模型已在 `BeforeCall` 上叫用 `ParameterInspector` 方法之後，即會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="ffb86-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ffb86-114">訊息</span><span class="sxs-lookup"><span data-stu-id="ffb86-114">Message</span></span>  
 <span data-ttu-id="ffb86-115">發送器在型別 '%1' 的 ParameterInspector 上叫用了 'BeforeCall'。</span><span class="sxs-lookup"><span data-stu-id="ffb86-115">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ffb86-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ffb86-116">Details</span></span>  
  
|<span data-ttu-id="ffb86-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="ffb86-117">Data Item Name</span></span>|<span data-ttu-id="ffb86-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="ffb86-118">Data Item Type</span></span>|<span data-ttu-id="ffb86-119">描述</span><span class="sxs-lookup"><span data-stu-id="ffb86-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ffb86-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="ffb86-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="ffb86-121">叫用之偵測器型別的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="ffb86-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="ffb86-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="ffb86-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="ffb86-123">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="ffb86-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ffb86-124">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="ffb86-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ffb86-125">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="ffb86-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ffb86-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ffb86-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ffb86-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="ffb86-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
