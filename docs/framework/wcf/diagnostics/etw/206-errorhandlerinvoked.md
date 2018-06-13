---
title: 206 - ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: 40a92d77c57728249569a854eab8767ff371bca2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458815"
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="fe4f9-102">206 - ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="fe4f9-102">206 - ErrorHandlerInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="fe4f9-103">屬性</span><span class="sxs-lookup"><span data-stu-id="fe4f9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fe4f9-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="fe4f9-104">ID</span></span>|<span data-ttu-id="fe4f9-105">206</span><span class="sxs-lookup"><span data-stu-id="fe4f9-105">206</span></span>|  
|<span data-ttu-id="fe4f9-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="fe4f9-106">Keywords</span></span>|<span data-ttu-id="fe4f9-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fe4f9-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="fe4f9-108">層級</span><span class="sxs-lookup"><span data-stu-id="fe4f9-108">Level</span></span>|<span data-ttu-id="fe4f9-109">資訊</span><span class="sxs-lookup"><span data-stu-id="fe4f9-109">Information</span></span>|  
|<span data-ttu-id="fe4f9-110">通道</span><span class="sxs-lookup"><span data-stu-id="fe4f9-110">Channel</span></span>|<span data-ttu-id="fe4f9-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="fe4f9-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fe4f9-112">描述</span><span class="sxs-lookup"><span data-stu-id="fe4f9-112">Description</span></span>  
 <span data-ttu-id="fe4f9-113">這個事件是在 `ErrorHandler` 有機會處理服務作業中發生的例外狀況之後發出。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fe4f9-114">訊息</span><span class="sxs-lookup"><span data-stu-id="fe4f9-114">Message</span></span>  
 <span data-ttu-id="fe4f9-115">發送器叫用類型 '%1' 的 ErrorHandler 與類型 '%3' 的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="fe4f9-116">ErrorHandled == '%2'。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fe4f9-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fe4f9-117">Details</span></span>  
  
|<span data-ttu-id="fe4f9-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="fe4f9-118">Data Item Name</span></span>|<span data-ttu-id="fe4f9-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="fe4f9-119">Data Item Type</span></span>|<span data-ttu-id="fe4f9-120">描述</span><span class="sxs-lookup"><span data-stu-id="fe4f9-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fe4f9-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="fe4f9-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="fe4f9-122">已叫用 `ErrorHandler` 之類型的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="fe4f9-123">Handled</span><span class="sxs-lookup"><span data-stu-id="fe4f9-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="fe4f9-124">如果錯誤處理常式已處理錯誤，則為 `true`，否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="fe4f9-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="fe4f9-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="fe4f9-126">已處理之例外狀況的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="fe4f9-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="fe4f9-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="fe4f9-128">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="fe4f9-129">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="fe4f9-130">範例: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="fe4f9-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fe4f9-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="fe4f9-132">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="fe4f9-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
