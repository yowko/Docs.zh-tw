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
ms.openlocfilehash: 867b4a2b84a28dff4e3b9e4fc9d3c52065de212f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="f5e21-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="f5e21-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="f5e21-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="f5e21-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5e21-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5e21-104">Syntax</span></span>  
  
```  
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f5e21-105">方法</span><span class="sxs-lookup"><span data-stu-id="f5e21-105">Methods</span></span>  
 <span data-ttu-id="f5e21-106">MtomMessageEncodingBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="f5e21-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f5e21-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f5e21-107">Properties</span></span>  
 <span data-ttu-id="f5e21-108">MtomMessageEncodingBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f5e21-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="f5e21-109">編碼</span><span class="sxs-lookup"><span data-stu-id="f5e21-109">Encoding</span></span>  
 <span data-ttu-id="f5e21-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="f5e21-110">Data type: string</span></span>  
  
 <span data-ttu-id="f5e21-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f5e21-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f5e21-112">要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f5e21-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="f5e21-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="f5e21-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="f5e21-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="f5e21-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="f5e21-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f5e21-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f5e21-116">定義可同時讀取之訊息數目 (在不配置新讀取器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="f5e21-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="f5e21-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="f5e21-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="f5e21-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="f5e21-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="f5e21-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f5e21-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f5e21-120">定義可同時傳送之訊息數目 (在不配置新寫入器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="f5e21-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="f5e21-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="f5e21-121">ReaderQuotas</span></span>  
 <span data-ttu-id="f5e21-122">資料型別：XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="f5e21-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="f5e21-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f5e21-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f5e21-124">讀取器的配額。</span><span class="sxs-lookup"><span data-stu-id="f5e21-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5e21-125">需求</span><span class="sxs-lookup"><span data-stu-id="f5e21-125">Requirements</span></span>  
  
|<span data-ttu-id="f5e21-126">MOF</span><span class="sxs-lookup"><span data-stu-id="f5e21-126">MOF</span></span>|<span data-ttu-id="f5e21-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="f5e21-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f5e21-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="f5e21-128">Namespace</span></span>|<span data-ttu-id="f5e21-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="f5e21-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5e21-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5e21-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
