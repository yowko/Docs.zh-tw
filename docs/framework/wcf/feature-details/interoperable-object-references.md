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
# <a name="interoperable-object-references"></a>互通的物件參考

依預設，會 <xref:System.Runtime.Serialization.DataContractSerializer> 以傳值方式序列化物件。 您可以使用 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> 屬性，指示資料合約序列化程式在序列化物件時保留物件參考。  
  
## <a name="generated-xml"></a>產生的 XML  

 做為範例，請考量下列物件：  
  
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
  
 在 <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> 設為 `false` (預設值) 的情況下，會產生以下 XML：  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 在 <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> 設為 `true` 的情況下，會產生以下 XML：  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 但是， <xref:System.Runtime.Serialization.XsdDataContractExporter> `id` 即使屬性設定為，也不會 `ref` 在其架構中描述和屬性 `preserveObjectReferences` `true` 。  
  
## <a name="using-isreference"></a>使用 IsReference  

 若要根據描述的架構產生有效的物件參考資訊，請將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至類型，並將旗標設 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> 為 `true` 。 下列範例會藉 `X` 由新增下列內容來修改上一個範例中的類別 `IsReference` ：  
  
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

 產生的 XML 如下：  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A>
    <B ref="1"></B>  
</X>
```  
  
 使用 `IsReference` 確保往返的訊息相符。 如果沒有它，從架構產生型別時，該型別的 XML 輸出就不一定會與原本假設的架構相容。 換句話說，即使 `id` 和 `ref` 屬性已序列化，原始結構描述仍可能禁止這些屬性 (或所有屬性) 出現在該 XML 中。 `IsReference`如果套用至資料成員，則在進行往返時，成員會繼續被視為 *可參考*。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
