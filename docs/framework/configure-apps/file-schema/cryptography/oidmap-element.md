---
title: "&lt;oidMap&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<oidMap> 項目"
  - "oidMap 項目"
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;oidMap&gt; 項目
包含類別的 ASN.1 物件識別項 \(OID\) 對應。  
  
## 語法  
  
```  
<oidMap>   
</oidMap>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|元素|說明|  
|--------|--------|  
|[\<oidEntry\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|將 ASN.1 OID 對應至易記名稱。|  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`cryptographySettings`|包含密碼編譯設定。|  
|`mscorlib`|包含 `cryptographySettings`  項目。|  
  
## 範例  
 下列範例顯示如何使用 **\<oidMap\>** 項目來將 RIPEMD\-160 雜湊演算法的 OID 對應包含至該雜湊演算法的實作。  
  
```  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"  name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## 請參閱  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [密碼編譯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)   
 [密碼編譯服務](../../../../../docs/standard/security/cryptographic-services.md)   
 [設定密碼編譯類別](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)   
 [對應物件識別項至密碼編譯演算法](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)