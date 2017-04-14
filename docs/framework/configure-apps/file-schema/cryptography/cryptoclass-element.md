---
title: "&lt;cryptoClass&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<cryptoClass> 項目"
  - "cryptoClass 項目"
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;cryptoClass&gt; 項目
包含加密類別，其在 [\<nameEntry\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) 項目中具有易記名稱的對應。  
  
## 語法  
  
```  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`customClassName`|必要屬性。<br /><br /> 包含密碼編譯類別的資訊。  使用這個屬性，提供您類別的簡短名稱。  您必須指定符合在[指定完整型別名稱](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)中所指定的需求。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`cryptoClasses`|包含加密類別清單，其在 [\<nameEntry\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) 項目中具有易記名稱的對應。|  
|`cryptographySettings`|包含密碼編譯設定。|  
|`cryptoNameMapping`|包含易記名稱的類別對應。|  
|`mscorlib`|包含 [\<cryptographySettings\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md) 項目。|  
  
## 範例  
 以下範例說明如何使用 **\<cryptoClass\>** 項目參考加密類別及設定執行階段。  接著您可以將 "RSA" 字串傳遞給 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=fullName> 方法，並使用 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> 方法傳回 `MyCryptoRSAClass` 物件。  
  
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