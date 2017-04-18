---
title: "如何：暫停 Windows 服務 (Visual Basic) | Microsoft Docs"
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
  - "ServiceController.Pause"
helpviewer_keywords: 
  - "暫停 Windows 服務應用程式"
  - "Windows 服務應用程式, 暫停"
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
caps.latest.revision: 17
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 15
---
# 如何：暫停 Windows 服務 (Visual Basic)
本範例使用 <xref:System.ServiceProcess.ServiceController> 元件來暫停本機電腦上的 IIS 管理服務。  
  
## 範例  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 這個程式碼範例也可做為 IntelliSense 程式碼片段。  在程式碼片段選擇器中，它位於 \[**Windows 作業系統**\] \> \[Windows 服務\] 中。  如需詳細資訊，請參閱 [程式碼片段](../Topic/Code%20Snippets.md)。  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System.serviceprocess.dll 的專案參考。  
  
-   對 <xref:System.ServiceProcess> 命名空間成員的存取權。  如果您的程式碼中未完整限定成員名稱，請加入 `Imports` 陳述式。  如需詳細資訊，請參閱 [Imports Statement \(.NET Namespace and Type\)](../../../ocs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。  
  
## 穩固程式設計  
 根據預設，<xref:System.ServiceProcess.ServiceController> 類別的 <xref:System.ServiceProcess.ServiceController.MachineName%2A> 屬性是本機電腦。  若要參考其他電腦上的 Windows 服務，請將 <xref:System.ServiceProcess.ServiceController.MachineName%2A> 屬性變更為該電腦的名稱。  
  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   無法暫停服務   \([InvalidOperationException 類別](frlrfSystemInvalidOperationExceptionClassTopic)\)  
  
-   在存取系統 API 時發生錯誤   \([Win32Exception 類別](frlrfSystemComponentModelWin32ExceptionClassTopic)\)  
  
## .NET Framework 安全性  
 您可以藉由使用 [ServiceControllerPermissionAccess 列舉型別](frlrfSystemServiceProcessServiceControllerPermissionAccessClassTopic)來設定 [ServiceControllerPermission 類別](frlrfSystemServiceProcessServiceControllerPermissionClassTopic)中的使用權限，以限制控制電腦上的服務。  
  
 您可以透過使用 [PermissionState 列舉型別](frlrfSystemSecurityPermissionsPermissionStateClassTopic)來設定 [SecurityPermission 類別](frlrfSystemSecurityPermissionsSecurityPermissionClassTopic)中的使用權限，以限制存取服務資訊。  
  
## 請參閱  
 <xref:System.ServiceProcess.ServiceController>   
 <xref:System.ServiceProcess.ServiceControllerStatus>   
 <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>   
 [如何：繼續執行 Windows 服務 \(Visual Basic\)](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)