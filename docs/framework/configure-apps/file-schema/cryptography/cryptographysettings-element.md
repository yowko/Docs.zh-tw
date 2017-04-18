---
title: "&lt;cryptographySettings&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<cryptographySettings> 項目"
  - "cryptographySettings 項目"
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# &lt;cryptographySettings&gt; 項目
包含密碼編譯設定。  
  
## 語法  
  
```  
  
      <cryptographySettings>   
</crytopgraphySettings>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|元素|說明|  
|--------|--------|  
|[\<cryptoNameMapping\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|包含易記名稱的類別對應。|  
|[\<oidMap\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|包含類別的 ASN.1 物件識別項 \(OID\) 對應。|  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`mscorlib`|包含 `cryptographySettings` 項目。|  
  
## 範例  
 下列範例顯示如何使用 **\<cryptographySettings\>** 項目來包含密碼編譯名稱對應和 OID 對應。  這個範例設定執行階段，讓 [System.Security.Cryptography.HashAlgorithm.Create](frlrfSystemSecurityCryptographyHashAlgorithmClassCreateTopic) 傳回 `MyHashClass` 物件，並讓 `MyCryptoClass` 類別對應物件識別項 1.3.36.2.1。  
  
```  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## 請參閱  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [密碼編譯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)   
 [密碼編譯服務](../../../../../docs/standard/security/cryptographic-services.md)