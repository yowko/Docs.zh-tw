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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 461c9e423abb7b34edec4135f05f8fcf66244cfc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="a31b9-102">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="a31b9-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="a31b9-103">屬性</span><span class="sxs-lookup"><span data-stu-id="a31b9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a31b9-104">ID</span><span class="sxs-lookup"><span data-stu-id="a31b9-104">ID</span></span>|<span data-ttu-id="a31b9-105">202</span><span class="sxs-lookup"><span data-stu-id="a31b9-105">202</span></span>|  
|<span data-ttu-id="a31b9-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a31b9-106">Keywords</span></span>|<span data-ttu-id="a31b9-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a31b9-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="a31b9-108">層級</span><span class="sxs-lookup"><span data-stu-id="a31b9-108">Level</span></span>|<span data-ttu-id="a31b9-109">資訊</span><span class="sxs-lookup"><span data-stu-id="a31b9-109">Information</span></span>|  
|<span data-ttu-id="a31b9-110">通道</span><span class="sxs-lookup"><span data-stu-id="a31b9-110">Channel</span></span>|<span data-ttu-id="a31b9-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="a31b9-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a31b9-112">描述</span><span class="sxs-lookup"><span data-stu-id="a31b9-112">Description</span></span>  
 <span data-ttu-id="a31b9-113">服務模型在用戶端訊息偵測器上叫用 `BeforeSendRequest` 方法之後，即會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="a31b9-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a31b9-114">訊息</span><span class="sxs-lookup"><span data-stu-id="a31b9-114">Message</span></span>  
 <span data-ttu-id="a31b9-115">發送器在型別 '%1' 的 ClientMessageInspector 上叫用了 'BeforeSendRequest'。</span><span class="sxs-lookup"><span data-stu-id="a31b9-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a31b9-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a31b9-116">Details</span></span>  
  
|<span data-ttu-id="a31b9-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="a31b9-117">Data Item Name</span></span>|<span data-ttu-id="a31b9-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="a31b9-118">Data Item Type</span></span>|<span data-ttu-id="a31b9-119">描述</span><span class="sxs-lookup"><span data-stu-id="a31b9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a31b9-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="a31b9-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="a31b9-121">叫用之偵測器型別的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="a31b9-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="a31b9-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="a31b9-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="a31b9-123">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="a31b9-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a31b9-124">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="a31b9-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a31b9-125">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="a31b9-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a31b9-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a31b9-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a31b9-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="a31b9-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
