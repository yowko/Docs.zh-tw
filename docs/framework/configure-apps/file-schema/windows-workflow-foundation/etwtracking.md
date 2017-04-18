---
title: "&lt;etwTracking&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;etwTracking&gt;
可讓服務透過使用 <xref:System.Activities.Tracking.ETWTrackingParticipant> 來利用 ETW 進行追蹤的服務行為。  
  
## 語法  
  
```  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name=String">  
      <etwTracking profileName=”String” />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|profileName|可指定與這個行為相關聯的追蹤設定檔名稱的字串。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<serviceBehaviors\> 的 \<behavior\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|指定行為項目。|  
  
## 備註  
 加入至服務的行為組態時，這個組態項目會在工作流程服務中，設定追蹤參與者。  
  
 追蹤參與者是用來取得自工作流程發出的追蹤資料，然後將資料儲存至不同的媒體。  同樣地，追蹤記錄的任何後期處理也可在追蹤參與者之中完成。  
  
## 範例  
 以下組態範例顯示在 Web.config 檔案中設定的標準 ETW 追蹤參與者。  
  
 ETW 追蹤參與者用來寫入追蹤記錄至 ETW 的提供者識別碼會定義於 **\<diagnostics\>** 區段。  追蹤參與者擁有與其相關聯的設定檔，以指定已經訂閱的追蹤記錄。  這是由 **profileName** 項目的 **\<add\>** 屬性所定義。  一旦這些定義完成，追蹤參與者就會加入至 **\<etwTracking\>** 服務行為。  如此會將選取的追蹤參與者加入至工作流程執行個體的擴充，因此，追蹤參與者可開始接收追蹤記錄。  
  
```  
  
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
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
  
## 請參閱  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>   
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>   
 [工作流程追蹤與追查](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)   
 [追蹤參與者](../../../../../docs/framework/windows-workflow-foundation//tracking-participants.md)