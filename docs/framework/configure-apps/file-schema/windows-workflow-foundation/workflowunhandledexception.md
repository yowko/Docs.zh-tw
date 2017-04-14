---
title: "&lt;workflowUnhandledException&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;workflowUnhandledException&gt;
這個服務行為可讓您指定工作流程服務內發生未處理的例外狀況時要採取的動作。  
  
## 語法  
  
```  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name=String">  
      <workflowUnhandledException action=”Abandon/AbandonAndSuspend/Cancel/Terminate” />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|action|字串，可指定發生未處理的例外狀況時要採取的動作。  此屬性的型別為 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionaction>。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<serviceBehaviors\> 的 \<behavior\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|指定行為項目。|  
  
## 請參閱  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>   
 <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>