---
title: "將演算法名稱對應至密碼編譯類別 | Microsoft Docs"
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
  - "密碼編譯, 對應演算法名稱"
  - "對應演算法名稱"
  - "名稱 [.NET Framework], 演算法對應"
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# 將演算法名稱對應至密碼編譯類別
開發人員有四種使用 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 建立密碼編譯物件的方式：  
  
-   使用 **new** 運算子建立物件。  
  
-   呼叫特定密碼編譯演算法抽象類別 \(Abstract Class\) 上的 **Create** 方法，來建立實作該演算法的物件。  
  
-   呼叫 [System.Security.Cryptography.CryptoConfig.CreateFromName](frlrfSystemSecurityCryptographyCryptoConfigClassCreateFromNameTopic) 方法，建立實作特定密碼編譯演算法的物件。  
  
-   呼叫密碼編譯演算法 \(例如 <xref:System.Security.Cryptography.SymmetricAlgorithm>\) 抽象類別上的 **Create** 方法，建立實作該類型演算法 \(例如 Symmetric Block Cipher\) 類別的物件。  
  
 例如，假設開發人員想要計算一組位元組的 SHA1 雜湊。  <xref:System.Security.Cryptography> 命名空間包含 SHA1 演算法的兩個實作，一個為純粹的 Managed 實作，而一個則包裝 CryptoAPI。  開發人員可以呼叫 **new** 運算子，選擇要具現化特定 SHA1 實作 \(例如 [SHA1Managed 類別](frlrfSystemSecurityCryptographySHA1ManagedClassTopic)\)。  然而，如果只要類別實作 SHA1 雜湊演算法，Common Language Runtime 將載入哪個類別即無關緊要的話，開發人員可以呼叫 [System.Security.Cryptography.SHA1.Create](frlrfSystemSecurityCryptographySHA1ClassCreateTopic) 方法建立物件。  這個方法會呼叫必須傳回 SHA1 雜湊演算法實作的 **System.Security.Cryptography.CryptoConfig.CreateFromName\("System.Security.Cryptography.SHA1"\)**。  
  
 開發人員也可以呼叫 **System.Security.Cryptography.CryptoConfig.CreateFromName\("SHA1"\)**，因為在預設情況中，加密組態包含 .NET Framework 中隨附的演算法的簡短名稱。  
  
 如果使用哪個雜湊演算法無關緊要的話，開發人員就可以呼叫 [System.Security.Cryptography.HashAlgorithm.Create](frlrfSystemSecurityCryptographyHashAlgorithmClassCreateTopic) 方法，傳回實作雜湊轉換的物件。  
  
## 在組態檔中對應演算法名稱  
 預設的情況下，執行階段對所有四個案例都會傳回 [System.Security.Cryptography.SHA1CryptoServiceProvider 類別](frlrfSystemSecurityCryptographySHA1CryptoServiceProviderClassTopic)物件。  然而，電腦系統管員可以變更最後兩個案例中的方法所傳回物件的型別。  若要這麼做，您必須對應易記的演算法名稱至您想要在電腦組態檔 \(Machine.config\) 中使用的類別。  
  
 下列範例將示範如何設定執行階段，使得 **System.Security.Cryptography.SHA1.Create**、**System.Security.CryptoConfig.CreateFromName\("SHA1"\)** 和 **System.Security.Cryptography.HashAlgorithm.Create** 會傳回 `MySHA1HashClass` 物件。  
  
```  
<configuration>  
   <!-- Other configuration settings. -->  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MySHA1Hash="MySHA1HashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="SHA1" class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.SHA1"  
                       class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MySHA1Hash"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 您可以在 [\<cryptoClass\> 項目](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)中指定屬性名稱 \(之前的範例將此屬性命名為`MySHA1Hash` \)。  **\<cryptoClass\>**項目中屬性的值為 Common Language Runtime 用來尋找類別的字串。  您可以使用符合[指定完整的型別名稱](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)中指定的要求的任一字串。  
  
 許多演算法名稱可以對應至相同類別。  [\<nameEntry\>項目](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)對應類別至一個易記的演算法名稱。  **name** 屬性可以是呼叫 **System.Security.Cryptography.CryptoConfig.CreateFromName** 方法時使用的字串，或者是 <xref:System.Security.Cryptography> 命名空間中的抽象密碼編譯類別名稱。  **class** 屬性的值是 **\<cryptoClass\>** 項目中屬性的名稱。  
  
> [!NOTE]
>  您可以藉由呼叫 [System.Security.Cryptography.SHA1.Create](frlrfSystemSecurityCryptographySHA1ClassCreateTopic) 或 **Security.CryptoConfig.CreateFromName\("SHA1"\)** 方法來取得 SHA1 演算法。  各個方法只保證它會傳回實作 SHA1 演算法的物件。  您不必對應演算法的每一個易記名稱至組態檔中的相同類別。  
  
 如需預設名稱和它們對應到的類別的清單，請參閱 [CryptoConfig 類別](frlrfSystemSecurityCryptographyCryptoConfigClassTopic)。  
  
## 請參閱  
 [密碼編譯服務](../../../docs/standard/security/cryptographic-services.md)   
 [設定密碼編譯類別](../../../docs/framework/configure-apps/configure-cryptography-classes.md)