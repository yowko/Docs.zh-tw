---
title: "1031 - CompleteFaultWorkItem | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1031 - CompleteFaultWorkItem
## 屬性  
  
|||  
|-|-|  
|ID|1031|  
|關鍵字|WFRuntime|  
|層級|詳細資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示 FaultWorkItem 已完成。  
  
## 訊息  
 已完成活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 的 FaultWorkItem。  活動 '%4'、DisplayName：'%5'、InstanceId：'%6' 傳回例外狀況。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|FaultActivity|xs:string|錯誤活動的型別名稱。|  
|FaultActivityDisplayName|xs:string|錯誤活動的顯示名稱。|  
|FaultActivityInstanceId|xs:string|錯誤活動的執行個體 ID。|  
|ExceptionActivity|xs:string|擲回例外狀況之活動的型別名稱。|  
|ExceptionActivityDisplayName|xs:string|擲回例外狀況之活動的顯示名稱。|  
|ExceptionActivityInstanceId|xs:string|擲回例外狀況之活動的執行個體 ID。|  
|例外狀況|xs:string|例外狀況的例外狀況詳細資料|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|