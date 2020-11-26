---
title: 302 - UserDefinedWarningOccurred
ms.date: 03/30/2017
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
ms.openlocfilehash: b942b2e9716713371b8679fc9df9b9634dfc7283
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243439"
---
# <a name="302---userdefinedwarningoccurred"></a><span data-ttu-id="ecd0b-102">302 - UserDefinedWarningOccurred</span><span class="sxs-lookup"><span data-stu-id="ecd0b-102">302 - UserDefinedWarningOccurred</span></span>

## <a name="properties"></a><span data-ttu-id="ecd0b-103">屬性</span><span class="sxs-lookup"><span data-stu-id="ecd0b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ecd0b-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="ecd0b-104">ID</span></span>|<span data-ttu-id="ecd0b-105">302</span><span class="sxs-lookup"><span data-stu-id="ecd0b-105">302</span></span>|  
|<span data-ttu-id="ecd0b-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="ecd0b-106">Keywords</span></span>|<span data-ttu-id="ecd0b-107">Troubleshooting，HealthMonitoring，UserEvents，ServiceModel，EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="ecd0b-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="ecd0b-108">層級</span><span class="sxs-lookup"><span data-stu-id="ecd0b-108">Level</span></span>|<span data-ttu-id="ecd0b-109">警告</span><span class="sxs-lookup"><span data-stu-id="ecd0b-109">Warning</span></span>|  
|<span data-ttu-id="ecd0b-110">通路</span><span class="sxs-lookup"><span data-stu-id="ecd0b-110">Channel</span></span>|<span data-ttu-id="ecd0b-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="ecd0b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ecd0b-112">描述</span><span class="sxs-lookup"><span data-stu-id="ecd0b-112">Description</span></span>  

 <span data-ttu-id="ecd0b-113">此事件是由使用者程式碼所發出。</span><span class="sxs-lookup"><span data-stu-id="ecd0b-113">This event is emitted from user code.</span></span> <span data-ttu-id="ecd0b-114">當開發人員的服務中發生自訂定義警告事件時，即可發出此事件。</span><span class="sxs-lookup"><span data-stu-id="ecd0b-114">Developers can emit this event when a custom-defined warning event occurs in their service.</span></span> <span data-ttu-id="ecd0b-115">這項操作可使用 <xref:System.Diagnostics.Eventing> API 達到目的。</span><span class="sxs-lookup"><span data-stu-id="ecd0b-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="ecd0b-116">另外還有 WCF 範例，可包裝該 API 並示範如何正確發出此事件。</span><span class="sxs-lookup"><span data-stu-id="ecd0b-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ecd0b-117">訊息</span><span class="sxs-lookup"><span data-stu-id="ecd0b-117">Message</span></span>  

 <span data-ttu-id="ecd0b-118">名稱:'%1'，參考:'%2'，承載:%3。</span><span class="sxs-lookup"><span data-stu-id="ecd0b-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="ecd0b-119">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ecd0b-119">Details</span></span>  
  
|<span data-ttu-id="ecd0b-120">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="ecd0b-120">Data Item Name</span></span>|<span data-ttu-id="ecd0b-121">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="ecd0b-121">Data Item Type</span></span>|<span data-ttu-id="ecd0b-122">描述</span><span class="sxs-lookup"><span data-stu-id="ecd0b-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ecd0b-123">Name</span><span class="sxs-lookup"><span data-stu-id="ecd0b-123">Name</span></span>|`xs:string`|<span data-ttu-id="ecd0b-124">使用者定義的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="ecd0b-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="ecd0b-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="ecd0b-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="ecd0b-126">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="ecd0b-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ecd0b-127">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName '。</span><span class="sxs-lookup"><span data-stu-id="ecd0b-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ecd0b-128">範例： ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '。</span><span class="sxs-lookup"><span data-stu-id="ecd0b-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ecd0b-129">Payload</span><span class="sxs-lookup"><span data-stu-id="ecd0b-129">Payload</span></span>|`xs:string`|<span data-ttu-id="ecd0b-130">使用者定義的事件裝載。</span><span class="sxs-lookup"><span data-stu-id="ecd0b-130">The user-defined payload of the event.</span></span>|
