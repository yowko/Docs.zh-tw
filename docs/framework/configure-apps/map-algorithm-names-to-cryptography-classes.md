---
title: 將演算法名稱對應至密碼編譯類別
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
author: mcleblanc
ms.author: markl
ms.openlocfilehash: cd57cc7bbe39b042e11d0dad3fd54373bcaae98b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47076506"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>將演算法名稱對應至密碼編譯類別
有四種方式，開發人員可以建立密碼編譯物件，使用[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:  
  
-   使用建立的物件**新**運算子。  
  
-   建立藉由呼叫實作特定的密碼編譯演算法的物件**建立**該演算法的抽象類別上的方法。  
  
-   建立藉由呼叫實作特定的密碼編譯演算法的物件<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法。  
  
-   建立物件，實作密碼編譯演算法 （例如對稱區塊編碼器） 藉由呼叫**Create**方法的抽象類別上該類型的演算法 (例如<xref:System.Security.Cryptography.SymmetricAlgorithm>)。  
  
 例如，假設開發人員想要計算一組位元組的 SHA1 雜湊。 <xref:System.Security.Cryptography>命名空間包含兩個 SHA1 演算法，其中一個純粹是 managed 的實作，另一個包裝 CryptoAPI 實作。 開發人員可以選擇要具現化特定的 SHA1 實作 (例如<xref:System.Security.Cryptography.SHA1Managed>) 藉由呼叫**新**運算子。 不過，如果它並不重要，只要此類別會實作的 SHA1 雜湊演算法，common language runtime 載入哪一個類別，開發人員可以建立物件藉由呼叫<xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType>方法。 這個方法會呼叫**System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**，它必須傳回 SHA1 雜湊演算法的實作。  
  
 開發人員也可以呼叫**System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** 因為根據預設，加密組態包含隨附於.NET Framework 中的演算法簡短名稱。  
  
 如果不論使用哪一個雜湊演算法，開發人員可以呼叫<xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType>方法，以傳回該物件會實作雜湊的轉換。  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>將組態檔中的演算法名稱對應  
 根據預設，執行階段會傳回<xref:System.Security.Cryptography.SHA1CryptoServiceProvider>這四個案例的物件。 不過，電腦的系統管理員可以變更最後兩個案例中的方法所傳回的物件的類型。 若要這樣做，您必須將易記的演算法名稱對應至您想要在電腦組態檔 (Machine.config) 中使用的類別。  
  
 下列範例示範如何設定執行階段，讓**System.Security.Cryptography.SHA1.Create**， **System.Security.CryptoConfig.CreateFromName("SHA1")**，和**System.Security.Cryptography.HashAlgorithm.Create**傳回`MySHA1HashClass`物件。  
  
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
  
 您可以指定中的屬性名稱[< cryptoClass\>項目](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)(上述範例將此屬性命名`MySHA1Hash`)。 中的屬性值 **\<cryptoClass >** 項目是 common language runtime 用來尋找類別的字串。 您可以使用任何符合需求中所指定的字串[指定完整的型別名稱](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。  
  
 許多的演算法名稱可以對應至相同的類別。 [ \<NameEntry > 項目](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)類別對應至一個易記的演算法名稱。 **名稱**屬性可以是字串時，呼叫使用**System.Security.Cryptography.CryptoConfig.CreateFromName**方法或在抽象的密碼編譯類別的名稱<xref:System.Security.Cryptography>命名空間。 值**類別**屬性是中的屬性名稱 **\<cryptoClass >** 項目。  
  
> [!NOTE]
>  您可以呼叫來取得 SHA1 演算法<xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType>或**Security.CryptoConfig.CreateFromName("SHA1")** 方法。 每一種方法僅保證，它會傳回實作 SHA1 演算法的物件。 您沒有對應至相同的類別，在組態檔中的每個演算法的好記的名稱。  
  
 如需預設名稱和它們對應到類別的清單，請參閱<xref:System.Security.Cryptography.CryptoConfig>。  
  
## <a name="see-also"></a>另請參閱  
 [The signature is valid](../../../docs/standard/security/cryptographic-services.md)  
 [設定密碼編譯類別](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
