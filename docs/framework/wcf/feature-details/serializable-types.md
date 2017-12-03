---
title: "可序列化的型別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e368472db3bdca73661586821106174e13d4d24
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="serializable-types"></a>可序列化的型別
根據預設，<xref:System.Runtime.Serialization.DataContractSerializer> 會序列化所有公開可見的型別。 型別的所有公用讀取/寫入屬性 (Property) 和欄位都會序列化。  
  
 您可以透過將 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性套用至型別和成員的方式來變更預設行為。當您擁有的型別並非您所能控制，而且無法經過修改以加入屬性時，這個功能便相當實用。 <xref:System.Runtime.Serialization.DataContractSerializer> 會識別這類「未標記」的型別。  
  
## <a name="serialization-defaults"></a>序列化預設值  
 您可以套用 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性，以便明確控制或自訂型別和成員的序列化作業。 此外，您可以將這些屬性套用至私用欄位。 不過，即使未以這些屬性標記的型別，仍可以進行序列化和還原序列化。 以下為適用的規則和例外狀況：  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> 會使用新建立型別的預設屬性 (Property)，從未包含屬性 (Attribute) 的型別推斷資料合約。  
  
-   除非您將 `get` 屬性 (Attribute) 套用至該成員，否則所有公用欄位，以及含有公用 `set` 和 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> 方法的屬性 (Property) 都會加以序列化。  
  
-   序列化語意 (Semantics) 與 <xref:System.Xml.Serialization.XmlSerializer> 的語意相似。  
  
-   在未標記的型別中，只有具有未包含參數之建構函式 (Constructor) 的公用型別才會序列化。 這個規則的例外情形是搭配 <xref:System.Runtime.Serialization.ExtensionDataObject> 介面使用的 <xref:System.Runtime.Serialization.IExtensibleDataObject>。  
  
-   唯讀欄位、沒有 `get` 或 `set` 方法的屬性，以及具有內部或私用 `set` 或 `get` 方法的屬性不會序列化。 這類屬性會被略過，而且不會擲回例外狀況，但不包括 get-only 集合。  
  
-   <xref:System.Xml.Serialization.XmlSerializer> 屬性 (例如 `XmlElement`、`XmlAttribute`、`XmlIgnore`、`XmlInclude` 等屬性) 會被略過。  
  
-   如果您未將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至指定的型別，則序列化程式會忽略該型別中任何已套用 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性的成員。  
  
-   未標記 <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> 屬性 (Attribute) 的型別支援 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性 (Property)。 這包括支援未標記型別上的 <xref:System.Runtime.Serialization.KnownTypeAttribute> 屬性。  
  
-   若要「選擇不」序列化公用成員、屬性 (Property) 或欄位的處理序，請將 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> 屬性 (Attribute) 套用至該成員。  
  
## <a name="inheritance"></a>繼承  
 未標記的型別 (沒有 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性的型別) 可以繼承自沒有這個屬性的型別，不過不允許反向操作，也就是說，擁有這個屬性的型別無法繼承自未標記的型別。 強制執行這個規則的主要原因，是為了確保與使用舊版 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 撰寫的程式碼回溯相容。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [資料合約序列化程式所支援的類型](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
