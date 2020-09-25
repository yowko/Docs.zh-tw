---
title: 密碼編譯設定的 <mscorlib> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
ms.openlocfilehash: 1788205997d0dc49df172c9dfe48faceb8fc3290
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201781"
---
# <a name="mscorlib-element-for-cryptography-settings"></a>密碼編譯設定的 \<mscorlib> 項目

包含[ \<cryptographySettings> 元素](cryptographysettings-element.md)。  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<mscorlib>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
      <mscorlib>
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
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

 下列範例示範如何使用專案 **\<mscorlib>** 來參考加密類別，以及如何設定執行時間。 然後，您可以將字串 "RSA" 傳遞給 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 方法，並使用 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> 方法來傳回 `MyCryptoRSAClass` 物件。  
  
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
- [設定檔架構](../index.md)
- [密碼編譯設定架構](index.md)
- [密碼編譯服務](../../../../standard/security/cryptographic-services.md)
- [設定密碼編譯類別](../../configure-cryptography-classes.md)
