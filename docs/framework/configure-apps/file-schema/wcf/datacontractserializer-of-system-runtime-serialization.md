---
title: "&lt;system.runtime.serialization&gt; 的 &lt;dataContractSerializer&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;system.runtime.serialization&gt; 的 &lt;dataContractSerializer&gt;
包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。  
  
## 語法  
  
```  
  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer ignoreExtensionDataObject="Boolean"  
            maxItemsInObjectGraph="Integer">  
      <declaredTypes>  
        <add type="String">  
          <knownType type="String">  
             <parameter index="Integer"  
                        type="String" />  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|項目|描述|  
|--------|--------|  
|ignoreExtensionDataObject|布林值，該值會指定當端點序列化或還原序列化時，是否略過端點所提供的資料。  此屬性只能在 `<behavior>` 項目下的 `<dataContractSerializer>` 設定。|  
|maxItemsInObjectGraph|整數，指定要序列化或還原序列化的項目數上限。  此屬性為 65536。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<declaredTypes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|包含還原序列化時，<xref:System.Runtime.Serialization.DataContractSerializer> 使用的已知型別。<br /><br /> 如需資料合約和已知型別的詳細資訊，請參閱[資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<system.runtime.serialization\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|代表 <xref:System.Runtime.Serialization> 命名空間區段的根項目，而且包含用來設定 <xref:System.Runtime.Serialization.DataContractSerializer> 選項的項目。|  
  
## 備註  
 如需已知型別的詳細資訊，請參閱<xref:System.Runtime.Serialization.DataContractSerializer>與 [資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。  
  
## 請參閱  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>   
 [資料合約已知型別](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)