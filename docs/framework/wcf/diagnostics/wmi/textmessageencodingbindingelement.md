---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 2371c38aebe2bd8d6da93d702801556fad986ef9
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49372205"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="fc73e-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="fc73e-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="fc73e-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="fc73e-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc73e-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc73e-104">Syntax</span></span>  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="fc73e-105">方法</span><span class="sxs-lookup"><span data-stu-id="fc73e-105">Methods</span></span>  
 <span data-ttu-id="fc73e-106">TextMessageEncodingBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="fc73e-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fc73e-107">屬性</span><span class="sxs-lookup"><span data-stu-id="fc73e-107">Properties</span></span>  
 <span data-ttu-id="fc73e-108">TextMessageEncodingBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="fc73e-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="fc73e-109">編碼</span><span class="sxs-lookup"><span data-stu-id="fc73e-109">Encoding</span></span>  
 <span data-ttu-id="fc73e-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="fc73e-110">Data type: string</span></span>  
  
 <span data-ttu-id="fc73e-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="fc73e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc73e-112">要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="fc73e-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="fc73e-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="fc73e-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="fc73e-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="fc73e-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="fc73e-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="fc73e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc73e-116">定義可同時讀取之訊息數目 (在不配置新讀取器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="fc73e-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="fc73e-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="fc73e-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="fc73e-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="fc73e-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="fc73e-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="fc73e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc73e-120">定義可同時傳送之訊息數目 (在不配置新寫入器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="fc73e-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="fc73e-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="fc73e-121">ReaderQuotas</span></span>  
 <span data-ttu-id="fc73e-122">資料型別：XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="fc73e-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="fc73e-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="fc73e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc73e-124">讀取器的配額。</span><span class="sxs-lookup"><span data-stu-id="fc73e-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc73e-125">需求</span><span class="sxs-lookup"><span data-stu-id="fc73e-125">Requirements</span></span>  
  
|<span data-ttu-id="fc73e-126">MOF</span><span class="sxs-lookup"><span data-stu-id="fc73e-126">MOF</span></span>|<span data-ttu-id="fc73e-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="fc73e-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fc73e-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="fc73e-128">Namespace</span></span>|<span data-ttu-id="fc73e-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="fc73e-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc73e-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc73e-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
