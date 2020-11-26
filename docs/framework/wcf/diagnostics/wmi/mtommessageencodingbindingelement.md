---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: b4d8503543c93d0112fc39e4b2dba5434bc56472
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237400"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="f780b-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="f780b-102">MtomMessageEncodingBindingElement</span></span>

<span data-ttu-id="f780b-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="f780b-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f780b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f780b-104">Syntax</span></span>  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f780b-105">方法</span><span class="sxs-lookup"><span data-stu-id="f780b-105">Methods</span></span>  

 <span data-ttu-id="f780b-106">MtomMessageEncodingBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="f780b-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f780b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f780b-107">Properties</span></span>  

 <span data-ttu-id="f780b-108">MtomMessageEncodingBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f780b-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="f780b-109">編碼</span><span class="sxs-lookup"><span data-stu-id="f780b-109">Encoding</span></span>  

 <span data-ttu-id="f780b-110">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="f780b-110">Data type: string</span></span>  
  
 <span data-ttu-id="f780b-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f780b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f780b-112">要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f780b-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="f780b-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="f780b-113">MaxReadPoolSize</span></span>  

 <span data-ttu-id="f780b-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="f780b-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="f780b-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f780b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f780b-116">定義可同時讀取之訊息數目 (在不配置新讀取器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="f780b-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="f780b-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="f780b-117">MaxWritePoolSize</span></span>  

 <span data-ttu-id="f780b-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="f780b-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="f780b-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f780b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f780b-120">定義可同時傳送之訊息數目 (在不配置新寫入器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="f780b-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="f780b-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="f780b-121">ReaderQuotas</span></span>  

 <span data-ttu-id="f780b-122">資料型別：XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="f780b-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="f780b-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f780b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f780b-124">讀取器的配額。</span><span class="sxs-lookup"><span data-stu-id="f780b-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f780b-125">規格需求</span><span class="sxs-lookup"><span data-stu-id="f780b-125">Requirements</span></span>  
  
|<span data-ttu-id="f780b-126">MOF</span><span class="sxs-lookup"><span data-stu-id="f780b-126">MOF</span></span>|<span data-ttu-id="f780b-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="f780b-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f780b-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="f780b-128">Namespace</span></span>|<span data-ttu-id="f780b-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="f780b-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f780b-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f780b-130">See also</span></span>

- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
