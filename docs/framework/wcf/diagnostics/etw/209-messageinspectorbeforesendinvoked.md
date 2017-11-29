---
title: 209 - MessageInspectorBeforeSendInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8de4338fd9d1d18ab1f689df39b2247a29d2dcf5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="a4668-102">209 - MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="a4668-102">209 - MessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="a4668-103">屬性</span><span class="sxs-lookup"><span data-stu-id="a4668-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a4668-104">ID</span><span class="sxs-lookup"><span data-stu-id="a4668-104">ID</span></span>|<span data-ttu-id="a4668-105">209</span><span class="sxs-lookup"><span data-stu-id="a4668-105">209</span></span>|  
|<span data-ttu-id="a4668-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a4668-106">Keywords</span></span>|<span data-ttu-id="a4668-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a4668-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="a4668-108">層級</span><span class="sxs-lookup"><span data-stu-id="a4668-108">Level</span></span>|<span data-ttu-id="a4668-109">資訊</span><span class="sxs-lookup"><span data-stu-id="a4668-109">Information</span></span>|  
|<span data-ttu-id="a4668-110">通道</span><span class="sxs-lookup"><span data-stu-id="a4668-110">Channel</span></span>|<span data-ttu-id="a4668-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="a4668-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a4668-112">描述</span><span class="sxs-lookup"><span data-stu-id="a4668-112">Description</span></span>  
 <span data-ttu-id="a4668-113">服務模型在訊息偵測器上叫用 `BeforeSend` 方法之後，即會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="a4668-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a4668-114">訊息</span><span class="sxs-lookup"><span data-stu-id="a4668-114">Message</span></span>  
 <span data-ttu-id="a4668-115">發送器在型別 '%1' 的 MessageInspector 上叫用了 'BeforeSendRequest'。</span><span class="sxs-lookup"><span data-stu-id="a4668-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a4668-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a4668-116">Details</span></span>  
  
|<span data-ttu-id="a4668-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="a4668-117">Data Item Name</span></span>|<span data-ttu-id="a4668-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="a4668-118">Data Item Type</span></span>|<span data-ttu-id="a4668-119">描述</span><span class="sxs-lookup"><span data-stu-id="a4668-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a4668-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="a4668-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="a4668-121">已叫用 `MessageInspector` 之類型的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="a4668-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="a4668-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="a4668-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="a4668-123">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="a4668-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a4668-124">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="a4668-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a4668-125">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="a4668-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a4668-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a4668-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a4668-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="a4668-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
