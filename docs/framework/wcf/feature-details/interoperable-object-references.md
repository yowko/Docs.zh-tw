---
title: 互通物件參考
ms.date: 03/30/2017
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: 5d2f7d93544cafab7cfe5d8dcbb8a4c5d5c5b576
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582414"
---
# <a name="interoperable-object-references"></a><span data-ttu-id="12859-102">互通物件參考</span><span class="sxs-lookup"><span data-stu-id="12859-102">Interoperable Object References</span></span>
<span data-ttu-id="12859-103">根據預設，<xref:System.Runtime.Serialization.DataContractSerializer> 會以傳值方式序列化物件。</span><span class="sxs-lookup"><span data-stu-id="12859-103">By default the <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="12859-104">您可以使用 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> 屬性，指示資料合約序列化程式在序列化此類型物件時保留物件參考。</span><span class="sxs-lookup"><span data-stu-id="12859-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the Data Contract Serializer to preserve object references when serializing objects of the type.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="12859-105">產生的 XML</span><span class="sxs-lookup"><span data-stu-id="12859-105">Generated XML</span></span>  
 <span data-ttu-id="12859-106">做為範例，請考量下列物件：</span><span class="sxs-lookup"><span data-stu-id="12859-106">As an example, consider the following object:</span></span>  
  
```  
[DataContract]  
public class X  
{  
    SomeClass someInstance = new SomeClass();  
    [DataMember]  
    public SomeClass A = someInstance;  
    [DataMember]  
    public SomeClass B = someInstance;  
}  
  
public class SomeClass   
{  
}  
```  
  
 <span data-ttu-id="12859-107">在 <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> 設為 `false` (預設值) 的情況下，會產生以下 XML：</span><span class="sxs-lookup"><span data-stu-id="12859-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="12859-108">在 <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> 設為 `true` 的情況下，會產生以下 XML：</span><span class="sxs-lookup"><span data-stu-id="12859-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1" />  
</X>  
```  
  
 <span data-ttu-id="12859-109">不過，即使 <xref:System.Runtime.Serialization.XsdDataContractExporter> 屬性 (Property) 設為 `id`，`ref` 仍不會在其結構描述中描述 `preserveObjectReferences` 和 `true` 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="12859-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> does not describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="12859-110">使用 IsReference</span><span class="sxs-lookup"><span data-stu-id="12859-110">Using IsReference</span></span>  
 <span data-ttu-id="12859-111">若要根據描述物件參考資訊的結構描述產生有效的物件參考資訊，請將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至某一個類型，並且將 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> 旗標設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="12859-111">To generate object reference information that is valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="12859-112">在上一個範例的類別 `IsReference` 中使用 `X`：</span><span class="sxs-lookup"><span data-stu-id="12859-112">Using `IsReference` in the previous example class `X`:</span></span>  
  
 `[DataContract(IsReference=true)] public class X`  
  
 `{`  
  
 `SomeClass someInstance = new SomeClass();`  
  
 `[DataMember]`  
  
 `public SomeClass A = someInstance;`  
  
 `[DataMember]`  
  
 `public SomeClass B = someInstance;`  
  
 `}`  
  
 `public class SomeClass`  
  
 `{`  
  
 `}`  
  
 <span data-ttu-id="12859-113">產生的 XML 如下：</span><span class="sxs-lookup"><span data-stu-id="12859-113">The generated XML is as follows:</span></span>  
  
 `<X>`  
  
 `<A id="1">`  
  
 `<Value>contents of A</Value>`  
  
 `</A>`  
  
 `<B ref="1">`  
  
 `</B>`  
  
 `</X>`  
  
 <span data-ttu-id="12859-114">使用 `IsReference` 確保往返的訊息相符。</span><span class="sxs-lookup"><span data-stu-id="12859-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="12859-115">否則，當某類型自結構描述產生時，針對該類型傳回的 XML，不一定與結構描述原本預期的類型相容。</span><span class="sxs-lookup"><span data-stu-id="12859-115">Without it, when a type is generated from schema, what is sent back as XML for that type is not necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="12859-116">換句話說，即使 `id` 和 `ref` 屬性已序列化，原始結構描述仍可能禁止這些屬性 (或所有屬性) 出現在該 XML 中。</span><span class="sxs-lookup"><span data-stu-id="12859-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="12859-117">在 `IsReference` 已套用至資料成員的情況下，該成員就會在往返時繼續被視為「可參考」。</span><span class="sxs-lookup"><span data-stu-id="12859-117">With `IsReference` applied to a data member, the member continues to be recognized as "referenceable" when roundtripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12859-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12859-118">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference%2A>
