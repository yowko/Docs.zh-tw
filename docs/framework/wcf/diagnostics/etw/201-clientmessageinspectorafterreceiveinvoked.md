---
title: 201 - ClientMessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
ms.openlocfilehash: d84f6c6f38868f7915caaaf87e15885099b65456
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266671"
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="947df-102">201 - ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="947df-102">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="947df-103">屬性</span><span class="sxs-lookup"><span data-stu-id="947df-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="947df-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="947df-104">ID</span></span>|<span data-ttu-id="947df-105">201</span><span class="sxs-lookup"><span data-stu-id="947df-105">201</span></span>|  
|<span data-ttu-id="947df-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="947df-106">Keywords</span></span>|<span data-ttu-id="947df-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="947df-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="947df-108">層級</span><span class="sxs-lookup"><span data-stu-id="947df-108">Level</span></span>|<span data-ttu-id="947df-109">資訊</span><span class="sxs-lookup"><span data-stu-id="947df-109">Information</span></span>|  
|<span data-ttu-id="947df-110">通路</span><span class="sxs-lookup"><span data-stu-id="947df-110">Channel</span></span>|<span data-ttu-id="947df-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="947df-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="947df-112">描述</span><span class="sxs-lookup"><span data-stu-id="947df-112">Description</span></span>  

 <span data-ttu-id="947df-113">服務模型在用戶端訊息偵測器上叫用 `AfterReceiveReply` 方法之後，即會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="947df-113">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="947df-114">訊息</span><span class="sxs-lookup"><span data-stu-id="947df-114">Message</span></span>  

 <span data-ttu-id="947df-115">發送器在型別為 '%1' 的 ClientMessageInspector 上叫用了 'AfterReceiveReply'。</span><span class="sxs-lookup"><span data-stu-id="947df-115">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="947df-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="947df-116">Details</span></span>  
  
|<span data-ttu-id="947df-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="947df-117">Data Item Name</span></span>|<span data-ttu-id="947df-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="947df-118">Data Item Type</span></span>|<span data-ttu-id="947df-119">描述</span><span class="sxs-lookup"><span data-stu-id="947df-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="947df-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="947df-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="947df-121">叫用之偵測器型別的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="947df-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="947df-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="947df-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="947df-123">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="947df-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="947df-124">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName '。</span><span class="sxs-lookup"><span data-stu-id="947df-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="947df-125">範例： ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '。</span><span class="sxs-lookup"><span data-stu-id="947df-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="947df-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="947df-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="947df-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="947df-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
