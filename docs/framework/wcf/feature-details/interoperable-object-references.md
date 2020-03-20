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
# <a name="interoperable-object-references"></a>可交互操作的物件引用
預設情況下，<xref:System.Runtime.Serialization.DataContractSerializer>按值序列化物件。 可以使用 屬性<xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>指示資料協定序列化器在序列化物件時保留物件引用。  
  
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
  
 但是，<xref:System.Runtime.Serialization.XsdDataContractExporter>即使`preserveObjectReferences`屬性設置為`true`，`id`也不會在其架構中描述 和`ref`屬性。  
  
## <a name="using-isreference"></a>使用 IsReference  
 要根據描述該資訊的架構生成有效的物件引用資訊，請將<xref:System.Runtime.Serialization.DataContractAttribute>屬性應用於類型，並將<xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>標誌設置為`true`。 以下示例通過添加`X``IsReference`：  
  
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
  
 使用 `IsReference` 確保往返的訊息相符。 如果沒有它，當從架構組建類型時，該類型的 XML 輸出不一定與最初假定的架構相容。 換句話說，即使 `id` 和 `ref` 屬性已序列化，原始結構描述仍可能禁止這些屬性 (或所有屬性) 出現在該 XML 中。 應用於`IsReference`資料成員後，該成員在四捨五入時繼續被識別為*可引用*成員。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
