---
title: '&lt;cryptoNameMapping&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ef916b0950e179f6782ce8d4d6fa380fd3804aa0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577162"
---
# <a name="ltcryptonamemappinggt-element"></a>&lt;cryptoNameMapping&gt;項目
包含易記名稱的類別對應。  
  
 \<configuration>  
\<mscorlib>  
\<cryptographySettings>  
\<cryptoNameMapping>  
  
## <a name="syntax"></a>語法  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|`cryptoClasses`|包含密碼編譯類別清單，其具有 **\<nameEntry>** 項目中易記名稱的對應。|  
|`nameEntry`|將類別名稱對應至易記的演算法名稱，允許一個類別有許多易記名稱。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`cryptographySettings`|包含密碼編譯設定。|  
|`cryptoNameMapping`|包含易記名稱的類別對應。|  
|`mscorlib`|包含\<cryptographySettings > 項目。|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 **\<cryptoNameMapping >** 項目參考加密編譯類別及設定執行階段。 然後，您可以將字串"RSA"傳遞至<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>方法和用法<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>方法來傳回`MyCryptoRSAClass`物件。  
  
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
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [密碼編譯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [The signature is valid](../../../../../docs/standard/security/cryptographic-services.md)
- [設定密碼編譯類別](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
