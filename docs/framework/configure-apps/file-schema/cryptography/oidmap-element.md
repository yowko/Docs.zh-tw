---
title: <oidMap> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
ms.openlocfilehash: 80564c5895e08884f78a4ec7c955ecdb11126e35
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146870"
---
# <a name="oidmap-element"></a>\<oidMap > 項目
包含類別的 ASN.1 物件識別碼 (OID) 對應。  
  
 \<configuration>  
\<mscorlib>  
\<cryptographySettings>  
\<oidMap>  
  
## <a name="syntax"></a>語法  
  
```xml  
<oidMap>   
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<oidEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|將 ASN.1 OID 對應易記的名稱。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`cryptographySettings`|包含密碼編譯設定。|  
|`mscorlib`|包含`cryptographySettings`項目。|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 **\<oidMap >** 項目來包含該雜湊演算法的實作的 RIPEMD-160 雜湊演算法的 OID 的對應。  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"  name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [密碼編譯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [The signature is valid](../../../../../docs/standard/security/cryptographic-services.md)
- [設定密碼編譯類別](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [對應物件識別項至密碼編譯演算法](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
