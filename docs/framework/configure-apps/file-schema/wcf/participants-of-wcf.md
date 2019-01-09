---
title: WCF 的 &lt;participants&gt;
ms.date: 03/30/2017
ms.assetid: d99dbddc-0057-4e18-8e42-f91411d39970
ms.openlocfilehash: 341e5492f7a45ca89c18d478766b8ebd369dbdf2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151838"
---
# <a name="ltparticipantsgt-of-wcf"></a>WCF 的 &lt;participants&gt;
設定追蹤參與者的清單，這些參與者接聽執行階段直接發出的追蹤記錄並處理這些記錄，無論記錄的設定為何。 這包括寫入至特定的輸出 (例如檔案、主控台、ETW)、處理/彙總記錄，或任何其他可能需要的組合。  
  
 如需工作流程追蹤及追蹤參與者的詳細資訊，請參閱[工作流程追蹤](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)並[追蹤參與者](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)。  
  
 \<system.serviceModel>  
\<追蹤 >  
\<參與者 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/add-of-participants.md)|包含追蹤參與者的設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<追蹤 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|代表定義工作流程服務之追蹤設定的組態區段。|  
  
## <a name="remarks"></a>備註  
 追蹤參與者是用來取得自工作流程發出的追蹤資料，然後將資料儲存至不同的媒體。 同樣地，追蹤記錄的任何後期處理也可在追蹤參與者之中完成。  
  
 多個追蹤參與者可同時使用追蹤事件。 每個追蹤參與者都可以與不同的追蹤設定檔相關聯。  
  
 此處提供標準的追蹤參與者，可將追蹤記錄寫入至 ETW 工作階段。 透過在設定檔中加入特定追蹤的行為，您可以設定工作流程服務上的參與者。 啟用 ETW 追蹤參與者可在事件檢視器中檢視追蹤記錄。 如果不符合需求，您也可以寫入自訂的追蹤參與者。  
  
## <a name="example"></a>範例  
 以下組態範例顯示在 Web.config 檔案中設定的標準 ETW 追蹤參與者。  
  
 ETW 追蹤參與者用來寫入追蹤記錄至 ETW 的提供者識別碼會定義於 `<diagnostics>` 區段。 追蹤參與者擁有與其相關聯的設定檔，以指定已經訂閱的追蹤記錄。 這是由 `profileName` 項目的 `<add>` 屬性所定義。 一旦這些定義完成，追蹤參與者就會加入至 `<etwTracking>` 服務行為。 如此會將選取的追蹤參與者加入至工作流程執行個體的擴充，因此，追蹤參與者可開始接收追蹤記錄。  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0" />
  </system.web>
  <system.serviceModel>
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />
    <tracking>
      <participants>
        <add name="EtwTrackingParticipant"
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
             profileName="HealthMonitoring_Tracking_Profile"/>
      </participants>
    </tracking>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile"/>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 [工作流程追蹤及追蹤](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [追蹤參與者](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
