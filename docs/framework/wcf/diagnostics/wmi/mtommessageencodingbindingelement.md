---
title: MtomMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3cc36d7daed1a2cfaf050cbfe9661951117ff66d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="21fe4-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="21fe4-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="21fe4-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="21fe4-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21fe4-104">語法</span><span class="sxs-lookup"><span data-stu-id="21fe4-104">Syntax</span></span>  
  
```  
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="21fe4-105">方法</span><span class="sxs-lookup"><span data-stu-id="21fe4-105">Methods</span></span>  
 <span data-ttu-id="21fe4-106">MtomMessageEncodingBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="21fe4-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="21fe4-107">屬性</span><span class="sxs-lookup"><span data-stu-id="21fe4-107">Properties</span></span>  
 <span data-ttu-id="21fe4-108">MtomMessageEncodingBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="21fe4-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="21fe4-109">編碼</span><span class="sxs-lookup"><span data-stu-id="21fe4-109">Encoding</span></span>  
 <span data-ttu-id="21fe4-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="21fe4-110">Data type: string</span></span>  
  
 <span data-ttu-id="21fe4-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="21fe4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="21fe4-112">要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="21fe4-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="21fe4-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="21fe4-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="21fe4-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="21fe4-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="21fe4-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="21fe4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="21fe4-116">定義可同時讀取之訊息數目 (在不配置新讀取器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="21fe4-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="21fe4-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="21fe4-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="21fe4-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="21fe4-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="21fe4-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="21fe4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="21fe4-120">定義可同時傳送之訊息數目 (在不配置新寫入器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="21fe4-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="21fe4-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="21fe4-121">ReaderQuotas</span></span>  
 <span data-ttu-id="21fe4-122">資料型別：XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="21fe4-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="21fe4-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="21fe4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="21fe4-124">讀取器的配額。</span><span class="sxs-lookup"><span data-stu-id="21fe4-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21fe4-125">需求</span><span class="sxs-lookup"><span data-stu-id="21fe4-125">Requirements</span></span>  
  
|<span data-ttu-id="21fe4-126">MOF</span><span class="sxs-lookup"><span data-stu-id="21fe4-126">MOF</span></span>|<span data-ttu-id="21fe4-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="21fe4-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="21fe4-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="21fe4-128">Namespace</span></span>|<span data-ttu-id="21fe4-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="21fe4-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21fe4-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="21fe4-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
