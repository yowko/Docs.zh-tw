---
title: 作法：繼續執行 Windows 服務 (Visual Basic)
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
ms.openlocfilehash: a10e05b0460608a9e67ee4527adf80be3d47438e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053631"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="7a814-102">作法：繼續執行 Windows 服務 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a814-102">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="7a814-103">這個範例會使用 <xref:System.ServiceProcess.ServiceController> 元件，在本機電腦上繼續執行 IIS 管理服務。</span><span class="sxs-lookup"><span data-stu-id="7a814-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a814-104">範例</span><span class="sxs-lookup"><span data-stu-id="7a814-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="7a814-105">這個程式碼範例也可用為 IntelliSense 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="7a814-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="7a814-106">在程式碼片段選擇器中，它位於 [Windows 作業系統] > [Windows 服務] 中。</span><span class="sxs-lookup"><span data-stu-id="7a814-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="7a814-107">如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="7a814-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7a814-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="7a814-108">Compiling the Code</span></span>  
 <span data-ttu-id="7a814-109">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="7a814-109">This example requires:</span></span>  
  
- <span data-ttu-id="7a814-110">System.serviceprocess.dll 的專案參考。</span><span class="sxs-lookup"><span data-stu-id="7a814-110">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="7a814-111"><xref:System.ServiceProcess> 命名空間成員的存取權。</span><span class="sxs-lookup"><span data-stu-id="7a814-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="7a814-112">新增 `Imports` 陳述式 (如果未在程式碼中完整限定成員名稱)。</span><span class="sxs-lookup"><span data-stu-id="7a814-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="7a814-113">如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="7a814-113">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="7a814-114">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="7a814-114">Robust Programming</span></span>  
 <span data-ttu-id="7a814-115"><xref:System.ServiceProcess.ServiceController> 類別的 <xref:System.ServiceProcess.ServiceController.MachineName%2A> 屬性預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="7a814-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="7a814-116">若要參考另一部電腦上的 Windows 服務，請將 <xref:System.ServiceProcess.ServiceController.MachineName%2A> 屬性變更為該電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="7a814-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="7a814-117">在服務控制程式狀態成為 <xref:System.ServiceProcess.ServiceControllerStatus.Paused> 之前，您無法在服務上呼叫 <xref:System.ServiceProcess.ServiceController.Continue%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7a814-117">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="7a814-118">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="7a814-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="7a814-119">服務無法繼續。</span><span class="sxs-lookup"><span data-stu-id="7a814-119">The service cannot be resumed.</span></span> <span data-ttu-id="7a814-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="7a814-120">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="7a814-121">存取系統 API 時發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="7a814-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="7a814-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="7a814-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7a814-123">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="7a814-123">.NET Framework Security</span></span>  
 <span data-ttu-id="7a814-124">您可能會使用 <xref:System.ServiceProcess.ServiceControllerPermissionAccess> 列舉來設定 <xref:System.ServiceProcess.ServiceControllerPermission> 類別中的權限，藉以限制電腦上對服務的控制。</span><span class="sxs-lookup"><span data-stu-id="7a814-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="7a814-125">您可能會使用 <xref:System.Security.Permissions.PermissionState> 列舉來設定 <xref:System.Security.Permissions.SecurityPermission> 類別中的權限，藉以限制電腦上對服務資訊的存取。</span><span class="sxs-lookup"><span data-stu-id="7a814-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a814-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a814-126">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- [<span data-ttu-id="7a814-127">如何：暫停 Windows 服務 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a814-127">How to: Pause a Windows Service (Visual Basic)</span></span>](how-to-pause-a-windows-service-visual-basic.md)
