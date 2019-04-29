---
title: 213 - ServiceHostStarted
ms.date: 03/30/2017
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
ms.openlocfilehash: 819efa2e13c94e2c7a16c24f6ba9c7ef2b87ef8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781819"
---
# <a name="213---servicehoststarted"></a><span data-ttu-id="dd5ca-102">213 - ServiceHostStarted</span><span class="sxs-lookup"><span data-stu-id="dd5ca-102">213 - ServiceHostStarted</span></span>
## <a name="properties"></a><span data-ttu-id="dd5ca-103">屬性</span><span class="sxs-lookup"><span data-stu-id="dd5ca-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dd5ca-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="dd5ca-104">ID</span></span>|<span data-ttu-id="dd5ca-105">213</span><span class="sxs-lookup"><span data-stu-id="dd5ca-105">213</span></span>|  
|<span data-ttu-id="dd5ca-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="dd5ca-106">Keywords</span></span>|<span data-ttu-id="dd5ca-107">EndToEndMonitoring，HealthMonitoring，Troubleshooting，ServiceHost</span><span class="sxs-lookup"><span data-stu-id="dd5ca-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span></span>|  
|<span data-ttu-id="dd5ca-108">層級</span><span class="sxs-lookup"><span data-stu-id="dd5ca-108">Level</span></span>|<span data-ttu-id="dd5ca-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="dd5ca-109">LogAlways</span></span>|  
|<span data-ttu-id="dd5ca-110">通道</span><span class="sxs-lookup"><span data-stu-id="dd5ca-110">Channel</span></span>|<span data-ttu-id="dd5ca-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="dd5ca-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dd5ca-112">描述</span><span class="sxs-lookup"><span data-stu-id="dd5ca-112">Description</span></span>  
 <span data-ttu-id="dd5ca-113">此事件是在 Web 裝載服務主機啟動時發出。</span><span class="sxs-lookup"><span data-stu-id="dd5ca-113">This event is emitted when a Web-hosted service host is started.</span></span> <span data-ttu-id="dd5ca-114">這種情況通常是在訊息啟動服務時發生。</span><span class="sxs-lookup"><span data-stu-id="dd5ca-114">This typically happens when the service is activated by a message.</span></span> <span data-ttu-id="dd5ca-115">此外也可能在服務設定為自動啟動時發生。</span><span class="sxs-lookup"><span data-stu-id="dd5ca-115">It may also happen if the service is configured to be automatically started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dd5ca-116">訊息</span><span class="sxs-lookup"><span data-stu-id="dd5ca-116">Message</span></span>  
 <span data-ttu-id="dd5ca-117">ServiceHost 已啟動: '%1'。</span><span class="sxs-lookup"><span data-stu-id="dd5ca-117">ServiceHost started: '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dd5ca-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dd5ca-118">Details</span></span>  
  
|<span data-ttu-id="dd5ca-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="dd5ca-119">Data Item Name</span></span>|<span data-ttu-id="dd5ca-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="dd5ca-120">Data Item Type</span></span>|<span data-ttu-id="dd5ca-121">描述</span><span class="sxs-lookup"><span data-stu-id="dd5ca-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dd5ca-122">服務型別名稱</span><span class="sxs-lookup"><span data-stu-id="dd5ca-122">Service Type Name</span></span>|`xs:string`|<span data-ttu-id="dd5ca-123">服務實作之型別的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="dd5ca-123">The CLR FullName of the type of the service implementation.</span></span>|  
|<span data-ttu-id="dd5ca-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="dd5ca-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="dd5ca-125">若是 Web 裝載的服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="dd5ca-125">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="dd5ca-126">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="dd5ca-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="dd5ca-127">範例：' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="dd5ca-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="dd5ca-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="dd5ca-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="dd5ca-129">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="dd5ca-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
