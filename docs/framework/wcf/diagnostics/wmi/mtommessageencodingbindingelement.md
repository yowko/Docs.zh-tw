---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: ad4f2cc3b03111854d10d6a1c1128f090a629a07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490970"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="4d40d-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="4d40d-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="4d40d-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="4d40d-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d40d-104">語法</span><span class="sxs-lookup"><span data-stu-id="4d40d-104">Syntax</span></span>  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4d40d-105">方法</span><span class="sxs-lookup"><span data-stu-id="4d40d-105">Methods</span></span>  
 <span data-ttu-id="4d40d-106">MtomMessageEncodingBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="4d40d-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4d40d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="4d40d-107">Properties</span></span>  
 <span data-ttu-id="4d40d-108">MtomMessageEncodingBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4d40d-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="4d40d-109">編碼</span><span class="sxs-lookup"><span data-stu-id="4d40d-109">Encoding</span></span>  
 <span data-ttu-id="4d40d-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="4d40d-110">Data type: string</span></span>  
  
 <span data-ttu-id="4d40d-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="4d40d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d40d-112">要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="4d40d-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="4d40d-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="4d40d-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="4d40d-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="4d40d-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="4d40d-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="4d40d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d40d-116">定義可同時讀取之訊息數目 (在不配置新讀取器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="4d40d-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="4d40d-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="4d40d-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="4d40d-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="4d40d-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="4d40d-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="4d40d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d40d-120">定義可同時傳送之訊息數目 (在不配置新寫入器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="4d40d-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="4d40d-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="4d40d-121">ReaderQuotas</span></span>  
 <span data-ttu-id="4d40d-122">資料類型：XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="4d40d-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="4d40d-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="4d40d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d40d-124">讀取器的配額。</span><span class="sxs-lookup"><span data-stu-id="4d40d-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d40d-125">需求</span><span class="sxs-lookup"><span data-stu-id="4d40d-125">Requirements</span></span>  
  
|<span data-ttu-id="4d40d-126">MOF</span><span class="sxs-lookup"><span data-stu-id="4d40d-126">MOF</span></span>|<span data-ttu-id="4d40d-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="4d40d-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4d40d-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="4d40d-128">Namespace</span></span>|<span data-ttu-id="4d40d-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="4d40d-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d40d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d40d-130">See also</span></span>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
