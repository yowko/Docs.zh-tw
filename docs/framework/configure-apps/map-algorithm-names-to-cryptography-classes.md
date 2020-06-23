---
title: 將演算法名稱對應至密碼編譯類別
description: 將演算法名稱對應至 .NET 中的密碼編譯類別。 開發人員有四個建立密碼編譯物件的選項。
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: 5a1d7acdd34182dd82f4dce66d136c4ef4de6e95
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105357"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>將演算法名稱對應至密碼編譯類別
有四種方式可供開發人員使用 Windows SDK 建立密碼編譯物件：  
  
- 使用**new**運算子建立物件。  
  
- 在該演算法的抽象類別上呼叫**create**方法，以建立可執行特定密碼編譯演算法的物件。  
  
- 藉由呼叫方法，建立可執行特定密碼編譯演算法的物件 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 。  
  
- 藉由在該演算法類型的抽象類別（例如）上呼叫**create**方法，來建立可實作為密碼編譯演算法類別（例如對稱式封鎖密碼）的物件 <xref:System.Security.Cryptography.SymmetricAlgorithm> 。  
  
 例如，假設開發人員想要計算一組位元組的 SHA1 雜湊。 <xref:System.Security.Cryptography>命名空間包含兩種 SHA1 演算法的實作為，一個純粹受控的執行，另一個則包裝 CryptoAPI。 開發人員可以藉 <xref:System.Security.Cryptography.SHA1Managed> 由呼叫**new**運算子，選擇具現化特定的 SHA1 實作為（例如）。 不過，如果通用語言執行平臺在類別實作為 SHA1 雜湊演算法時所載入的類別並不重要，則開發人員可以藉由呼叫方法來建立物件 <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> 。 這個方法會呼叫**cryptoconfig.createfromname. CreateFromName （"system.string"）**，它必須傳回 SHA1 雜湊演算法的實值。  
  
 開發人員也可以呼叫**cryptoconfig.createfromname. CreateFromName （"SHA1"）** ，因為根據預設，密碼編譯設定會包含 .NET Framework 隨附之演算法的簡短名稱。  
  
 如果使用的雜湊演算法並不重要，開發人員可以呼叫 <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> 方法，它會傳回可執行雜湊轉換的物件。  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>對應設定檔中的演算法名稱  
 根據預設，執行時間會 <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> 針對所有四個案例傳回物件。 不過，電腦系統管理員可以變更最後兩個案例中的方法所傳回的物件類型。 若要這樣做，您必須將易記的演算法名稱對應至您想要在電腦設定檔案中使用的類別（Machine.config）。  
  
 下列範例會示範如何設定運行**時間，讓** **cryptoconfig.createfromname CREATEFROMNAME （"SHA1"）** 和**HashAlgorithm. create**會傳回一個物件，以供您使用此方法。 *。 `MySHA1HashClass`  
  
```xml  
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
  
 您可以在<cryptoClass 專案中指定屬性的[ \> 名稱](./file-schema/cryptography/cryptoclass-element.md)（先前的範例會將屬性命名為 `MySHA1Hash` ）。 元素中的屬性值 **\<cryptoClass>** 是通用語言執行時間用來尋找類別的字串。 您可以使用符合指定[完整類型名稱](../reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的任何字串。  
  
 許多演算法名稱可以對應至相同的類別。 [ \<nameEntry> 元素](./file-schema/cryptography/nameentry-element.md)會將類別對應至一個易記的演算法名稱。 **Name**屬性可以是在命名空間中呼叫**cryptoconfig.createfromname. CreateFromName**方法或抽象密碼編譯類別名稱時所使用的字串 <xref:System.Security.Cryptography> 。 **類別**屬性的值是元素中的屬性名稱 **\<cryptoClass>** 。  
  
> [!NOTE]
> 您可以藉由呼叫 <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> 或**Cryptoconfig.createfromname. CreateFromName （"SHA1"）** 方法來取得 SHA1 演算法。 每個方法都只保證它會傳回可實作為 SHA1 演算法的物件。 您不需要將演算法的每一個易記名稱對應至設定檔中的相同類別。  
  
 如需預設名稱及其對應類別的清單，請參閱 <xref:System.Security.Cryptography.CryptoConfig> 。  
  
## <a name="see-also"></a>另請參閱

- [密碼編譯服務](../../standard/security/cryptographic-services.md)
- [設定密碼編譯類別](configure-cryptography-classes.md)
