---
title: <cryptographySettings> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: fe6de09213c6f980e8eb205a318aae50033b2a84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155228"
---
# <a name="cryptographysettings-element"></a>\<密碼設置>元素
包含密碼編譯設定。  

[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<姆斯科利布>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<密碼設置>**

## <a name="syntax"></a>語法  
  
```xml  
      <cryptographySettings>
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<加密名稱映射>](cryptonamemapping-element.md)|包含易記名稱的類別對應。|  
|[\<oidMap>](oidmap-element.md)|包含 ASN.1 物件識別碼 （OID） 映射到類。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`mscorlib`|包含元素`cryptographySettings`。|  
  
## <a name="example"></a>範例  
 下面的示例演示如何使用**\<加密設定>** 元素來包含加密名稱映射和 OID 映射。 此示例配置運行時，<xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType>以便返回`MyHashClass`物件，`MyCryptoClass`並且類映射到物件識別碼 1.3.36.2.1。  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [組態檔結構描述](../index.md)
- [加密設定架構](index.md)
- [The signature is valid](../../../../standard/security/cryptographic-services.md)
