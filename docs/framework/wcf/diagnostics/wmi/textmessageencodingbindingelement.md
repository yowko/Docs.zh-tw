---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 188a766807cd779ac51df390b1332641584dbb06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662708"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="3df09-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="3df09-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="3df09-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="3df09-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3df09-104">語法</span><span class="sxs-lookup"><span data-stu-id="3df09-104">Syntax</span></span>  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3df09-105">方法</span><span class="sxs-lookup"><span data-stu-id="3df09-105">Methods</span></span>  
 <span data-ttu-id="3df09-106">TextMessageEncodingBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="3df09-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3df09-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3df09-107">Properties</span></span>  
 <span data-ttu-id="3df09-108">TextMessageEncodingBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="3df09-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="3df09-109">編碼</span><span class="sxs-lookup"><span data-stu-id="3df09-109">Encoding</span></span>  
 <span data-ttu-id="3df09-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="3df09-110">Data type: string</span></span>  
  
 <span data-ttu-id="3df09-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="3df09-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3df09-112">要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="3df09-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="3df09-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="3df09-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="3df09-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="3df09-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="3df09-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="3df09-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3df09-116">定義可同時讀取之訊息數目 (在不配置新讀取器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="3df09-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="3df09-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="3df09-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="3df09-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="3df09-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="3df09-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="3df09-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3df09-120">定義可同時傳送之訊息數目 (在不配置新寫入器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="3df09-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="3df09-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="3df09-121">ReaderQuotas</span></span>  
 <span data-ttu-id="3df09-122">資料類型：XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="3df09-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="3df09-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="3df09-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3df09-124">讀取器的配額。</span><span class="sxs-lookup"><span data-stu-id="3df09-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3df09-125">需求</span><span class="sxs-lookup"><span data-stu-id="3df09-125">Requirements</span></span>  
  
|<span data-ttu-id="3df09-126">MOF</span><span class="sxs-lookup"><span data-stu-id="3df09-126">MOF</span></span>|<span data-ttu-id="3df09-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="3df09-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3df09-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="3df09-128">Namespace</span></span>|<span data-ttu-id="3df09-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="3df09-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3df09-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3df09-130">See also</span></span>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
