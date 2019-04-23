---
title: 版本相容序列化回呼
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OnDeserializedAttribute [WCF]
- OnDeserializingAttribute [WCF]
- OnSerializingAttribute [WCF]
- serialization [WCF], setting default values
- OnSerializedAttribute [WCF]
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
ms.openlocfilehash: da13f9989b427da047c4a94f77907847ed2ae4d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124627"
---
# <a name="version-tolerant-serialization-callbacks"></a><span data-ttu-id="8e9d8-102">版本相容序列化回呼</span><span class="sxs-lookup"><span data-stu-id="8e9d8-102">Version-Tolerant Serialization Callbacks</span></span>
<span data-ttu-id="8e9d8-103">資料合約程式設計模型完整支援 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 和 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 類別所支援的版本相容序列化回呼方法。</span><span class="sxs-lookup"><span data-stu-id="8e9d8-103">The data contract programming model fully supports the version-tolerant serialization callback methods that the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes support.</span></span>  
  
## <a name="version-tolerant-attributes"></a><span data-ttu-id="8e9d8-104">版本相容的屬性</span><span class="sxs-lookup"><span data-stu-id="8e9d8-104">Version-Tolerant Attributes</span></span>  
 <span data-ttu-id="8e9d8-105">回呼屬性有四個。</span><span class="sxs-lookup"><span data-stu-id="8e9d8-105">There are four callback attributes.</span></span> <span data-ttu-id="8e9d8-106">每個屬性都可以套用至序列化/還原序列化引擎在不同時間呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="8e9d8-106">Each attribute can be applied to a method that the serialization/deserialization engine calls at various times.</span></span> <span data-ttu-id="8e9d8-107">下表說明何時使用各個屬性。</span><span class="sxs-lookup"><span data-stu-id="8e9d8-107">The table below explains when to use each attribute.</span></span>  
  
|<span data-ttu-id="8e9d8-108">屬性</span><span class="sxs-lookup"><span data-stu-id="8e9d8-108">Attribute</span></span>|<span data-ttu-id="8e9d8-109">呼叫對應方法的時機</span><span class="sxs-lookup"><span data-stu-id="8e9d8-109">When the corresponding method is called</span></span>|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="8e9d8-110">在序列化型別之前呼叫。</span><span class="sxs-lookup"><span data-stu-id="8e9d8-110">Called before serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="8e9d8-111">在序列化型別之後呼叫。</span><span class="sxs-lookup"><span data-stu-id="8e9d8-111">Called after serializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="8e9d8-112">在還原序列化型別之前呼叫。</span><span class="sxs-lookup"><span data-stu-id="8e9d8-112">Called before deserializing the type.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="8e9d8-113">在還原序列化型別之後呼叫。</span><span class="sxs-lookup"><span data-stu-id="8e9d8-113">Called after deserializing the type.</span></span>|  
  
 <span data-ttu-id="8e9d8-114">這些方法必須接受 <xref:System.Runtime.Serialization.StreamingContext> 參數。</span><span class="sxs-lookup"><span data-stu-id="8e9d8-114">The methods must accept a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span>  
  
 <span data-ttu-id="8e9d8-115">這些方法主要是搭配版本處理或初始化使用。</span><span class="sxs-lookup"><span data-stu-id="8e9d8-115">These methods are primarily intended for use with versioning or initialization.</span></span> <span data-ttu-id="8e9d8-116">在還原序列化期間，不會呼叫建構函式。</span><span class="sxs-lookup"><span data-stu-id="8e9d8-116">During deserialization, no constructors are called.</span></span> <span data-ttu-id="8e9d8-117">因此，如果資料成員的資料在傳入資料流中遺失 (例如，當資料來自遺失某些資料成員的舊版型別時)，則這些資料成員可能無法正確地初始化 (做為預設值)。</span><span class="sxs-lookup"><span data-stu-id="8e9d8-117">Therefore, data members may not be correctly initialized (to intended default values) if the data for these members is missing in the incoming stream, for example, if the data comes from a previous version of a type that is missing some data members.</span></span> <span data-ttu-id="8e9d8-118">如果要修正這個問題，請使用以 <xref:System.Runtime.Serialization.OnDeserializingAttribute> 標示的回呼方法，如下例中所示。</span><span class="sxs-lookup"><span data-stu-id="8e9d8-118">To correct this, use the callback method marked with the <xref:System.Runtime.Serialization.OnDeserializingAttribute>, as shown in the following example.</span></span>  
  
 <span data-ttu-id="8e9d8-119">每種型別只有一個方法可以標上前述各個回呼屬性。</span><span class="sxs-lookup"><span data-stu-id="8e9d8-119">You can mark only one method per type with each of the preceding callback attributes.</span></span>  
  
### <a name="example"></a><span data-ttu-id="8e9d8-120">範例</span><span class="sxs-lookup"><span data-stu-id="8e9d8-120">Example</span></span>  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="8e9d8-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e9d8-121">See also</span></span>

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [<span data-ttu-id="8e9d8-122">版本相容序列化</span><span class="sxs-lookup"><span data-stu-id="8e9d8-122">Version Tolerant Serialization</span></span>](../../../../docs/standard/serialization/version-tolerant-serialization.md)
