---
title: 499 - TransferEmitted
ms.date: 03/30/2017
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
ms.openlocfilehash: dc47aa36b5a409c89aaf7963ce51f11cdf84b0fc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247573"
---
# <a name="499---transferemitted"></a><span data-ttu-id="922d6-102">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="922d6-102">499 - TransferEmitted</span></span>

## <a name="properties"></a><span data-ttu-id="922d6-103">屬性</span><span class="sxs-lookup"><span data-stu-id="922d6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="922d6-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="922d6-104">ID</span></span>|<span data-ttu-id="922d6-105">499</span><span class="sxs-lookup"><span data-stu-id="922d6-105">499</span></span>|  
|<span data-ttu-id="922d6-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="922d6-106">Keywords</span></span>|<span data-ttu-id="922d6-107">Troubleshooting，UserEvents，EndToEndMonitoring，ServiceModel，WFTracking，ServiceHost，WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="922d6-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="922d6-108">層級</span><span class="sxs-lookup"><span data-stu-id="922d6-108">Level</span></span>|<span data-ttu-id="922d6-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="922d6-109">LogAlways</span></span>|  
|<span data-ttu-id="922d6-110">通路</span><span class="sxs-lookup"><span data-stu-id="922d6-110">Channel</span></span>|<span data-ttu-id="922d6-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="922d6-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="922d6-112">描述</span><span class="sxs-lookup"><span data-stu-id="922d6-112">Description</span></span>  

 <span data-ttu-id="922d6-113">當傳輸事件發生時，就會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="922d6-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="922d6-114">訊息</span><span class="sxs-lookup"><span data-stu-id="922d6-114">Message</span></span>  

 <span data-ttu-id="922d6-115">已發出傳輸事件。</span><span class="sxs-lookup"><span data-stu-id="922d6-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="922d6-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="922d6-116">Details</span></span>  
  
|<span data-ttu-id="922d6-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="922d6-117">Data Item Name</span></span>|<span data-ttu-id="922d6-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="922d6-118">Data Item Type</span></span>|<span data-ttu-id="922d6-119">描述</span><span class="sxs-lookup"><span data-stu-id="922d6-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="922d6-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="922d6-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="922d6-121">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="922d6-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="922d6-122">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName '。</span><span class="sxs-lookup"><span data-stu-id="922d6-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="922d6-123">範例： ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '。</span><span class="sxs-lookup"><span data-stu-id="922d6-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="922d6-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="922d6-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="922d6-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="922d6-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
