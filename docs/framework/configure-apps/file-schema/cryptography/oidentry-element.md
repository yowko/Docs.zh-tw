---
title: <oidEntry> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: 4564cf59e3b6cfbdcd9dca06cd0f966d524834de
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088554"
---
# <a name="oidentry-element"></a>\<oidEntry> 項目
將 ASN.1 物件識別碼 (OID) 對應至易記名稱。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**

## <a name="syntax"></a>語法  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|**OID**|必要屬性。<br /><br /> 指定對應至您的類別所實演算法的 asn.1 OID。|  
|**name**|必要屬性。<br /><br /> 指定標記中**name**屬性的值 [\<nameEntry>](nameentry-element.md) 。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`cryptographySettings`|包含密碼編譯設定。|  
|`mscorlib`|包含 `cryptographySettings` 元素。|  
|`oidMap`|包含對類別的 asn.1 物件識別元（OID）對應。|  
  
## <a name="remarks"></a>備註  
 Asn.1 物件識別碼會識別一些密碼編譯格式的演算法。 將物件識別碼對應至您想要識別之演算法的易記名稱。  
  
## <a name="example"></a>範例  
 下列範例顯示如何使用專案，將 **\<oidEntry>** RIPEMD-160 雜湊演算法的物件識別碼對應至該雜湊演算法的執行。  
  
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

- [設定檔架構](../index.md)
- [密碼編譯設定結構描述](index.md)
- [密碼編譯服務](../../../../standard/security/cryptographic-services.md)
- [設定密碼編譯類別](../../configure-cryptography-classes.md)
- [對應物件識別項至密碼編譯演算法](../../map-object-identifiers-to-cryptography-algorithms.md)
