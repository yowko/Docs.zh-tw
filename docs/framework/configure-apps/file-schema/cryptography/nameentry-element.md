---
title: "&lt;nameEntry&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<nameEntry> 項目"
  - "nameEntry 項目"
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;nameEntry&gt; 項目
將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。  
  
## 語法  
  
```  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|**name**|必要屬性。<br /><br /> 指定密碼編譯類別實作的演算法易記名稱。|  
|**class**|必要屬性。<br /><br /> 指定 [\<cryptoClass\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) 項目中的**name**  屬性值。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.web`|指定 ASP.NET 組態區段的根項目。|  
  
## 備註  
 **name** 屬性可以是 <xref:System.Security.Cryptography> 命名空間中所找到的抽象類別的其中一個名稱。  當您在抽象密碼編譯類別上呼叫 **Create** 方法時，抽象類別名稱會傳遞給 [Security.CryptoConfig.CreateFromName](frlrfSystemSecurityCryptographyCryptoConfigClassCreateFromNameTopic) 方法。  **CreateFromName** 會傳回 **class** 屬性所指示的型別執行個體 \(Instance\)。  如果 **name** 屬性是簡短名稱，例如 RSA，則當呼叫 **CreateFromName** 方法時，您可以使用該名稱。  
  
## 範例  
 以下範例說明如何使用 **\<nameEntry\>** 項目參考密碼編譯類別及設定執行階段。  接著您可以將 "RSA" 字串傳遞給 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=fullName> 方法，並使用 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> 方法傳回 `MyCryptoRSAClass` 物件。  
  
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
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [密碼編譯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)   
 [密碼編譯服務](../../../../../docs/standard/security/cryptographic-services.md)   
 [設定密碼編譯類別](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)