---
title: 可交互操作的物件引用
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: 0927f217a1666f8f27ca9c3e68f80a96b9c0f2b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184697"
---
# <a name="interoperable-object-references"></a><span data-ttu-id="5a188-102">可交互操作的物件引用</span><span class="sxs-lookup"><span data-stu-id="5a188-102">Interoperable object references</span></span>
<span data-ttu-id="5a188-103">預設情況下，<xref:System.Runtime.Serialization.DataContractSerializer>按值序列化物件。</span><span class="sxs-lookup"><span data-stu-id="5a188-103">By default, <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="5a188-104">可以使用 屬性<xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>指示資料協定序列化器在序列化物件時保留物件引用。</span><span class="sxs-lookup"><span data-stu-id="5a188-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the data contract serializer to preserve object references when serializing objects.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="5a188-105">產生的 XML</span><span class="sxs-lookup"><span data-stu-id="5a188-105">Generated XML</span></span>  
 <span data-ttu-id="5a188-106">做為範例，請考量下列物件：</span><span class="sxs-lookup"><span data-stu-id="5a188-106">As an example, consider the following object:</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="5a188-107">在 <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> 設為 `false` (預設值) 的情況下，會產生以下 XML：</span><span class="sxs-lookup"><span data-stu-id="5a188-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="5a188-108">在 <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> 設為 `true` 的情況下，會產生以下 XML：</span><span class="sxs-lookup"><span data-stu-id="5a188-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 <span data-ttu-id="5a188-109">但是，<xref:System.Runtime.Serialization.XsdDataContractExporter>即使`preserveObjectReferences`屬性設置為`true`，`id`也不會在其架構中描述 和`ref`屬性。</span><span class="sxs-lookup"><span data-stu-id="5a188-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> doesn't describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="5a188-110">使用 IsReference</span><span class="sxs-lookup"><span data-stu-id="5a188-110">Using IsReference</span></span>  
 <span data-ttu-id="5a188-111">要根據描述該資訊的架構生成有效的物件引用資訊，請將<xref:System.Runtime.Serialization.DataContractAttribute>屬性應用於類型，並將<xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>標誌設置為`true`。</span><span class="sxs-lookup"><span data-stu-id="5a188-111">To generate object reference information that's valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="5a188-112">以下示例通過添加`X``IsReference`：</span><span class="sxs-lookup"><span data-stu-id="5a188-112">The following example modifies class `X` in the previous example by adding `IsReference`:</span></span>  
  
```csharp
[DataContract(IsReference=true)]
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
````

 <span data-ttu-id="5a188-113">產生的 XML 如下：</span><span class="sxs-lookup"><span data-stu-id="5a188-113">The generated XML is as follows:</span></span>  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A>
    <B ref="1"></B>  
</X>
```  
  
 <span data-ttu-id="5a188-114">使用 `IsReference` 確保往返的訊息相符。</span><span class="sxs-lookup"><span data-stu-id="5a188-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="5a188-115">如果沒有它，當從架構組建類型時，該類型的 XML 輸出不一定與最初假定的架構相容。</span><span class="sxs-lookup"><span data-stu-id="5a188-115">Without it, when a type is generated from schema, the XML output for that type isn't necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="5a188-116">換句話說，即使 `id` 和 `ref` 屬性已序列化，原始結構描述仍可能禁止這些屬性 (或所有屬性) 出現在該 XML 中。</span><span class="sxs-lookup"><span data-stu-id="5a188-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="5a188-117">應用於`IsReference`資料成員後，該成員在四捨五入時繼續被識別為*可引用*成員。</span><span class="sxs-lookup"><span data-stu-id="5a188-117">With `IsReference` applied to a data member, the member continues to be recognized as *referenceable* when round-tripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a188-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a188-118">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
