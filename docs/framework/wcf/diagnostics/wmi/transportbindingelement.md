---
title: TransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c2605e1a1f88434a9052059ac3ebdce429d6d6c8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="transportbindingelement"></a><span data-ttu-id="1f285-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="1f285-102">TransportBindingElement</span></span>
<span data-ttu-id="1f285-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="1f285-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f285-104">語法</span><span class="sxs-lookup"><span data-stu-id="1f285-104">Syntax</span></span>  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1f285-105">方法</span><span class="sxs-lookup"><span data-stu-id="1f285-105">Methods</span></span>  
 <span data-ttu-id="1f285-106">TransportBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="1f285-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1f285-107">屬性</span><span class="sxs-lookup"><span data-stu-id="1f285-107">Properties</span></span>  
 <span data-ttu-id="1f285-108">TransportBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="1f285-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="1f285-109">ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="1f285-109">ManualAddressing</span></span>  
 <span data-ttu-id="1f285-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="1f285-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="1f285-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="1f285-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f285-112">指定使用者是否要取得訊息定址控制權的布林值。</span><span class="sxs-lookup"><span data-stu-id="1f285-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="1f285-113">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="1f285-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="1f285-114">資料型別：sint64</span><span class="sxs-lookup"><span data-stu-id="1f285-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="1f285-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="1f285-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f285-116">繫結的緩衝集區大小上限。</span><span class="sxs-lookup"><span data-stu-id="1f285-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="1f285-117">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="1f285-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="1f285-118">資料型別：sint64</span><span class="sxs-lookup"><span data-stu-id="1f285-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="1f285-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="1f285-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f285-120">此繫結所處理之訊息的大小上限。</span><span class="sxs-lookup"><span data-stu-id="1f285-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="1f285-121">配置</span><span class="sxs-lookup"><span data-stu-id="1f285-121">Scheme</span></span>  
 <span data-ttu-id="1f285-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="1f285-122">Data type: string</span></span>  
  
 <span data-ttu-id="1f285-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="1f285-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f285-124">傳輸的 URI 配置。</span><span class="sxs-lookup"><span data-stu-id="1f285-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f285-125">需求</span><span class="sxs-lookup"><span data-stu-id="1f285-125">Requirements</span></span>  
  
|<span data-ttu-id="1f285-126">MOF</span><span class="sxs-lookup"><span data-stu-id="1f285-126">MOF</span></span>|<span data-ttu-id="1f285-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="1f285-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1f285-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="1f285-128">Namespace</span></span>|<span data-ttu-id="1f285-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="1f285-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f285-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f285-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
