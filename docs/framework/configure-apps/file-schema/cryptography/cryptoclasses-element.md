---
title: <cryptoClasses> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: 89f1d89ea397794e366b53205ac23b94d7892869
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699760"
---
# <a name="cryptoclasses-element"></a>\<cryptoClasses > 元素
包含密碼編譯類別清單，其具有 [\<nameEntry>](nameentry-element.md) 項目中易記名稱的對應。  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings >** ](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cryptoClasses >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 None。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<cryptoClass >](cryptoclass-element.md)|包含密碼編譯類別，其具有 **\<nameEntry>** 項目中易記名稱的對應。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`cryptographySettings`|包含密碼編譯設定。|  
|`cryptoNameMapping`|包含易記名稱的類別對應。|  
|`mscorlib`|包含 `cryptographySettings` 元素。|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用\<的**cryptoClass >** 元素來參考密碼編譯類別，以及設定執行時間。 接著，您可以將字串 "RSA" 傳遞給 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 方法，然後使用 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> 方法來傳回 `MyCryptoRSAClass` 物件。  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Security.Cryptography>
- [組態檔結構描述](../index.md)
- [密碼編譯設定結構描述](index.md)
- [密碼編譯服務](../../../../standard/security/cryptographic-services.md)
- [Cryptoconfig.createfromname. CreateFromName。](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)
- [設定密碼編譯類別](../../configure-cryptography-classes.md)
