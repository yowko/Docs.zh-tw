---
title: "互通物件參考"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3d74c54d29f7da085d9d87bf37cc93078726f308
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="interoperable-object-references"></a>互通物件參考
根據預設，<xref:System.Runtime.Serialization.DataContractSerializer> 會以傳值方式序列化物件。 您可以使用 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> 屬性，指示資料合約序列化程式在序列化此類型物件時保留物件參考。  
  
## <a name="generated-xml"></a>產生的 XML  
 做為範例，請考量下列物件：  
  
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
   <B ref="1" />  
</X>  
```  
  
 不過，即使 <xref:System.Runtime.Serialization.XsdDataContractExporter> 屬性 (Property) 設為 `id`，`ref` 仍不會在其結構描述中描述 `preserveObjectReferences` 和 `true` 屬性 (Attribute)。  
  
## <a name="using-isreference"></a>使用 IsReference  
 若要根據描述物件參考資訊的結構描述產生有效的物件參考資訊，請將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至某一個類型，並且將 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> 旗標設為 `true`。 在上一個範例的類別 `IsReference` 中使用 `X`：  
  
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
  
 產生的 XML 如下：  
  
 `<X>`  
  
 `<A id="1">`  
  
 `<Value>contents of A</Value>`  
  
 `</A>`  
  
 `<B ref="1">`  
  
 `</B>`  
  
 `</X>`  
  
 使用 `IsReference` 確保往返的訊息相符。 否則，當某類型自結構描述產生時，針對該類型傳回的 XML，不一定與結構描述原本預期的類型相容。 換句話說，即使 `id` 和 `ref` 屬性已序列化，原始結構描述仍可能禁止這些屬性 (或所有屬性) 出現在該 XML 中。 在 `IsReference` 已套用至資料成員的情況下，該成員就會在往返時繼續被視為「可參考」。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference%2A>
