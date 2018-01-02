---
title: "&lt;enforceFIPSPolicy&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fb8cb1ea4d011eb25aee14ddd53d3dc882f75d8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltenforcefipspolicygt-element"></a>&lt;enforceFIPSPolicy&gt;項目
指定是否強制執行電腦設定需求，以便讓密碼編譯演算法符合美國聯邦資訊處理標準 (FIPS) 的規範。  
  
 \<設定 > 項目  
\<runtime > 項目  
\<enforceFIPSPolicy > 項目  
  
## <a name="syntax"></a>語法  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|enabled|必要屬性。<br /><br /> 指定是否要啟用 強制執行密碼編譯演算法必須與 FIPS 相容的電腦設定需求。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`true`|如果您的電腦設定為需要與 FIPS 相容的密碼編譯演算法時，會強制執行這項需求。 如果類別實作的演算法不會符合 FIPS，建構函式或`Create`該電腦上執行時，該類別的方法擲回例外狀況。 這是預設值。|  
|`false`|密碼編譯演算法所使用的應用程式不一定要符合 FIPS，不論電腦組態。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 從.NET Framework 2.0 開始，實作密碼編譯演算法之類別的建立是由電腦的設定所控制。 如果電腦已設定為需要演算法，以符合 FIPS，類別會實作與 FIPS 不相容的演算法，任何嘗試建立該類別的執行個體就會擲回例外狀況。 建構函式會擲回<xref:System.InvalidOperationException>例外狀況，以及`Create`方法會擲回<xref:System.Reflection.TargetInvocationException>例外狀況，並傳回內部<xref:System.InvalidOperationException>例外狀況。  
  
 如果您的應用程式在其設定，都需要使用 FIPS，相容性的電腦上執行您的應用程式會使用與 FIPS 不相容的演算法，您可以防止 common language runtime (CLR) 來自組態檔中使用這個項目強制使用 FIPS 相容性。 中引進這個項目[!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)]。  
  
## <a name="example"></a>範例  
 下列範例會示範如何防止 CLR 強制使用 FIPS 相容性。  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [加密模型](../../../../../docs/standard/security/cryptography-model.md)
