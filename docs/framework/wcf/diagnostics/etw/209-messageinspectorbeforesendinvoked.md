---
title: 209 - MessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
ms.openlocfilehash: 50a9424f445781cac70d7d7fde58beea10231cfa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267750"
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="73f11-102">209 - MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="73f11-102">209 - MessageInspectorBeforeSendInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="73f11-103">屬性</span><span class="sxs-lookup"><span data-stu-id="73f11-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="73f11-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="73f11-104">ID</span></span>|<span data-ttu-id="73f11-105">209</span><span class="sxs-lookup"><span data-stu-id="73f11-105">209</span></span>|  
|<span data-ttu-id="73f11-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="73f11-106">Keywords</span></span>|<span data-ttu-id="73f11-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="73f11-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="73f11-108">層級</span><span class="sxs-lookup"><span data-stu-id="73f11-108">Level</span></span>|<span data-ttu-id="73f11-109">資訊</span><span class="sxs-lookup"><span data-stu-id="73f11-109">Information</span></span>|  
|<span data-ttu-id="73f11-110">通路</span><span class="sxs-lookup"><span data-stu-id="73f11-110">Channel</span></span>|<span data-ttu-id="73f11-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="73f11-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="73f11-112">描述</span><span class="sxs-lookup"><span data-stu-id="73f11-112">Description</span></span>  

 <span data-ttu-id="73f11-113">服務模型在訊息偵測器上叫用 `BeforeSend` 方法之後，即會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="73f11-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="73f11-114">訊息</span><span class="sxs-lookup"><span data-stu-id="73f11-114">Message</span></span>  

 <span data-ttu-id="73f11-115">發送器在型別 '%1' 的 MessageInspector 上叫用了 'BeforeSendRequest'。</span><span class="sxs-lookup"><span data-stu-id="73f11-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="73f11-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="73f11-116">Details</span></span>  
  
|<span data-ttu-id="73f11-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="73f11-117">Data Item Name</span></span>|<span data-ttu-id="73f11-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="73f11-118">Data Item Type</span></span>|<span data-ttu-id="73f11-119">描述</span><span class="sxs-lookup"><span data-stu-id="73f11-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="73f11-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="73f11-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="73f11-121">已叫用 `MessageInspector` 之類型的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="73f11-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="73f11-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="73f11-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="73f11-123">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="73f11-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="73f11-124">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName '。</span><span class="sxs-lookup"><span data-stu-id="73f11-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="73f11-125">範例： ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '。</span><span class="sxs-lookup"><span data-stu-id="73f11-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="73f11-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="73f11-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="73f11-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="73f11-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
