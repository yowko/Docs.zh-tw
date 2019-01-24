---
title: '&lt;mscorlib&gt;密碼編譯設定的項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 0615a68add60b02a875921b1abb3776267db1731
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527584"
---
# <a name="ltmscorlibgt-element-for-cryptography-settings"></a>&lt;mscorlib&gt;密碼編譯設定的項目
包含[ \<cryptographySettings > 項目](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)。  
  
 \<configuration>  
\<mscorlib>  
  
## <a name="syntax"></a>語法  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|`cryptographySettings`|包含密碼編譯設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 **\<mscorlib >** 項目參考加密編譯類別及設定執行階段。 然後，您可以將字串"RSA"傳遞至<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法和用法<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>方法來傳回`MyCryptoRSAClass`物件。  
  
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
- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [密碼編譯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [The signature is valid](../../../../../docs/standard/security/cryptographic-services.md)
- [設定密碼編譯類別](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
