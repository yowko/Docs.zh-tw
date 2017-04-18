---
title: "如何：繼續執行 Windows 服務 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ServiceController.Continue"
helpviewer_keywords: 
  - "暫停 Windows 服務應用程式"
  - "Windows 服務應用程式, 暫停"
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
caps.latest.revision: 16
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 16
---
# 如何：繼續執行 Windows 服務 (Visual Basic)
本範例使用 <xref:System.ServiceProcess.ServiceController> 元件，繼續進行本機電腦上的 IIS 管理服務。  
  
## 範例  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 這個程式碼範例也可做為 IntelliSense 程式碼片段。  在程式碼片段選擇器中，它位於 \[**Windows 作業系統**\] \> \[Windows 服務\] 中。  如需詳細資訊，請參閱 [程式碼片段](../Topic/Code%20Snippets.md)。  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System.serviceprocess.dll 的專案參考。  
  
-   對 <xref:System.ServiceProcess> 命名空間成員的存取權。  如果您的程式碼中未完整限定成員名稱，請加入 `Imports` 陳述式。  如需詳細資訊，請參閱 [Imports Statement \(.NET Namespace and Type\)](../../../ocs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。  
  
## 穩固程式設計  
 根據預設，<xref:System.ServiceProcess.ServiceController> 類別的 <xref:System.ServiceProcess.ServiceController.MachineName%2A> 屬性是本機電腦。  若要參考其他電腦上的 Windows 服務，請將 <xref:System.ServiceProcess.ServiceController.MachineName%2A> 屬性變更為該電腦的名稱。  
  
 當服務控制程式的狀態變為 <xref:System.ServiceProcess.ServiceControllerStatus> 之後，您才能呼叫該服務的 <xref:System.ServiceProcess.ServiceController.Continue%2A> 方法。  
  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   服務無法繼續執行   \(<xref:System.InvalidOperationException>\)  
  
-   在存取系統 API 時發生錯誤   \(<xref:System.ComponentModel.Win32Exception>\)  
  
## .NET Framework 安全性  
 您可以藉由使用 <xref:System.ServiceProcess.ServiceControllerPermissionAccess> 列舉型別來設定 <xref:System.ServiceProcess.ServiceControllerPermission> 類別中的使用權限，以限制電腦上的服務控制。  
  
 您可以透過使用 <xref:System.Security.Permissions.PermissionState> 列舉型別來設定 <xref:System.Security.Permissions.SecurityPermission> 類別中的使用權限，以限制服務資訊的存取。  
  
## 請參閱  
 <xref:System.ServiceProcess.ServiceController>   
 <xref:System.ServiceProcess.ServiceControllerStatus>   
 [如何：暫停 Windows 服務 \(Visual Basic\)](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)