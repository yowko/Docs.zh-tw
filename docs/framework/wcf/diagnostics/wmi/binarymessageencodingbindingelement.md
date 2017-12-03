---
title: BinaryMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45f80b9ac7ca052ea3a8d7d89b35413b167eacfa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="ef15d-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="ef15d-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="ef15d-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="ef15d-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef15d-104">語法</span><span class="sxs-lookup"><span data-stu-id="ef15d-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ef15d-105">方法</span><span class="sxs-lookup"><span data-stu-id="ef15d-105">Methods</span></span>  
 <span data-ttu-id="ef15d-106">BinaryMessageEncodingBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="ef15d-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ef15d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ef15d-107">Properties</span></span>  
 <span data-ttu-id="ef15d-108">BinaryMessageEncodingBindingElement 類別具有下列屬性。</span><span class="sxs-lookup"><span data-stu-id="ef15d-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="ef15d-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="ef15d-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="ef15d-110">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="ef15d-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="ef15d-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ef15d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef15d-112">定義可同時讀取之訊息數目 (在不配置新讀取器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="ef15d-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="ef15d-113">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="ef15d-113">MaxSessionSize</span></span>  
 <span data-ttu-id="ef15d-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="ef15d-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="ef15d-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ef15d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef15d-116">此值可指定用於編碼的緩衝區大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="ef15d-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="ef15d-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="ef15d-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="ef15d-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="ef15d-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="ef15d-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ef15d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef15d-120">定義可同時傳送之訊息數目 (在不配置新寫入器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="ef15d-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="ef15d-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="ef15d-121">ReaderQuotas</span></span>  
 <span data-ttu-id="ef15d-122">資料型別：XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="ef15d-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="ef15d-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ef15d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef15d-124">讀取器的配額。</span><span class="sxs-lookup"><span data-stu-id="ef15d-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef15d-125">需求</span><span class="sxs-lookup"><span data-stu-id="ef15d-125">Requirements</span></span>  
  
|<span data-ttu-id="ef15d-126">MOF</span><span class="sxs-lookup"><span data-stu-id="ef15d-126">MOF</span></span>|<span data-ttu-id="ef15d-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="ef15d-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ef15d-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="ef15d-128">Namespace</span></span>|<span data-ttu-id="ef15d-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="ef15d-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef15d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef15d-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
