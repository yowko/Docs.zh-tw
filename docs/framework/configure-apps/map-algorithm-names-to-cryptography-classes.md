---
title: 將演算法名稱對應至密碼編譯類別
description: 將演算法名稱對應至 .NET 中的密碼編譯類別。 開發人員有四個選項可建立密碼編譯物件。
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: b67db612496e56a341dab2e5fc4b52c954ff02b4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183386"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>將演算法名稱對應至密碼編譯類別

有四種方式可供開發人員使用 Windows SDK 建立密碼編譯物件：  
  
- 使用 **new** 運算子建立物件。  
  
- 藉由在該演算法的抽象類別上呼叫 **Create** 方法，建立可執行特定密碼編譯演算法的物件。  
  
- 藉由呼叫方法，建立可執行特定密碼編譯演算法的物件 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 。  
  
- 建立物件，該物件會執行密碼編譯演算法的類別 (例如對稱封鎖密碼) ，方法是在該類型 (演算法的抽象類別上呼叫 **Create** 方法，例如 <xref:System.Security.Cryptography.SymmetricAlgorithm>) 。  
  
 例如，假設開發人員想要計算一組位元組的 SHA1 雜湊。 <xref:System.Security.Cryptography>命名空間包含兩個 SHA1 演算法的實作為，一個純粹受控的實作為一個包裝 CryptoAPI。 開發人員可以藉 <xref:System.Security.Cryptography.SHA1Managed> 由呼叫 **new** 運算子，選擇具現化特定的 SHA1 實 (，例如) 。 但是，如果 common language runtime 所載入的類別不重要，只要該類別會執行 SHA1 雜湊演算法，開發人員就可以藉由呼叫方法來建立物件 <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> 。 這個方法會呼叫 **cryptoconfig.createfromname. CreateFromName ( "system.string" ) **，它必須傳回 SHA1 雜湊演算法的實值。  
  
 開發人員也可以呼叫 **cryptoconfig.createfromname. CreateFromName ( "SHA1" ) ** 因為在預設的情況下，密碼編譯設定包含 .NET Framework 所隨附演算法的簡短名稱。  
  
 如果使用哪一個雜湊演算法並不重要，開發人員可以呼叫 <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> 方法，以傳回可執行雜湊轉換的物件。  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>在設定檔中對應演算法名稱  

 依預設，執行時間會傳回 <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> 所有四個案例的物件。 但是，電腦系統管理員可以變更最後兩個案例中的方法所傳回的物件類型。 若要這樣做，您必須將易記的演算法名稱對應至您要在電腦設定檔中使用的類別 ( # A0) 。  
  
 下列範例會示範如何設定執行時間，以便 **建立** **cryptoconfig.createfromname. CREATEFROMNAME ( "SHA1" ) **，以及 **HashAlgorithm..** 會傳回一個物件的方法，如下所示 `MySHA1HashClass` 。  
  
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
  
 您可以在 [<>cryptoclass \> 元素](./file-schema/cryptography/cryptoclass-element.md) 中指定屬性的名稱， (先前的範例將屬性命名為 `MySHA1Hash`) 。 專案中的屬性值 **\<cryptoClass>** 是通用語言執行時間用來尋找類別的字串。 您可以使用符合指定 [完整型別名稱](../reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的任何字串。  
  
 許多演算法名稱都可以對應到相同的類別。 [ \<nameEntry> 元素](./file-schema/cryptography/nameentry-element.md)會將類別對應至一個易記的演算法名稱。 **Name**屬性可以是在命名空間中呼叫**cryptoconfig.createfromname. CreateFromName**方法或抽象密碼編譯類別的名稱時，所使用的字串。 <xref:System.Security.Cryptography> **類別**屬性的值是元素中的屬性名稱 **\<cryptoClass>** 。  
  
> [!NOTE]
> 您可以藉由呼叫 <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> 或 **Cryptoconfig.createfromname. CreateFromName ( "sha1" ) ** 方法來取得 SHA1 演算法。 每個方法都可保證它會傳回可執行 SHA1 演算法的物件。 您不需要將演算法的每個易記名稱對應至設定檔中的相同類別。  
  
 如需預設名稱及其對應類別的清單，請參閱 <xref:System.Security.Cryptography.CryptoConfig> 。  
  
## <a name="see-also"></a>另請參閱

- [密碼編譯服務](../../standard/security/cryptographic-services.md)
- [設定密碼編譯類別](configure-cryptography-classes.md)
