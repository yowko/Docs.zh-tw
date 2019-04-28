---
title: 互通物件參考
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: ada9084f6ac3c97dc641571c0cb8379a2fac68a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918966"
---
# <a name="interoperable-object-references"></a>互通物件參考
根據預設，<xref:System.Runtime.Serialization.DataContractSerializer>將物件序列化的值。 您可以使用<xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>屬性，指示資料合約序列化程式，將物件序列化時保留物件參考。  
  
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
  
 不過，<xref:System.Runtime.Serialization.XsdDataContractExporter>並未說明`id`並`ref`它的結構描述中的屬性，即使`preserveObjectReferences`屬性設定為`true`。  
  
## <a name="using-isreference"></a>使用 IsReference  
 若要產生有效根據結構描述的物件參考資訊，請套用<xref:System.Runtime.Serialization.DataContractAttribute>屬性設為型別，並設定<xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>旗標設為`true`。 下列範例會修改類別`X`加上一個範例中`IsReference`:  
  
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
  
 使用 `IsReference` 確保往返的訊息相符。 未安裝，當從結構描述產生類型的 XML 輸出的型別不一定與原本預期的結構描述相容。 換句話說，即使 `id` 和 `ref` 屬性已序列化，原始結構描述仍可能禁止這些屬性 (或所有屬性) 出現在該 XML 中。 具有`IsReference`套用至資料成員，該成員就會被視為*referenceable*時往返。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
