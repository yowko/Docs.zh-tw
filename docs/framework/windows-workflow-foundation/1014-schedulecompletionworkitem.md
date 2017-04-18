---
title: "1014 - ScheduleCompletionWorkItem | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1014 - ScheduleCompletionWorkItem
## 屬性  
  
|||  
|-|-|  
|ID|1014|  
|關鍵字|WFRuntime|  
|層級|詳細資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示已排定 CompletionWorkItem。  
  
## 訊息  
 已排定父活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 CompletionWorkItem。已完成活動 '%4'、DisplayName：'%5'、InstanceId：'%6'。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|ParentActivity|xs:string|父活動的型別名稱。|  
|ParentDisplayName|xs:string|父活動的顯示名稱。|  
|ParentInstanceId|xs:string|父活動的執行個體 ID。|  
|CompletedActivity|xs:string|已完成之活動的型別名稱。|  
|CompletedActivityDisplayName|xs:string|已完成之活動的顯示名稱。|  
|CompletedActivityInstanceId|xs:string|已完成之活動的執行個體 ID。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|