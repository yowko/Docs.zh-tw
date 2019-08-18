---
title: 將演算法名稱對應至密碼編譯類別
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: 49f4b5b4b3634df5e648b5208448d644168e9d19
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566730"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>將演算法名稱對應至密碼編譯類別
有四種方式可供開發人員使用 Windows SDK 建立密碼編譯物件:  
  
- 使用**new**運算子建立物件。  
  
- 在該演算法的抽象類別上呼叫**create**方法, 以建立可執行特定密碼編譯演算法的物件。  
  
- 藉由呼叫<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法, 建立可執行特定密碼編譯演算法的物件。  
  
- 藉由在該演算法類型的抽象類別 (例如<xref:System.Security.Cryptography.SymmetricAlgorithm>) 上呼叫**create**方法, 來建立可實作為密碼編譯演算法類別 (例如對稱式封鎖密碼) 的物件。  
  
 例如, 假設開發人員想要計算一組位元組的 SHA1 雜湊。 <xref:System.Security.Cryptography>命名空間包含兩種 SHA1 演算法的實作為, 一個純粹受控的執行, 另一個則包裝 CryptoAPI。 開發人員可以藉由呼叫**new**運算子, 選擇具現化特定<xref:System.Security.Cryptography.SHA1Managed>的 SHA1 實作為 (例如)。 不過, 如果通用語言執行平臺在類別實作為 SHA1 雜湊演算法時所載入的類別並不重要, 則開發人員可以藉由呼叫<xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType>方法來建立物件。 這個方法會呼叫**cryptoconfig.createfromname. CreateFromName ("system.string")** , 它必須傳回 SHA1 雜湊演算法的實值。  
  
 開發人員也可以呼叫**cryptoconfig.createfromname. CreateFromName ("SHA1")** , 因為根據預設, 密碼編譯設定會包含 .NET Framework 隨附之演算法的簡短名稱。  
  
 如果使用的雜湊演算法並不重要, 開發人員可以呼叫<xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType>方法, 它會傳回可執行雜湊轉換的物件。  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>對應設定檔中的演算法名稱  
 根據預設, 運行<xref:System.Security.Cryptography.SHA1CryptoServiceProvider>時間會針對所有四個案例傳回物件。 不過, 電腦系統管理員可以變更最後兩個案例中的方法所傳回的物件類型。 若要這樣做, 您必須將易記的演算法名稱對應至您想要在電腦設定檔案 (Machine.config) 中使用的類別。  
  
 下列範例會示範如何設定執行時間, 使**Cryptoconfig.createfromname CreateFromName ("SHA1")** , 以及 **HashAlgorithm. 建立程式中的執行密碼編譯。 create。傳回物件。** `MySHA1HashClass`  
  
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
  
 您可以在[< cryptoClass\> ](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)專案中指定屬性的名稱 (先前的範例會將屬性`MySHA1Hash`命名為)。 CryptoClass > 元素中 **\<** 的屬性值是通用語言執行時間用來尋找類別的字串。 您可以使用符合指定[完整類型名稱](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的任何字串。  
  
 許多演算法名稱可以對應至相同的類別。 Y > 元素會將類別對應至一個易記的演算法名稱。 [ \< ](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) **Name**屬性可以是在<xref:System.Security.Cryptography>命名空間中呼叫**cryptoconfig.createfromname. CreateFromName**方法或抽象密碼編譯類別名稱時所使用的字串。 **類別**屬性的值是 **\<cryptoClass >** 元素中的屬性名稱。  
  
> [!NOTE]
>  您可以藉由呼叫<xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType>或**cryptoconfig.createfromname. CreateFromName ("SHA1")** 方法來取得 SHA1 演算法。 每個方法都只保證它會傳回可實作為 SHA1 演算法的物件。 您不需要將演算法的每一個易記名稱對應至設定檔中的相同類別。  
  
 如需預設名稱及其對應類別的清單, 請參閱<xref:System.Security.Cryptography.CryptoConfig>。  
  
## <a name="see-also"></a>另請參閱

- [The signature is valid](../../../docs/standard/security/cryptographic-services.md)
- [設定密碼編譯類別](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
