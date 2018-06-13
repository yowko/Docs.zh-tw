---
title: 207 - FaultProviderInvoked
ms.date: 03/30/2017
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
ms.openlocfilehash: 9f97e74e7685d57b487f456625826ee9cd8e1760
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457344"
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="0c4de-102">207 - FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="0c4de-102">207 - FaultProviderInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="0c4de-103">屬性</span><span class="sxs-lookup"><span data-stu-id="0c4de-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0c4de-104">ID</span><span class="sxs-lookup"><span data-stu-id="0c4de-104">ID</span></span>|<span data-ttu-id="0c4de-105">207</span><span class="sxs-lookup"><span data-stu-id="0c4de-105">207</span></span>|  
|<span data-ttu-id="0c4de-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="0c4de-106">Keywords</span></span>|<span data-ttu-id="0c4de-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0c4de-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="0c4de-108">層級</span><span class="sxs-lookup"><span data-stu-id="0c4de-108">Level</span></span>|<span data-ttu-id="0c4de-109">資訊</span><span class="sxs-lookup"><span data-stu-id="0c4de-109">Information</span></span>|  
|<span data-ttu-id="0c4de-110">通道</span><span class="sxs-lookup"><span data-stu-id="0c4de-110">Channel</span></span>|<span data-ttu-id="0c4de-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="0c4de-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0c4de-112">描述</span><span class="sxs-lookup"><span data-stu-id="0c4de-112">Description</span></span>  
 <span data-ttu-id="0c4de-113">此事件是在已叫用 `FaultProvider` 之後發出。</span><span class="sxs-lookup"><span data-stu-id="0c4de-113">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0c4de-114">訊息</span><span class="sxs-lookup"><span data-stu-id="0c4de-114">Message</span></span>  
 <span data-ttu-id="0c4de-115">發送器已叫用型別為 '%1' 的 FaultProvider，其例外狀況型別為 '%2'。</span><span class="sxs-lookup"><span data-stu-id="0c4de-115">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0c4de-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0c4de-116">Details</span></span>  
  
|<span data-ttu-id="0c4de-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="0c4de-117">Data Item Name</span></span>|<span data-ttu-id="0c4de-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="0c4de-118">Data Item Type</span></span>|<span data-ttu-id="0c4de-119">描述</span><span class="sxs-lookup"><span data-stu-id="0c4de-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0c4de-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="0c4de-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="0c4de-121">已叫用 `FaultProvider` 之類型的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="0c4de-121">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="0c4de-122">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="0c4de-122">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="0c4de-123">`FaultProvider` 已處理之例外狀況的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="0c4de-123">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="0c4de-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="0c4de-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="0c4de-125">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="0c4de-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="0c4de-126">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="0c4de-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="0c4de-127">範例: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="0c4de-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="0c4de-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0c4de-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="0c4de-129">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="0c4de-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
