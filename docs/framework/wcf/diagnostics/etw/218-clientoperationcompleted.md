---
title: 218 - ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: 83f39be84a8d62962b85652b0e39b537c92e612c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781757"
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="c9cca-102">218 - ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="c9cca-102">218 - ClientOperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="c9cca-103">屬性</span><span class="sxs-lookup"><span data-stu-id="c9cca-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c9cca-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="c9cca-104">ID</span></span>|<span data-ttu-id="c9cca-105">218</span><span class="sxs-lookup"><span data-stu-id="c9cca-105">218</span></span>|  
|<span data-ttu-id="c9cca-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c9cca-106">Keywords</span></span>|<span data-ttu-id="c9cca-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c9cca-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c9cca-108">層級</span><span class="sxs-lookup"><span data-stu-id="c9cca-108">Level</span></span>|<span data-ttu-id="c9cca-109">資訊</span><span class="sxs-lookup"><span data-stu-id="c9cca-109">Information</span></span>|  
|<span data-ttu-id="c9cca-110">通道</span><span class="sxs-lookup"><span data-stu-id="c9cca-110">Channel</span></span>|<span data-ttu-id="c9cca-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c9cca-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c9cca-112">描述</span><span class="sxs-lookup"><span data-stu-id="c9cca-112">Description</span></span>  
 <span data-ttu-id="c9cca-113">此事件由用戶端在作業完成之後發出。</span><span class="sxs-lookup"><span data-stu-id="c9cca-113">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="c9cca-114">若為單向作業，此事件是在訊息成功傳送之後立即發出。</span><span class="sxs-lookup"><span data-stu-id="c9cca-114">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="c9cca-115">若為要求-回應作業，此事件是在收到回應之後發出。</span><span class="sxs-lookup"><span data-stu-id="c9cca-115">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c9cca-116">訊息</span><span class="sxs-lookup"><span data-stu-id="c9cca-116">Message</span></span>  
 <span data-ttu-id="c9cca-117">用戶端已完成執行與 '%2' 合約相關聯的動作 '%1'。</span><span class="sxs-lookup"><span data-stu-id="c9cca-117">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="c9cca-118">訊息已傳送至 '%3'。</span><span class="sxs-lookup"><span data-stu-id="c9cca-118">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c9cca-119">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c9cca-119">Details</span></span>  
  
|<span data-ttu-id="c9cca-120">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="c9cca-120">Data Item Name</span></span>|<span data-ttu-id="c9cca-121">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="c9cca-121">Data Item Type</span></span>|<span data-ttu-id="c9cca-122">描述</span><span class="sxs-lookup"><span data-stu-id="c9cca-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c9cca-123">動作</span><span class="sxs-lookup"><span data-stu-id="c9cca-123">Action</span></span>|<span data-ttu-id="c9cca-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9cca-124">xs:string</span></span>|<span data-ttu-id="c9cca-125">傳出訊息的 SOAP 動作標頭。</span><span class="sxs-lookup"><span data-stu-id="c9cca-125">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="c9cca-126">合約名稱</span><span class="sxs-lookup"><span data-stu-id="c9cca-126">Contract Name</span></span>|`xs:string`|<span data-ttu-id="c9cca-127">合約的名稱。</span><span class="sxs-lookup"><span data-stu-id="c9cca-127">The name of the contract.</span></span> <span data-ttu-id="c9cca-128">範例：ICalculator。</span><span class="sxs-lookup"><span data-stu-id="c9cca-128">Example: ICalculator.</span></span>|  
|<span data-ttu-id="c9cca-129">目的地</span><span class="sxs-lookup"><span data-stu-id="c9cca-129">Destination</span></span>|`xs:string`|<span data-ttu-id="c9cca-130">訊息傳送至該處的服務端點位址。</span><span class="sxs-lookup"><span data-stu-id="c9cca-130">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="c9cca-131">HostReference</span><span class="sxs-lookup"><span data-stu-id="c9cca-131">HostReference</span></span>|`xs:string`|<span data-ttu-id="c9cca-132">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="c9cca-132">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c9cca-133">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="c9cca-133">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c9cca-134">範例：' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="c9cca-134">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c9cca-135">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c9cca-135">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c9cca-136">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="c9cca-136">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
