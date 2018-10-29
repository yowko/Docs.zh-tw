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
ms.openlocfilehash: 255dccfb74eced63ffbeff7ef567083a504cc6da
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48027282"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a>如何：繼續執行 Windows 服務 (Visual Basic)
這個範例會使用 <xref:System.ServiceProcess.ServiceController> 元件，在本機電腦上繼續執行 IIS 管理服務。  
  
## <a name="example"></a>範例  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 這個程式碼範例也可用為 IntelliSense 程式碼片段。 在程式碼片段選擇器中，它位於 [Windows 作業系統] > [Windows 服務] 中。 如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System.serviceprocess.dll 的專案參考。  
  
-   <xref:System.ServiceProcess> 命名空間成員的存取權。 新增 `Imports` 陳述式 (如果未在程式碼中完整限定成員名稱)。 如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。  
  
## <a name="robust-programming"></a>穩固程式設計  
 <xref:System.ServiceProcess.ServiceController> 類別的 <xref:System.ServiceProcess.ServiceController.MachineName%2A> 屬性預設是本機電腦。 若要參考另一部電腦上的 Windows 服務，請將 <xref:System.ServiceProcess.ServiceController.MachineName%2A> 屬性變更為該電腦的名稱。  
  
 在服務控制程式狀態成為 <xref:System.ServiceProcess.ServiceControllerStatus.Paused> 之前，您無法在服務上呼叫 <xref:System.ServiceProcess.ServiceController.Continue%2A> 方法。  
  
 以下條件可能會造成例外狀況：  
  
-   服務無法繼續。 (<xref:System.InvalidOperationException>)  
  
-   存取系統 API 時發生的錯誤。 (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 您可能會使用 <xref:System.ServiceProcess.ServiceControllerPermissionAccess> 列舉來設定 <xref:System.ServiceProcess.ServiceControllerPermission> 類別中的權限，藉以限制電腦上對服務的控制。  
  
 您可能會使用 <xref:System.Security.Permissions.PermissionState> 列舉來設定 <xref:System.Security.Permissions.SecurityPermission> 類別中的權限，藉以限制電腦上對服務資訊的存取。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 [如何：暫停 Windows 服務 (Visual Basic)](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
