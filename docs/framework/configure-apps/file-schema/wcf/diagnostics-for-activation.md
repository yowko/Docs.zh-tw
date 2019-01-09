---
title: 啟用的 &lt;diagnostics&gt;
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 28f051a7ab06dbc1b40f804c56071818eb37e88b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144973"
---
# <a name="ltdiagnosticsgt-for-activation"></a>啟用的 &lt;diagnostics&gt;
設定 Windows Communication Foundation (WCF) 接聽程式的診斷功能。  
  
 \<system.serviceModel.activation>  
\<診斷 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a>類型  
 `Type`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`performanceCountersEnabled`|布林值，指出是否啟用效能計數器以供診斷用途。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|包含 SMSvcHost.exe 接聽程式處理序的組態設定。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
