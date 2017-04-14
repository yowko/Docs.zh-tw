---
title: "工作流程的 &lt;behaviors&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 工作流程的 &lt;behaviors&gt;
這個項目包含 **serviceBehaviors** 集合。  集合中的每個項目都會定義工作流程服務使用的行為項目。  每個行為項目都由其唯一的 **name** 屬性所識別。  
  
 \<system.ServiceModel\>  
  
## 語法  
  
```  
  
<behaviors>  
   <serviceBehaviors>  
   </serviceBehaviors>  
</behaviors>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<serviceBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|這個組態區段表示為特定工作流程服務定義的所有行為。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<system.serviceModel\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|所有工作流程組態項目的根項目。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>   
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>   
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>   
 [使用行為來設定與擴充執行階段](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)