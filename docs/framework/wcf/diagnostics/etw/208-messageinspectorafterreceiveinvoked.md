---
title: 208 - MessageInspectorAfterReceiveInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfb5f7b0-4346-4949-8104-351726b1f502
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 670650c612ac01ab9c82028388a4524d2f08fd79
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="208---messageinspectorafterreceiveinvoked"></a><span data-ttu-id="49925-102">208 - MessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="49925-102">208 - MessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="49925-103">屬性</span><span class="sxs-lookup"><span data-stu-id="49925-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="49925-104">ID</span><span class="sxs-lookup"><span data-stu-id="49925-104">ID</span></span>|<span data-ttu-id="49925-105">208</span><span class="sxs-lookup"><span data-stu-id="49925-105">208</span></span>|  
|<span data-ttu-id="49925-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="49925-106">Keywords</span></span>|<span data-ttu-id="49925-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="49925-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="49925-108">層級</span><span class="sxs-lookup"><span data-stu-id="49925-108">Level</span></span>|<span data-ttu-id="49925-109">資訊</span><span class="sxs-lookup"><span data-stu-id="49925-109">Information</span></span>|  
|<span data-ttu-id="49925-110">通道</span><span class="sxs-lookup"><span data-stu-id="49925-110">Channel</span></span>|<span data-ttu-id="49925-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="49925-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="49925-112">描述</span><span class="sxs-lookup"><span data-stu-id="49925-112">Description</span></span>  
 <span data-ttu-id="49925-113">服務模型在訊息偵測器上叫用 `AfterReceive` 方法之後，即會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="49925-113">This event is emitted after the Service Model has invoked the `AfterReceive` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="49925-114">訊息</span><span class="sxs-lookup"><span data-stu-id="49925-114">Message</span></span>  
 <span data-ttu-id="49925-115">發送器在型別 '%1' 的 MessageInspector 上叫用了 'AfterReceiveReply'。</span><span class="sxs-lookup"><span data-stu-id="49925-115">The Dispatcher invoked 'AfterReceiveReply' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="49925-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="49925-116">Details</span></span>  
  
|<span data-ttu-id="49925-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="49925-117">Data Item Name</span></span>|<span data-ttu-id="49925-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="49925-118">Data Item Type</span></span>|<span data-ttu-id="49925-119">描述</span><span class="sxs-lookup"><span data-stu-id="49925-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="49925-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="49925-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="49925-121">已叫用 `MessageInspector` 之類型的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="49925-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="49925-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="49925-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="49925-123">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="49925-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="49925-124">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="49925-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="49925-125">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="49925-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="49925-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="49925-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="49925-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="49925-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
