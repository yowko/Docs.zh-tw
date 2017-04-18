---
title: "資料成員預設值 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "資料成員 [WCF]"
  - "資料成員 [WCF], 預設值"
ms.assetid: 53a3b505-4b27-444b-b079-0eb84a97cfd8
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# 資料成員預設值
在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中，型別具有*預設值*的概念。例如，任何參考型別的預設值為 `null`，整數型別則為零。有時候資料成員設為預設值時，會需要從序列化資料中省略該成員。因為此成員為預設值，而實際值不需要序列化，因此這樣做可促進效能。  
  
 若要省略序列化資料中的成員，請將 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 \(Attribute\) 的 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> 屬性 \(Property\) 設為 `false` \(預設值為 `true`\)。  
  
> [!NOTE]
>  您應該只在有特殊需要時才會將 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> 屬性設定為 `false`，例如為了互通性或縮減資料大小。  
  
## 範例  
 以下程式碼中有數個成員的 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> 都設為 `false`。  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 如果這個類別的執行個體已序列化，則結果可能如下：`employeeName` 和 `employeeID` 將會序列化。`employeeName` 的 null 值和 `employeeID` 的零值將明確成為序列化資料的一部分。不過，`position`、`salary` 和 `bonus` 成員都不會序列化。最後，即使 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> 屬性設為 `false`，`targetSalary` 通常仍會序列化，因為 57800 不符合 .NET 預設的整數值，也就是零。  
  
### XML 表示  
 如果之前的範例已序列化為 XML，則表示方式將類似以下內容：  
  
```  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 `xsi:nil` 屬性 \(Attribute\) 是全球資訊網協會 \(W3C\) XML 結構描述執行個體命名空間中的特殊屬性，會提供可互通的方式明確表示 null 值。請注意，XML 中沒有任何關於職位、薪資及獎金資料成員的資訊。接收端可以分別將這些成員解譯為 `null`、零和 `null`。不過不保證協力廠商的還原序列化程式能夠正確解譯，這也是不建議使用此模式的原因。<xref:System.Runtime.Serialization.DataContractSerializer> 類別永遠會為遺漏的值選取正確解譯。  
  
### 與 IsRequired 互動  
 如同在[資料合約版本控制](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)中所討論，<xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 \(Attribute\) 具有 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 屬性 \(Property\) \(預設值為 `false`\)。這個屬性會表示還原序列化指定的資料成員時，是否必須以序列化的資料表示該成員。如果 `IsRequired` 設為 `true` \(表示一定要使用一個值\)，且 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> 設為 `false` \(表示如果使用預設值，則不需要使用該值\)，因為結果會互相矛盾，所以無法序列化此資料成員的預設值。如果這類資料成員設為其預設值 \(通常為 `null` 或零\)，並且嘗試進行序列化，則會擲回 <xref:System.Runtime.Serialization.SerializationException>。  
  
### 結構描述表示  
 `EmitDefaultValue` 屬性設為 `false` 時，資料成員的 XML 結構描述定義語言 \(XSD\) 結構描述表示的詳細資訊將在[資料合約結構描述參考](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)中討論。不過，以下提供簡要的概觀。  
  
-   當 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> 設為 `false` 時，會以如同 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 專屬附註的結構描述表示。目前沒有可互通的方式能表示這項資訊。特別是結構描述中的 "default" 屬性 \(Attribute\) 不是用於此目的時，`minOccurs` 屬性只會受到 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 設定的影響，而 `nillable` 屬性只會受到資料成員的型別影響。  
  
-   實際使用的預設值不會在結構描述中表示。端看接收端點如何適當地解譯遺失的項目而定。  
  
 在結構描述匯入時，無論偵測到之前提到之 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 專屬附註的時機為何，<xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> 屬性都會自動設為 `false`。針對 `nillable` 屬性設為 `false` 的參考型別，此屬性也會設為 `false`，以支援常在使用 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 服務時發生的特定互通性案例。  
  
## 請參閱  
 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>   
 <xref:System.Runtime.Serialization.DataMemberAttribute>