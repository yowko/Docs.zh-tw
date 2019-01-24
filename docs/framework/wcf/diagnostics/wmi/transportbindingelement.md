---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: 303e5523befb68c65bc50ee3933af58897929363
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668443"
---
# <a name="transportbindingelement"></a><span data-ttu-id="5e2e5-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="5e2e5-102">TransportBindingElement</span></span>
<span data-ttu-id="5e2e5-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="5e2e5-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e2e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="5e2e5-104">Syntax</span></span>  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5e2e5-105">方法</span><span class="sxs-lookup"><span data-stu-id="5e2e5-105">Methods</span></span>  
 <span data-ttu-id="5e2e5-106">TransportBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="5e2e5-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5e2e5-107">屬性</span><span class="sxs-lookup"><span data-stu-id="5e2e5-107">Properties</span></span>  
 <span data-ttu-id="5e2e5-108">TransportBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="5e2e5-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="5e2e5-109">ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="5e2e5-109">ManualAddressing</span></span>  
 <span data-ttu-id="5e2e5-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="5e2e5-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="5e2e5-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5e2e5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5e2e5-112">指定使用者是否要取得訊息定址控制權的布林值。</span><span class="sxs-lookup"><span data-stu-id="5e2e5-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="5e2e5-113">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="5e2e5-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="5e2e5-114">資料型別：sint64</span><span class="sxs-lookup"><span data-stu-id="5e2e5-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="5e2e5-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5e2e5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5e2e5-116">繫結的緩衝集區大小上限。</span><span class="sxs-lookup"><span data-stu-id="5e2e5-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="5e2e5-117">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="5e2e5-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="5e2e5-118">資料型別：sint64</span><span class="sxs-lookup"><span data-stu-id="5e2e5-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="5e2e5-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5e2e5-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5e2e5-120">此繫結所處理之訊息的大小上限。</span><span class="sxs-lookup"><span data-stu-id="5e2e5-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="5e2e5-121">配置</span><span class="sxs-lookup"><span data-stu-id="5e2e5-121">Scheme</span></span>  
 <span data-ttu-id="5e2e5-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="5e2e5-122">Data type: string</span></span>  
  
 <span data-ttu-id="5e2e5-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5e2e5-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5e2e5-124">傳輸的 URI 配置。</span><span class="sxs-lookup"><span data-stu-id="5e2e5-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e2e5-125">需求</span><span class="sxs-lookup"><span data-stu-id="5e2e5-125">Requirements</span></span>  
  
|<span data-ttu-id="5e2e5-126">MOF</span><span class="sxs-lookup"><span data-stu-id="5e2e5-126">MOF</span></span>|<span data-ttu-id="5e2e5-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="5e2e5-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5e2e5-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="5e2e5-128">Namespace</span></span>|<span data-ttu-id="5e2e5-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="5e2e5-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e2e5-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e2e5-130">See also</span></span>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
