---
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: baf466bf63dcb9335a20eed8b563c222e09c7055
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="a3491-102">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="a3491-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="a3491-103">屬性</span><span class="sxs-lookup"><span data-stu-id="a3491-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a3491-104">ID</span><span class="sxs-lookup"><span data-stu-id="a3491-104">ID</span></span>|<span data-ttu-id="a3491-105">202</span><span class="sxs-lookup"><span data-stu-id="a3491-105">202</span></span>|  
|<span data-ttu-id="a3491-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a3491-106">Keywords</span></span>|<span data-ttu-id="a3491-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a3491-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="a3491-108">層級</span><span class="sxs-lookup"><span data-stu-id="a3491-108">Level</span></span>|<span data-ttu-id="a3491-109">資訊</span><span class="sxs-lookup"><span data-stu-id="a3491-109">Information</span></span>|  
|<span data-ttu-id="a3491-110">通道</span><span class="sxs-lookup"><span data-stu-id="a3491-110">Channel</span></span>|<span data-ttu-id="a3491-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="a3491-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a3491-112">描述</span><span class="sxs-lookup"><span data-stu-id="a3491-112">Description</span></span>  
 <span data-ttu-id="a3491-113">服務模型在用戶端訊息偵測器上叫用 `BeforeSendRequest` 方法之後，即會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="a3491-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a3491-114">訊息</span><span class="sxs-lookup"><span data-stu-id="a3491-114">Message</span></span>  
 <span data-ttu-id="a3491-115">發送器在型別 '%1' 的 ClientMessageInspector 上叫用了 'BeforeSendRequest'。</span><span class="sxs-lookup"><span data-stu-id="a3491-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a3491-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a3491-116">Details</span></span>  
  
|<span data-ttu-id="a3491-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="a3491-117">Data Item Name</span></span>|<span data-ttu-id="a3491-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="a3491-118">Data Item Type</span></span>|<span data-ttu-id="a3491-119">描述</span><span class="sxs-lookup"><span data-stu-id="a3491-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a3491-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="a3491-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="a3491-121">叫用之偵測器型別的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="a3491-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="a3491-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="a3491-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="a3491-123">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="a3491-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a3491-124">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="a3491-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a3491-125">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="a3491-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a3491-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a3491-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a3491-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="a3491-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
