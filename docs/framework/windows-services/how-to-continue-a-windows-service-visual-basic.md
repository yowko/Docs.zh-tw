---
title: 如何：繼續執行 Windows 服務 (Visual Basic)
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
author: ghogen
manager: douge
ms.openlocfilehash: 15ef15e0afe43d56db0972a686cd093e22c672dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a>如何：繼續執行 Windows 服務 (Visual Basic)
這個範例會使用<xref:System.ServiceProcess.ServiceController>繼續在本機電腦上的 IIS 管理服務元件。  
  
## <a name="example"></a>範例  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 這個程式碼範例也可用為 IntelliSense 程式碼片段。 在程式碼片段選擇器中，位於**Windows 作業系統 > Windows 服務**。 如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System.serviceprocess.dll 專案參考。  
  
-   <xref:System.ServiceProcess> 命名空間成員的存取權。 新增 `Imports` 陳述式 (如果未在程式碼中完整限定成員名稱)。 如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。  
  
## <a name="robust-programming"></a>穩固程式設計  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A>屬性<xref:System.ServiceProcess.ServiceController>類別是預設的本機電腦。 若要參考另一部電腦上的 Windows 服務，變更<xref:System.ServiceProcess.ServiceController.MachineName%2A>屬性設為該電腦的名稱。  
  
 您不能呼叫<xref:System.ServiceProcess.ServiceController.Continue%2A>方法上的服務，直到服務控制站狀態<xref:System.ServiceProcess.ServiceControllerStatus.Paused>。  
  
 以下條件可能會造成例外狀況：  
  
-   服務無法繼續。 (<xref:System.InvalidOperationException>)  
  
-   存取系統 API 時發生的錯誤。 (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 控制服務的電腦上可能會受到使用<xref:System.ServiceProcess.ServiceControllerPermissionAccess>中設定權限的列舉<xref:System.ServiceProcess.ServiceControllerPermission>類別。  
  
 服務資訊的存取權可能會受到使用<xref:System.Security.Permissions.PermissionState>中設定權限的列舉<xref:System.Security.Permissions.SecurityPermission>類別。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 [如何：暫停 Windows 服務 (Visual Basic)](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
