---
title: <cryptoClass> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
ms.openlocfilehash: c8076fba1ebae693aa5e4c80e822b9ae840ff1c5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664329"
---
# <a name="cryptoclass-element"></a>\<cryptoClass > 元素
包含密碼編譯類別，其具有 [\<nameEntry>](nameentry-element.md) 項目中易記名稱的對應。  
  
 \<configuration>  
\<mscorlib>  
\<cryptographySettings>  
\<cryptoNameMapping>  
\<cryptoClasses >  
\<cryptoClass >  
  
## <a name="syntax"></a>語法  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`customClassName`|必要屬性。<br /><br /> 包含密碼編譯類別的資訊。 使用此屬性來提供類別的簡短名稱。 您必須指定符合指定[完整類型名稱](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)所指定之需求的字串。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`cryptoClasses`|包含密碼編譯類別清單，其具有 [\<nameEntry>](nameentry-element.md) 項目中易記名稱的對應。|  
|`cryptographySettings`|包含密碼編譯設定。|  
|`cryptoNameMapping`|包含易記名稱的類別對應。|  
|`mscorlib`|包含 [\<cryptographySettings>](cryptographysettings-element.md) 項目。|  
  
## <a name="example"></a>範例  
 下列範例顯示如何使用 **\<cryptoClass >** 專案來參考密碼編譯類別, 以及設定執行時間。 接著, 您可以將字串 "RSA" 傳遞給<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法, 並<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>使用方法來`MyCryptoRSAClass`傳回物件。  
  
```xml  
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
  
## <a name="see-also"></a>另請參閱

- [組態檔結構描述](../index.md)
- [密碼編譯設定結構描述](index.md)
- [The signature is valid](../../../../../docs/standard/security/cryptographic-services.md)
- [設定密碼編譯類別](../../configure-cryptography-classes.md)
