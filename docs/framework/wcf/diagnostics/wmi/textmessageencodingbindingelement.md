---
title: TextMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 966f1ae06f5d7e0dacb8b7d450463c75f783ef1f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="c3e96-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="c3e96-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="c3e96-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="c3e96-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3e96-104">語法</span><span class="sxs-lookup"><span data-stu-id="c3e96-104">Syntax</span></span>  
  
```  
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c3e96-105">方法</span><span class="sxs-lookup"><span data-stu-id="c3e96-105">Methods</span></span>  
 <span data-ttu-id="c3e96-106">TextMessageEncodingBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="c3e96-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c3e96-107">屬性</span><span class="sxs-lookup"><span data-stu-id="c3e96-107">Properties</span></span>  
 <span data-ttu-id="c3e96-108">TextMessageEncodingBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="c3e96-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="c3e96-109">編碼</span><span class="sxs-lookup"><span data-stu-id="c3e96-109">Encoding</span></span>  
 <span data-ttu-id="c3e96-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="c3e96-110">Data type: string</span></span>  
  
 <span data-ttu-id="c3e96-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c3e96-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3e96-112">要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c3e96-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="c3e96-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="c3e96-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="c3e96-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="c3e96-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="c3e96-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c3e96-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3e96-116">定義可同時讀取之訊息數目 (在不配置新讀取器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="c3e96-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="c3e96-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="c3e96-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="c3e96-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="c3e96-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="c3e96-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c3e96-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3e96-120">定義可同時傳送之訊息數目 (在不配置新寫入器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="c3e96-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="c3e96-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="c3e96-121">ReaderQuotas</span></span>  
 <span data-ttu-id="c3e96-122">資料型別：XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="c3e96-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="c3e96-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c3e96-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3e96-124">讀取器的配額。</span><span class="sxs-lookup"><span data-stu-id="c3e96-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3e96-125">需求</span><span class="sxs-lookup"><span data-stu-id="c3e96-125">Requirements</span></span>  
  
|<span data-ttu-id="c3e96-126">MOF</span><span class="sxs-lookup"><span data-stu-id="c3e96-126">MOF</span></span>|<span data-ttu-id="c3e96-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="c3e96-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c3e96-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="c3e96-128">Namespace</span></span>|<span data-ttu-id="c3e96-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="c3e96-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3e96-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3e96-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
