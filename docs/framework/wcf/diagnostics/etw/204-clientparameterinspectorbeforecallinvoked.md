---
title: 204 - ClientParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
ms.openlocfilehash: a7db8c9fa87518c59969f3089ff033fa8c912577
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275784"
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a><span data-ttu-id="48c42-102">204 - ClientParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="48c42-102">204 - ClientParameterInspectorBeforeCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="48c42-103">屬性</span><span class="sxs-lookup"><span data-stu-id="48c42-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="48c42-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="48c42-104">ID</span></span>|<span data-ttu-id="48c42-105">204</span><span class="sxs-lookup"><span data-stu-id="48c42-105">204</span></span>|  
|<span data-ttu-id="48c42-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="48c42-106">Keywords</span></span>|<span data-ttu-id="48c42-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="48c42-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="48c42-108">層級</span><span class="sxs-lookup"><span data-stu-id="48c42-108">Level</span></span>|<span data-ttu-id="48c42-109">資訊</span><span class="sxs-lookup"><span data-stu-id="48c42-109">Information</span></span>|  
|<span data-ttu-id="48c42-110">通路</span><span class="sxs-lookup"><span data-stu-id="48c42-110">Channel</span></span>|<span data-ttu-id="48c42-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="48c42-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="48c42-112">描述</span><span class="sxs-lookup"><span data-stu-id="48c42-112">Description</span></span>  

 <span data-ttu-id="48c42-113">此事件是在服務模型已在用戶端參數偵測器上叫用 `BeforeCall` 方法之後發出。</span><span class="sxs-lookup"><span data-stu-id="48c42-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="48c42-114">訊息</span><span class="sxs-lookup"><span data-stu-id="48c42-114">Message</span></span>  

 <span data-ttu-id="48c42-115">發送器在型別 '%1' 的 ClientParameterInspector 上叫用了 'BeforeCall'。</span><span class="sxs-lookup"><span data-stu-id="48c42-115">The Dispatcher invoked 'BeforeCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="48c42-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="48c42-116">Details</span></span>  
  
|<span data-ttu-id="48c42-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="48c42-117">Data Item Name</span></span>|<span data-ttu-id="48c42-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="48c42-118">Data Item Type</span></span>|<span data-ttu-id="48c42-119">描述</span><span class="sxs-lookup"><span data-stu-id="48c42-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="48c42-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="48c42-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="48c42-121">叫用之偵測器型別的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="48c42-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="48c42-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="48c42-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="48c42-123">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="48c42-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="48c42-124">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName '。</span><span class="sxs-lookup"><span data-stu-id="48c42-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="48c42-125">範例： ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '。</span><span class="sxs-lookup"><span data-stu-id="48c42-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="48c42-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="48c42-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="48c42-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="48c42-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
