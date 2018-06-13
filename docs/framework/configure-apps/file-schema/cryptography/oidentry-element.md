---
title: '&lt;oidEntry&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: db209bac487ccbb98f7f0aeb272f51169e7a0148
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746351"
---
# <a name="ltoidentrygt-element"></a>&lt;oidEntry&gt;項目
將 ASN.1 物件識別碼 (OID) 對應至易記名稱。  
  
 \<configuration>  
\<mscorlib >  
\<cryptographySettings >  
\<oidMap >  
\<oidEntry >  
  
## <a name="syntax"></a>語法  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|**OID**|必要屬性。<br /><br /> 指定對應至您的類別所實作的演算法的 ASN.1 OID。|  
|**name**|必要屬性。<br /><br /> 指定的值**名稱**屬性[ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)標記。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`cryptographySettings`|包含密碼編譯設定。|  
|`mscorlib`|包含`cryptographySettings`項目。|  
|`oidMap`|包含類別到 ASN.1 物件識別碼 (OID) 對應。|  
  
## <a name="remarks"></a>備註  
 ASN.1 物件識別項識別中某些加密格式的演算法。 將物件識別碼對應至您想要識別演算法的易記名稱。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 **\<oidEntry >** 項目，將 ripemd-160 雜湊演算法的物件識別碼對應至該雜湊演算法的實作。  
  
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
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [密碼編譯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [密碼編譯服務](../../../../../docs/standard/security/cryptographic-services.md)  
 [設定密碼編譯類別](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [對應物件識別項至密碼編譯演算法](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
