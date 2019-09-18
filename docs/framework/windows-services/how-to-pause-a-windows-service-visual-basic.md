---
title: HOW TO：暫停 Windows 服務 (Visual Basic)
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
author: ghogen
ms.openlocfilehash: 166eda4a9348188fa6e5048fd3ce41645cde4816
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053603"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a>作法：暫停 Windows 服務 (Visual Basic)
這個範例會使用 <xref:System.ServiceProcess.ServiceController> 元件，在本機電腦上暫停 IIS 管理服務。  
  
## <a name="example"></a>範例  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 這個程式碼範例也可用為 IntelliSense 程式碼片段。 在程式碼片段選擇器中，它位於 [Windows 作業系統] > [Windows 服務] 中。 如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- System.serviceprocess.dll 的專案參考。  
  
- <xref:System.ServiceProcess> 命名空間成員的存取權。 新增 `Imports` 陳述式 (如果未在程式碼中完整限定成員名稱)。 如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。  
  
## <a name="robust-programming"></a>穩固程式設計  
 <xref:System.ServiceProcess.ServiceController> 類別的 <xref:System.ServiceProcess.ServiceController.MachineName%2A> 屬性預設是本機電腦。 若要參考另一部電腦上的 Windows 服務，請將 <xref:System.ServiceProcess.ServiceController.MachineName%2A> 屬性變更為該電腦的名稱。  
  
 以下條件可能會造成例外狀況：  
  
- 無法暫停服務。 (<xref:System.InvalidOperationException>)  
  
- 存取系統 API 時發生的錯誤。 (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 您可能會使用 <xref:System.ServiceProcess.ServiceControllerPermissionAccess> 來設定 <xref:System.ServiceProcess.ServiceControllerPermission> 中的權限，藉以限制電腦上對服務的控制。  
  
 您可能會使用 <xref:System.Security.Permissions.PermissionState> 來設定 <xref:System.Security.Permissions.SecurityPermission> 中的權限，藉以限制電腦上對服務資訊的存取。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [如何：繼續執行 Windows 服務 (Visual Basic)](how-to-continue-a-windows-service-visual-basic.md)
