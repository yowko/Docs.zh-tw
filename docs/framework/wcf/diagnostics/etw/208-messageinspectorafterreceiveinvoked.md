---
title: 208 - MessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: dfb5f7b0-4346-4949-8104-351726b1f502
ms.openlocfilehash: 3499131fcb52f0a0ab6d0e78e165522b7092612f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781897"
---
# <a name="208---messageinspectorafterreceiveinvoked"></a><span data-ttu-id="3c9ff-102">208 - MessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="3c9ff-102">208 - MessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="3c9ff-103">屬性</span><span class="sxs-lookup"><span data-stu-id="3c9ff-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3c9ff-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="3c9ff-104">ID</span></span>|<span data-ttu-id="3c9ff-105">208</span><span class="sxs-lookup"><span data-stu-id="3c9ff-105">208</span></span>|  
|<span data-ttu-id="3c9ff-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="3c9ff-106">Keywords</span></span>|<span data-ttu-id="3c9ff-107">Troubleshooting，ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3c9ff-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="3c9ff-108">層級</span><span class="sxs-lookup"><span data-stu-id="3c9ff-108">Level</span></span>|<span data-ttu-id="3c9ff-109">資訊</span><span class="sxs-lookup"><span data-stu-id="3c9ff-109">Information</span></span>|  
|<span data-ttu-id="3c9ff-110">通道</span><span class="sxs-lookup"><span data-stu-id="3c9ff-110">Channel</span></span>|<span data-ttu-id="3c9ff-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="3c9ff-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3c9ff-112">描述</span><span class="sxs-lookup"><span data-stu-id="3c9ff-112">Description</span></span>  
 <span data-ttu-id="3c9ff-113">服務模型在訊息偵測器上叫用 `AfterReceive` 方法之後，即會發出此事件。</span><span class="sxs-lookup"><span data-stu-id="3c9ff-113">This event is emitted after the Service Model has invoked the `AfterReceive` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3c9ff-114">訊息</span><span class="sxs-lookup"><span data-stu-id="3c9ff-114">Message</span></span>  
 <span data-ttu-id="3c9ff-115">發送器在型別 '%1' 的 MessageInspector 上叫用了 'AfterReceiveReply'。</span><span class="sxs-lookup"><span data-stu-id="3c9ff-115">The Dispatcher invoked 'AfterReceiveReply' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3c9ff-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3c9ff-116">Details</span></span>  
  
|<span data-ttu-id="3c9ff-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="3c9ff-117">Data Item Name</span></span>|<span data-ttu-id="3c9ff-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="3c9ff-118">Data Item Type</span></span>|<span data-ttu-id="3c9ff-119">描述</span><span class="sxs-lookup"><span data-stu-id="3c9ff-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3c9ff-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="3c9ff-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="3c9ff-121">已叫用 `MessageInspector` 之類型的 CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="3c9ff-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="3c9ff-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="3c9ff-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="3c9ff-123">若為 Web 託管服務，此欄位會唯一識別 Web 階層架構中的服務。</span><span class="sxs-lookup"><span data-stu-id="3c9ff-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="3c9ff-124">其格式定義為 ' Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'。</span><span class="sxs-lookup"><span data-stu-id="3c9ff-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="3c9ff-125">範例：' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="3c9ff-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="3c9ff-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3c9ff-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="3c9ff-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="3c9ff-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
