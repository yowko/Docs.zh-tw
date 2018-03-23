---
title: 302 - UserDefinedWarningOccurred
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ae455c9eec2335fcf6eb5473932bd8d9e5d2db95
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="302---userdefinedwarningoccurred"></a><span data-ttu-id="234da-102">302 - UserDefinedWarningOccurred</span><span class="sxs-lookup"><span data-stu-id="234da-102">302 - UserDefinedWarningOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="234da-103">屬性</span><span class="sxs-lookup"><span data-stu-id="234da-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="234da-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="234da-104">ID</span></span>|<span data-ttu-id="234da-105">302</span><span class="sxs-lookup"><span data-stu-id="234da-105">302</span></span>|  
|<span data-ttu-id="234da-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="234da-106">Keywords</span></span>|<span data-ttu-id="234da-107">Troubleshooting，HealthMonitoring，UserEvents，ServiceModel，EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="234da-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="234da-108">層級</span><span class="sxs-lookup"><span data-stu-id="234da-108">Level</span></span>|<span data-ttu-id="234da-109">警告</span><span class="sxs-lookup"><span data-stu-id="234da-109">Warning</span></span>|  
|<span data-ttu-id="234da-110">通道</span><span class="sxs-lookup"><span data-stu-id="234da-110">Channel</span></span>|<span data-ttu-id="234da-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="234da-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="234da-112">描述</span><span class="sxs-lookup"><span data-stu-id="234da-112">Description</span></span>  
 <span data-ttu-id="234da-113">此事件是由使用者程式碼所發出。</span><span class="sxs-lookup"><span data-stu-id="234da-113">This event is emitted from user code.</span></span> <span data-ttu-id="234da-114">當開發人員的服務中發生自訂定義警告事件時，即可發出此事件。</span><span class="sxs-lookup"><span data-stu-id="234da-114">Developers can emit this event when a custom-defined warning event occurs in their service.</span></span> <span data-ttu-id="234da-115">這項操作可使用 <xref:System.Diagnostics.Eventing> API 達到目的。</span><span class="sxs-lookup"><span data-stu-id="234da-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="234da-116">另外還有 WCF 範例，可包裝該 API 並示範如何正確發出此事件。</span><span class="sxs-lookup"><span data-stu-id="234da-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="234da-117">訊息</span><span class="sxs-lookup"><span data-stu-id="234da-117">Message</span></span>  
 <span data-ttu-id="234da-118">名稱:'%1'，參考:'%2'，承載:%3。</span><span class="sxs-lookup"><span data-stu-id="234da-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="234da-119">詳細資料</span><span class="sxs-lookup"><span data-stu-id="234da-119">Details</span></span>  
  
|<span data-ttu-id="234da-120">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="234da-120">Data Item Name</span></span>|<span data-ttu-id="234da-121">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="234da-121">Data Item Type</span></span>|<span data-ttu-id="234da-122">描述</span><span class="sxs-lookup"><span data-stu-id="234da-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="234da-123">名稱</span><span class="sxs-lookup"><span data-stu-id="234da-123">Name</span></span>|`xs:string`|<span data-ttu-id="234da-124">使用者定義的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="234da-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="234da-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="234da-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="234da-126">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="234da-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="234da-127">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="234da-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="234da-128">範例: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="234da-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="234da-129">承載</span><span class="sxs-lookup"><span data-stu-id="234da-129">Payload</span></span>|`xs:string`|<span data-ttu-id="234da-130">使用者定義的事件裝載。</span><span class="sxs-lookup"><span data-stu-id="234da-130">The user-defined payload of the event.</span></span>|
