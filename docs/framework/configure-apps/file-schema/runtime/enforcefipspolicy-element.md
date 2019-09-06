---
title: <enforceFIPSPolicy> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f90abf9f6c2bc0aed2cf01558b2c0cca4e967e81
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252638"
---
# <a name="enforcefipspolicy-element"></a>\<enforceFIPSPolicy > 元素
指定是否強制執行電腦設定需求，以便讓密碼編譯演算法符合美國聯邦資訊處理標準 (FIPS) 的規範。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<enforceFIPSPolicy>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|enabled|必要屬性。<br /><br /> 指定是否要啟用電腦設定需求，而密碼編譯演算法必須符合 FIPS 規範。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|說明|  
|-----------|-----------------|  
|`true`|如果您的電腦設定為要求密碼編譯演算法符合 FIPS 規範，則會強制執行該需求。 如果類別會執行不符合 FIPS 規範的演算法，則該類別的函`Create`式或方法會在該電腦上執行時擲回例外狀況。 這是預設值。|  
|`false`|無論電腦設定為何，應用程式所使用的密碼編譯演算法都不需要符合 FIPS。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 從 .NET Framework 2.0 開始，建立執行密碼編譯演算法的類別是由電腦的設定所控制。 如果電腦設定為要求演算法必須符合 FIPS，而且類別會執行不符合 FIPS 規範的演算法，則嘗試建立該類別的實例會擲回例外狀況。 函式<xref:System.InvalidOperationException>會擲回例外`Create`狀況，而<xref:System.Reflection.TargetInvocationException>方法會擲回<xref:System.InvalidOperationException>具有內部例外狀況的例外狀況。  
  
 如果您的應用程式在設定需要符合 FIPS 規範的電腦上執行，而且您的應用程式使用不符合 FIPS 規範的演算法，您可以在設定檔案中使用這個元素，以防止 common language runtime （CLR）強制執行 FIPS 合規性。 此元素是在 .NET Framework 2.0 Service Pack 1 中引進。  
  
## <a name="example"></a>範例  
 下列範例顯示如何防止 CLR 強制執行 FIPS 合規性。  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [加密模型](../../../../standard/security/cryptography-model.md)
