---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: 330496d5f0f80affcb6bc44a1f66f4321a635f00
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580586"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="83b30-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="83b30-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="83b30-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="83b30-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83b30-104">語法</span><span class="sxs-lookup"><span data-stu-id="83b30-104">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="83b30-105">方法</span><span class="sxs-lookup"><span data-stu-id="83b30-105">Methods</span></span>  
 <span data-ttu-id="83b30-106">BinaryMessageEncodingBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="83b30-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="83b30-107">屬性</span><span class="sxs-lookup"><span data-stu-id="83b30-107">Properties</span></span>  
 <span data-ttu-id="83b30-108">BinaryMessageEncodingBindingElement 類別具有下列屬性。</span><span class="sxs-lookup"><span data-stu-id="83b30-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="83b30-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="83b30-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="83b30-110">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="83b30-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="83b30-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="83b30-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="83b30-112">定義可同時讀取之訊息數目 (在不配置新讀取器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="83b30-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="83b30-113">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="83b30-113">MaxSessionSize</span></span>  
 <span data-ttu-id="83b30-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="83b30-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="83b30-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="83b30-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="83b30-116">此值可指定用於編碼的緩衝區大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="83b30-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="83b30-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="83b30-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="83b30-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="83b30-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="83b30-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="83b30-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="83b30-120">定義可同時傳送之訊息數目 (在不配置新寫入器的情況下) 的整數。</span><span class="sxs-lookup"><span data-stu-id="83b30-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="83b30-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="83b30-121">ReaderQuotas</span></span>  
 <span data-ttu-id="83b30-122">資料類型：XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="83b30-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="83b30-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="83b30-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="83b30-124">讀取器的配額。</span><span class="sxs-lookup"><span data-stu-id="83b30-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83b30-125">需求</span><span class="sxs-lookup"><span data-stu-id="83b30-125">Requirements</span></span>  
  
|<span data-ttu-id="83b30-126">MOF</span><span class="sxs-lookup"><span data-stu-id="83b30-126">MOF</span></span>|<span data-ttu-id="83b30-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="83b30-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="83b30-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="83b30-128">Namespace</span></span>|<span data-ttu-id="83b30-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="83b30-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83b30-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83b30-130">See also</span></span>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
