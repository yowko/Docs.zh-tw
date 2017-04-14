---
title: "&lt;oidEntry&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<oidEntry> 項目"
  - "oidEntry 項目"
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;oidEntry&gt; 項目
將 ASN.1 物件識別項對應至易記名稱。  
  
## 語法  
  
```  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|**OID**|必要屬性。<br /><br /> 指定 ASN.1 OID，對應至您類別所實作的演算法。|  
|**name**|必要屬性。<br /><br /> 指定 [\<nameEntry\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) 標記中的 **name**  屬性值。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`cryptographySettings`|包含密碼編譯設定。|  
|`mscorlib`|包含 `cryptographySettings` 項目。|  
|`oidMap`|包含類別的 ASN.1 物件識別項 \(OID\) 對應。|  
  
## 備註  
 ASN.1 物件識別項會以某些密碼編譯格式識別演算法。  將物件識別項對應至您要識別的演算法之易記名稱。  如需物件識別項的詳細資訊，請參閱 MSDN Library。  
  
## 範例  
 下列範例顯示如何使用 **\<oidEntry\>** 項目，來將 RIPEMD\-160 雜湊演算法的物件識別項，對應至該雜湊演算法的實作 \(Implementation\)。  
  
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
 [設定密碼編譯類別](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)   
 [對應物件識別項至密碼編譯演算法](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)