---
title: "對應物件識別項至密碼編譯演算法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "密碼編譯演算法"
  - "密碼編譯, 對應物件識別項"
  - "數位簽章"
  - "識別項, 對應物件識別項"
  - "對應物件識別項"
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# 對應物件識別項至密碼編譯演算法
數位簽章確保資料從一個程式傳送至另一程式時不會被竄改。  基本上數位簽章是藉著套用數學函式於要被簽名的資料的雜湊來計算。  當格式化雜湊值要被簽名時，某些數位簽章演算法會附加 ASN.1 物件識別項 \(OID\) 做為格式化作業的一部分。  OID 辨識用來計算雜湊的演算法。  您可以對應演算法至物件識別項，以擴充要使用自訂演算法的密碼編譯機制。  下列範例示範如何對應物件識別項至新的雜湊演算法。  
  
```  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MyNewHash="MyNewHashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="NewHash" class="MyNewHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.14.33.42.46"  name="NewHash"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 [\<oidEntry\>項目](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)包含兩個屬性。  **OID** 屬性為物件識別項編號。  **name** 屬性為 [\<nameEntry\> 項目](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)的 **name** 屬性值。  在物件識別項可以對應至簡單名稱之前，必須要有從演算法名稱至類別的對應。  
  
## 請參閱  
 [設定密碼編譯類別](../../../docs/framework/configure-apps/configure-cryptography-classes.md)   
 [密碼編譯服務](../../../docs/standard/security/cryptographic-services.md)