---
title: "&lt;userDefinedType&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;userDefinedType&gt;
表示要包含在服務合約中的使用者定義型別 \(User Defined Type，UDT\)。  
  
## 語法  
  
```  
  
<comContracts>  
  <comContract>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
         </userDefinedType>  
      </userDefinedTypes>  
  </comContract>  
</comContracts>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`name`|選擇性屬性，其中包含提供可讀型別名稱的字串。  雖然這不是供執行階段使用，但是可幫助讀者分辨型別。|  
|`TypeDefID`|GUID 字串，識別已註冊型別程式庫內的特定 UDT 型別。|  
|`TypeLibID`|GUID 字串，識別定義此型別的已註冊型別程式庫。|  
|`TypeLibVersion`|字串，識別定義此型別的型別程式庫版本。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`userDefinedTypes`|`userDefinedType` 項目的集合。|  
  
## 備註  
 COM\+ 整合執行階段會藉由檢查型別程式庫來建立服務。  當 COM\+ 元件包含傳遞 VARIANT 的方法時，系統便無法在執行階段之前判斷要傳遞的實際型別。  因此，嘗試在 VARIANT 內傳遞使用者定義型別 \(UDT\) 會因為該型別不是序列化的已知型別而失敗。  
  
 如果要避免這個問題，您可以將這些 UDT 新增至組態檔中，以便包含它們做為適當服務合約中的已知型別。  如果要這樣做，您必須唯一識別這些 UDT 和合約，也就是使用其原始的 COM 介面。  
  
 下列範例將示範如何將兩個特定的 UDT 新增至組態檔的 \<`userDefinedTypes`\> 區段，以達成這個目的。  
  
```  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
      <userDefinedTypes>  
         <userDefinedType name="CustomerType"  
            typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"  
            typeLibVersion="1.0"  
            typeDefID="{D129765C-F211-434e-825A-9A63198C41F2}">  
         </userDefinedType>  
         <userDefinedType name="AddressType"  
            typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"  
            typeLibVersion="1.0"  
            typeDefID="{4616AE0D-687A-43B7-BC63-141AE3DFD099}">  
         </userDefinedType>  
      </userDefinedTypes>  
      <exposedMethods>  
         <exposedMethod name="BuyStock" />  
         <exposedMethod name="SellStock" />  
         <exposedMethod name="ExecuteTransaction" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
 當初始化服務時，整合執行階段會查詢指定的型別，並將它們加入做為指定合約的已知型別集合。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>   
 <xref:System.ServiceModel.Configuration.ComUdtElementCollection>   
 <xref:System.ServiceModel.Configuration.ComUdtElement>   
 [\<comContracts\>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)   
 [整合 COM\+ 應用程式](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)   
 [HOW TO：設定 COM\+ 服務設定](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)