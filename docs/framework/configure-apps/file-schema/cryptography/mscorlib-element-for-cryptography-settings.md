---
title: "密碼編譯設定的 &lt;mscorlib&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<mscorlib> 項目"
  - "mscorlib 項目"
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# 密碼編譯設定的 &lt;mscorlib&gt; 項目
包含 [\<cryptographySettings\> 項目](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)。  
  
## 語法  
  
```  
  
      <mscorlib>   
</mscorlib>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|元素|說明|  
|--------|--------|  
|`cryptographySettings`|包含密碼編譯設定。|  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## 範例  
 以下範例說明如何使用 **\<mscorlib\>** 項目，參考密碼編譯類別及設定執行階段。  接著您可以將 "RSA" 字串傳遞給 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=fullName> 方法，並使用 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> 方法傳回 `MyCryptoRSAClass` 物件。  
  
```  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>   
 <xref:System.Security.Cryptography>   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [密碼編譯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)   
 [密碼編譯服務](../../../../../docs/standard/security/cryptographic-services.md)   
 [設定密碼編譯類別](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)