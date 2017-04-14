---
title: "&lt;declaredTypes&gt; 項目的 &lt;add&gt; | Microsoft Docs"
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
  - "資料合約"
  - "DataContractAttribute"
  - "DataContractSerializer"
  - "dataContractSerializer 項目"
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# &lt;declaredTypes&gt; 項目的 &lt;add&gt;
在還原序列化期間，新增 <xref:System.Runtime.Serialization.DataContractSerializer> 所使用的型別。  每個宣告的型別都包含已知型別，這些已知型別將傳回做為宣告型別的欄位或屬性。  
  
## 語法  
  
```  
  
<add type="String">  
   <knownType type="String">  
       <parameter index="Integer"  
                  type="String" />  
   </knownType>  
</add>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|類型|必要的字串屬性。<br /><br /> 指定型別名稱 \(包括命名空間\)、組件名稱、版本號碼、文化特性和公開金鑰權杖。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<knownType\>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|為要加入的宣告型別指定已知型別。  如果宣告的型別是泛型型別，您也必須將參數項目加入至 `<knownType>` 項目，以指定要用於傳回已知型別的泛型參數。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<declaredTypes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|包含還原序列化期間 <xref:System.Runtime.Serialization.DataContractSerializer> 所需已知型別的型別。|  
  
## 備註  
 如需已知型別的詳細資訊，請參閱[資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)與 <xref:System.Runtime.Serialization.DataContractSerializer>。  
  
 如需使用這個項目的範例，請參閱 [\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)。  
  
> [!NOTE]
>  如果您將 <xref:System.Object> 型別加入做為 `<declaredType>`，則會擲回 <xref:System.Configuration.ConfigurationErrorsException>。  這是因為 <xref:System.Object> 型別無法用來做為組態中的宣告型別。  
  
## 範例  
  
```  
<add type="MyCompany.Library.Shape,   
           MyAssembly, Version=2.0.0.0, Culture=neutral,  
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">  
           <knownType type="MyCompany.Library.Circle,   
                      MyAssembly, Version=2.0.0.0, Culture=neutral,  
                      PublicKeyToken=XXXXXX,  
                      processorArchitecture=MSIL"/>  
</add>  
```  
  
## 請參閱  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 [資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)   
 [\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)   
 [\<add\> of \<declaredTypes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)