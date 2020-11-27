---
title: 互通的物件參考
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: bf395c187c46e88406bfb81798c7e359b48255e3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263226"
---
# <a name="interoperable-object-references"></a><span data-ttu-id="fa647-102">互通的物件參考</span><span class="sxs-lookup"><span data-stu-id="fa647-102">Interoperable object references</span></span>

<span data-ttu-id="fa647-103">依預設，會 <xref:System.Runtime.Serialization.DataContractSerializer> 以傳值方式序列化物件。</span><span class="sxs-lookup"><span data-stu-id="fa647-103">By default, <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="fa647-104">您可以使用 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> 屬性，指示資料合約序列化程式在序列化物件時保留物件參考。</span><span class="sxs-lookup"><span data-stu-id="fa647-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the data contract serializer to preserve object references when serializing objects.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="fa647-105">產生的 XML</span><span class="sxs-lookup"><span data-stu-id="fa647-105">Generated XML</span></span>  

 <span data-ttu-id="fa647-106">做為範例，請考量下列物件：</span><span class="sxs-lookup"><span data-stu-id="fa647-106">As an example, consider the following object:</span></span>  
  
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
  
 <span data-ttu-id="fa647-107">在 <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> 設為 `false` (預設值) 的情況下，會產生以下 XML：</span><span class="sxs-lookup"><span data-stu-id="fa647-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="fa647-108">在 <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> 設為 `true` 的情況下，會產生以下 XML：</span><span class="sxs-lookup"><span data-stu-id="fa647-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 <span data-ttu-id="fa647-109">但是， <xref:System.Runtime.Serialization.XsdDataContractExporter> `id` 即使屬性設定為，也不會 `ref` 在其架構中描述和屬性 `preserveObjectReferences` `true` 。</span><span class="sxs-lookup"><span data-stu-id="fa647-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> doesn't describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="fa647-110">使用 IsReference</span><span class="sxs-lookup"><span data-stu-id="fa647-110">Using IsReference</span></span>  

 <span data-ttu-id="fa647-111">若要根據描述的架構產生有效的物件參考資訊，請將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至類型，並將旗標設 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> 為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="fa647-111">To generate object reference information that's valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="fa647-112">下列範例會藉 `X` 由新增下列內容來修改上一個範例中的類別 `IsReference` ：</span><span class="sxs-lookup"><span data-stu-id="fa647-112">The following example modifies class `X` in the previous example by adding `IsReference`:</span></span>  
  
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

 <span data-ttu-id="fa647-113">產生的 XML 如下：</span><span class="sxs-lookup"><span data-stu-id="fa647-113">The generated XML is as follows:</span></span>  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A>
    <B ref="1"></B>  
</X>
```  
  
 <span data-ttu-id="fa647-114">使用 `IsReference` 確保往返的訊息相符。</span><span class="sxs-lookup"><span data-stu-id="fa647-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="fa647-115">如果沒有它，從架構產生型別時，該型別的 XML 輸出就不一定會與原本假設的架構相容。</span><span class="sxs-lookup"><span data-stu-id="fa647-115">Without it, when a type is generated from schema, the XML output for that type isn't necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="fa647-116">換句話說，即使 `id` 和 `ref` 屬性已序列化，原始結構描述仍可能禁止這些屬性 (或所有屬性) 出現在該 XML 中。</span><span class="sxs-lookup"><span data-stu-id="fa647-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="fa647-117">`IsReference`如果套用至資料成員，則在進行往返時，成員會繼續被視為 *可參考*。</span><span class="sxs-lookup"><span data-stu-id="fa647-117">With `IsReference` applied to a data member, the member continues to be recognized as *referenceable* when round-tripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa647-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa647-118">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
