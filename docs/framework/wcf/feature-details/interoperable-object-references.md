---
title: 互通物件參考
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: ada9084f6ac3c97dc641571c0cb8379a2fac68a8
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2019
ms.locfileid: "59610635"
---
# <a name="interoperable-object-references"></a><span data-ttu-id="5c014-102">互通物件參考</span><span class="sxs-lookup"><span data-stu-id="5c014-102">Interoperable object references</span></span>
<span data-ttu-id="5c014-103">根據預設，<xref:System.Runtime.Serialization.DataContractSerializer>將物件序列化的值。</span><span class="sxs-lookup"><span data-stu-id="5c014-103">By default, <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="5c014-104">您可以使用<xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>屬性，指示資料合約序列化程式，將物件序列化時保留物件參考。</span><span class="sxs-lookup"><span data-stu-id="5c014-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the data contract serializer to preserve object references when serializing objects.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="5c014-105">產生的 XML</span><span class="sxs-lookup"><span data-stu-id="5c014-105">Generated XML</span></span>  
 <span data-ttu-id="5c014-106">做為範例，請考量下列物件：</span><span class="sxs-lookup"><span data-stu-id="5c014-106">As an example, consider the following object:</span></span>  
  
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
  
 <span data-ttu-id="5c014-107">在 <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> 設為 `false` (預設值) 的情況下，會產生以下 XML：</span><span class="sxs-lookup"><span data-stu-id="5c014-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="5c014-108">在 <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> 設為 `true` 的情況下，會產生以下 XML：</span><span class="sxs-lookup"><span data-stu-id="5c014-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 <span data-ttu-id="5c014-109">不過，<xref:System.Runtime.Serialization.XsdDataContractExporter>並未說明`id`並`ref`它的結構描述中的屬性，即使`preserveObjectReferences`屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="5c014-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> doesn't describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="5c014-110">使用 IsReference</span><span class="sxs-lookup"><span data-stu-id="5c014-110">Using IsReference</span></span>  
 <span data-ttu-id="5c014-111">若要產生有效根據結構描述的物件參考資訊，請套用<xref:System.Runtime.Serialization.DataContractAttribute>屬性設為型別，並設定<xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>旗標設為`true`。</span><span class="sxs-lookup"><span data-stu-id="5c014-111">To generate object reference information that's valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="5c014-112">下列範例會修改類別`X`加上一個範例中`IsReference`:</span><span class="sxs-lookup"><span data-stu-id="5c014-112">The following example modifies class `X` in the previous example by adding `IsReference`:</span></span>  
  
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

 <span data-ttu-id="5c014-113">產生的 XML 如下：</span><span class="sxs-lookup"><span data-stu-id="5c014-113">The generated XML is as follows:</span></span>  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A> 
    <B ref="1"></B>  
</X>
```  
  
 <span data-ttu-id="5c014-114">使用 `IsReference` 確保往返的訊息相符。</span><span class="sxs-lookup"><span data-stu-id="5c014-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="5c014-115">未安裝，當從結構描述產生類型的 XML 輸出的型別不一定與原本預期的結構描述相容。</span><span class="sxs-lookup"><span data-stu-id="5c014-115">Without it, when a type is generated from schema, the XML output for that type isn't necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="5c014-116">換句話說，即使 `id` 和 `ref` 屬性已序列化，原始結構描述仍可能禁止這些屬性 (或所有屬性) 出現在該 XML 中。</span><span class="sxs-lookup"><span data-stu-id="5c014-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="5c014-117">具有`IsReference`套用至資料成員，該成員就會被視為*referenceable*時往返。</span><span class="sxs-lookup"><span data-stu-id="5c014-117">With `IsReference` applied to a data member, the member continues to be recognized as *referenceable* when round-tripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c014-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c014-118">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
