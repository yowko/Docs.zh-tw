---
title: 217 - ClientOperationPrepared
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5062d2c2146dae8b22165cfbea0c6a78241d17b8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="5b399-102">217 - ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="5b399-102">217 - ClientOperationPrepared</span></span>
## <a name="properties"></a><span data-ttu-id="5b399-103">屬性</span><span class="sxs-lookup"><span data-stu-id="5b399-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5b399-104">ID</span><span class="sxs-lookup"><span data-stu-id="5b399-104">ID</span></span>|<span data-ttu-id="5b399-105">217</span><span class="sxs-lookup"><span data-stu-id="5b399-105">217</span></span>|  
|<span data-ttu-id="5b399-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="5b399-106">Keywords</span></span>|<span data-ttu-id="5b399-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5b399-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="5b399-108">層級</span><span class="sxs-lookup"><span data-stu-id="5b399-108">Level</span></span>|<span data-ttu-id="5b399-109">資訊</span><span class="sxs-lookup"><span data-stu-id="5b399-109">Information</span></span>|  
|<span data-ttu-id="5b399-110">通道</span><span class="sxs-lookup"><span data-stu-id="5b399-110">Channel</span></span>|<span data-ttu-id="5b399-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="5b399-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5b399-112">描述</span><span class="sxs-lookup"><span data-stu-id="5b399-112">Description</span></span>  
 <span data-ttu-id="5b399-113">此事件由用戶端在作業傳送至服務之前發出。</span><span class="sxs-lookup"><span data-stu-id="5b399-113">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5b399-114">訊息</span><span class="sxs-lookup"><span data-stu-id="5b399-114">Message</span></span>  
 <span data-ttu-id="5b399-115">用戶端正在執行與 '%2' 合約相關聯的動作 '%1'。</span><span class="sxs-lookup"><span data-stu-id="5b399-115">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="5b399-116">訊息將傳送至 '%3'。</span><span class="sxs-lookup"><span data-stu-id="5b399-116">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5b399-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5b399-117">Details</span></span>  
  
|<span data-ttu-id="5b399-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="5b399-118">Data Item Name</span></span>|<span data-ttu-id="5b399-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="5b399-119">Data Item Type</span></span>|<span data-ttu-id="5b399-120">描述</span><span class="sxs-lookup"><span data-stu-id="5b399-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5b399-121">動作</span><span class="sxs-lookup"><span data-stu-id="5b399-121">Action</span></span>|`xs:string`|<span data-ttu-id="5b399-122">傳出訊息的 SOAP 動作標頭。</span><span class="sxs-lookup"><span data-stu-id="5b399-122">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="5b399-123">合約名稱</span><span class="sxs-lookup"><span data-stu-id="5b399-123">Contract Name</span></span>|`xs:string`|<span data-ttu-id="5b399-124">合約的名稱。</span><span class="sxs-lookup"><span data-stu-id="5b399-124">The name of the contract.</span></span> <span data-ttu-id="5b399-125">範例：ICalculator。</span><span class="sxs-lookup"><span data-stu-id="5b399-125">Example: ICalculator.</span></span>|  
|<span data-ttu-id="5b399-126">目的地</span><span class="sxs-lookup"><span data-stu-id="5b399-126">Destination</span></span>|`xs:string`|<span data-ttu-id="5b399-127">訊息將傳送至該處的服務端點位址。</span><span class="sxs-lookup"><span data-stu-id="5b399-127">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="5b399-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="5b399-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="5b399-129">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="5b399-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="5b399-130">其格式定義為 ' Web Site Name Application Virtual Path &#124;服務的虛擬路徑 &#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="5b399-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="5b399-131">範例: ' Default Web Site/CalculatorApplication #124;/CalculatorService.svc &#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="5b399-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="5b399-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5b399-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="5b399-133">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="5b399-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
