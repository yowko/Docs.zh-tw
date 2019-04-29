---
title: 209 - MessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
ms.openlocfilehash: 24184c24b9affdf3a56d7968c02cf5354d690749
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781873"
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="23709-102">209 - MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="23709-102">209 - MessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="23709-103">屬性</span><span class="sxs-lookup"><span data-stu-id="23709-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="23709-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="23709-104">ID</span></span>|<span data-ttu-id="23709-105">209</span><span class="sxs-lookup"><span data-stu-id="23709-105">209</span></span>|  
|<span data-ttu-id="23709-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="23709-106">Keywords</span></span>|<span data-ttu-id="23709-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="23709-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="23709-108">層級</span><span class="sxs-lookup"><span data-stu-id="23709-108">Level</span></span>|<span data-ttu-id="23709-109">資訊</span><span class="sxs-lookup"><span data-stu-id="23709-109">Information</span></span>|  
|<span data-ttu-id="23709-110">通道</span><span class="sxs-lookup"><span data-stu-id="23709-110">Channel</span></span>|<span data-ttu-id="23709-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="23709-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="23709-112">描述</span><span class="sxs-lookup"><span data-stu-id="23709-112">Description</span></span>  
 <span data-ttu-id="23709-113">服務模型在訊息偵測器上叫用 `BeforeSend` 方法之後，即會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="23709-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="23709-114">訊息</span><span class="sxs-lookup"><span data-stu-id="23709-114">Message</span></span>  
 <span data-ttu-id="23709-115">發送器在型別 '%1' 的 MessageInspector 上叫用了 'BeforeSendRequest'。</span><span class="sxs-lookup"><span data-stu-id="23709-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="23709-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="23709-116">Details</span></span>  
  
|<span data-ttu-id="23709-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="23709-117">Data Item Name</span></span>|<span data-ttu-id="23709-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="23709-118">Data Item Type</span></span>|<span data-ttu-id="23709-119">描述</span><span class="sxs-lookup"><span data-stu-id="23709-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="23709-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="23709-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="23709-121">已叫用 `MessageInspector` 之類型的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="23709-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="23709-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="23709-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="23709-123">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="23709-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="23709-124">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="23709-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="23709-125">範例：' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="23709-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="23709-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="23709-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="23709-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="23709-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
