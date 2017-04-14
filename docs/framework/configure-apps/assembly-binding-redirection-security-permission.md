---
title: "組件繫結重新導向安全性使用權限 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "組件 [.NET Framework], 繫結重新導向"
  - "並存執行, 組件繫結重新導向"
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# 組件繫結重新導向安全性使用權限
在應用程式組態檔中進行明確的組件繫結重新導向必須擁有安全性權限。  這適用於 .NET Framework 組件和協力廠商組件的重新導向。  使用權限的授與方式是，在 [SecurityPermission Class](frlrfSystemSecurityPermissionsSecurityPermissionClassTopic)上設定 [BindingRedirects](frlrfSystemSecurityPermissionsSecurityPermissionFlagClassTopic) 旗標。  Managed 組件預設沒有任何使用權限。  
  
 安全性使用權限是授與給在受信任區域 \(本機電腦\) 和內部網路區域中執行的應用程式。  在網際網路區域中執行的應用程式則受到嚴格禁止，不能執行組件繫結重新導向。  
  
 如果在元件發行者控制的發行者原則檔或是系統管理員控制的電腦組態檔中執行組件重新導向，就不需要任何使用權限。  然而，應用程式需要使用權限，來明確忽略於應用程式組態檔中使用[\<publisherPolicy apply\="no"\/\>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) 項目的發行者原則。  
  
 以下的表格顯示 **BindingRedirects** 旗標的預設安全性設定。  
  
|區域|BindingRedirects 旗標設定|  
|--------|---------------------------|  
|受信任區域 \(本機電腦\)|**ON**|  
|內部網路區域|**ON**|  
|網際網路區域|**OFF**|  
|未受信任區域|**OFF**|  
  
 系統管理員可以變更這些安全性設定，以支援或限制給定電腦上的特定案例。  沒有任何工具可以變更 **BindingRedirects** 旗標的預設設定；系統管理員必須手動編輯使用者電腦上的 Security.config 檔案。  
  
## 請參閱  
 [Publisher Policy Files and Side\-by\-Side Execution](http://msdn.microsoft.com/zh-tw/97a042be-4d72-40c3-91c0-76fd36bdf133)   
 [如何：啟用和停用自動繫結重新導向](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)   
 [並存執行](../../../docs/framework/deployment/side-by-side-execution.md)