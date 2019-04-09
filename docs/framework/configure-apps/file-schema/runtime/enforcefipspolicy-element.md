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
ms.openlocfilehash: b1aa958e15449949a1b7ca740198fff71295b2ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59114829"
---
# <a name="enforcefipspolicy-element"></a>\<enforceFIPSPolicy > 項目
指定是否強制執行電腦設定需求，以便讓密碼編譯演算法符合美國聯邦資訊處理標準 (FIPS) 的規範。  
  
 \<組態 > 項目  
\<執行階段 > 項目  
\<enforceFIPSPolicy > 項目  
  
## <a name="syntax"></a>語法  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|enabled|必要屬性。<br /><br /> 指定是否要啟用 強制執行密碼編譯演算法必須是符合 FIPS 規範的電腦設定需求。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`true`|如果您的電腦設定為需要與 FIPS 相容的密碼編譯演算法，會強制執行這項需求。 如果類別實作不符合 FIPS，建構函式是演算法或`Create`在該電腦上執行時，該類別的方法擲回例外狀況。 這是預設值。|  
|`false`|密碼編譯演算法所使用的應用程式不一定要符合 FIPS 規範，不論電腦設定。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 從.NET Framework 2.0 開始，實作密碼編譯演算法之類別的建立是由電腦的設定所控制。 如果電腦已設定為需要演算法，以符合 FIPS，類別會實作不會符合 FIPS 規範的演算法，任何嘗試建立該類別的執行個體就會擲回例外狀況。 建構函式會擲回<xref:System.InvalidOperationException>例外狀況，並`Create`方法會擲回<xref:System.Reflection.TargetInvocationException>例外狀況，並傳回內部<xref:System.InvalidOperationException>例外狀況。  
  
 如果您的應用程式在其組態需要 fips，合規性的電腦上執行您的應用程式會使用與 FIPS 不相容的演算法，您可以使用您的組態檔的這個項目以防止從的 common language runtime (CLR)強制執行的 FIPS 合規性。 這個項目中導入[!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)]。  
  
## <a name="example"></a>範例  
 下列範例示範如何防止 CLR 強制 FIPS 合規性。  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [密碼編譯模型](../../../../../docs/standard/security/cryptography-model.md)
