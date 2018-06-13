---
title: 212 - ParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
ms.openlocfilehash: 02d4a4ed1e96983e132a1943dd39f9f885e5596a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458802"
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="1c417-102">212 - ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="1c417-102">212 - ParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="1c417-103">屬性</span><span class="sxs-lookup"><span data-stu-id="1c417-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1c417-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="1c417-104">ID</span></span>|<span data-ttu-id="1c417-105">212</span><span class="sxs-lookup"><span data-stu-id="1c417-105">212</span></span>|  
|<span data-ttu-id="1c417-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="1c417-106">Keywords</span></span>|<span data-ttu-id="1c417-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1c417-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="1c417-108">層級</span><span class="sxs-lookup"><span data-stu-id="1c417-108">Level</span></span>|<span data-ttu-id="1c417-109">資訊</span><span class="sxs-lookup"><span data-stu-id="1c417-109">Information</span></span>|  
|<span data-ttu-id="1c417-110">通道</span><span class="sxs-lookup"><span data-stu-id="1c417-110">Channel</span></span>|<span data-ttu-id="1c417-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="1c417-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1c417-112">描述</span><span class="sxs-lookup"><span data-stu-id="1c417-112">Description</span></span>  
 <span data-ttu-id="1c417-113">服務模型已在 `BeforeCall` 上叫用 `ParameterInspector` 方法之後，即會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="1c417-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1c417-114">訊息</span><span class="sxs-lookup"><span data-stu-id="1c417-114">Message</span></span>  
 <span data-ttu-id="1c417-115">發送器在型別 '%1' 的 ParameterInspector 上叫用了 'BeforeCall'。</span><span class="sxs-lookup"><span data-stu-id="1c417-115">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1c417-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1c417-116">Details</span></span>  
  
|<span data-ttu-id="1c417-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="1c417-117">Data Item Name</span></span>|<span data-ttu-id="1c417-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="1c417-118">Data Item Type</span></span>|<span data-ttu-id="1c417-119">描述</span><span class="sxs-lookup"><span data-stu-id="1c417-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1c417-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="1c417-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="1c417-121">叫用之偵測器型別的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="1c417-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="1c417-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="1c417-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="1c417-123">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="1c417-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="1c417-124">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="1c417-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="1c417-125">範例: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="1c417-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="1c417-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1c417-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1c417-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="1c417-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
