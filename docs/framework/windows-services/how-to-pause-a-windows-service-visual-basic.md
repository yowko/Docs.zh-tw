---
title: 作法：暫停 Windows 服務 (Visual Basic)
description: 瞭解如何使用 ServiceController 元件，在本機電腦上使用 Visual Basic 來暫停 Windows 服務 (例如 IIS Admin service) 。
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
ms.openlocfilehash: 19919a8b0a289f0e88eb136d8c010a036e84cbec
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608500"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="9f634-103">作法：暫停 Windows 服務 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f634-103">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="9f634-104">這個範例會使用 <xref:System.ServiceProcess.ServiceController> 元件，在本機電腦上暫停 IIS 管理服務。</span><span class="sxs-lookup"><span data-stu-id="9f634-104">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f634-105">範例</span><span class="sxs-lookup"><span data-stu-id="9f634-105">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="9f634-106">這個程式碼範例也可用為 IntelliSense 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="9f634-106">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="9f634-107">在程式碼片段選擇器中，它位於 [Windows 作業系統] > [Windows 服務]\*\*\*\* 中。</span><span class="sxs-lookup"><span data-stu-id="9f634-107">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="9f634-108">如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="9f634-108">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9f634-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="9f634-109">Compiling the Code</span></span>  
 <span data-ttu-id="9f634-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="9f634-110">This example requires:</span></span>  
  
- <span data-ttu-id="9f634-111">System.serviceprocess.dll 的專案參考。</span><span class="sxs-lookup"><span data-stu-id="9f634-111">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="9f634-112"><xref:System.ServiceProcess> 命名空間成員的存取權。</span><span class="sxs-lookup"><span data-stu-id="9f634-112">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="9f634-113">新增 `Imports` 陳述式 (如果未在程式碼中完整限定成員名稱)。</span><span class="sxs-lookup"><span data-stu-id="9f634-113">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="9f634-114">如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="9f634-114">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9f634-115">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="9f634-115">Robust Programming</span></span>  
 <span data-ttu-id="9f634-116"><xref:System.ServiceProcess.ServiceController> 類別的 <xref:System.ServiceProcess.ServiceController.MachineName%2A> 屬性預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="9f634-116">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="9f634-117">若要參考另一部電腦上的 Windows 服務，請將 <xref:System.ServiceProcess.ServiceController.MachineName%2A> 屬性變更為該電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f634-117">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="9f634-118">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="9f634-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="9f634-119">無法暫停服務。</span><span class="sxs-lookup"><span data-stu-id="9f634-119">The service cannot be paused.</span></span> <span data-ttu-id="9f634-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="9f634-120">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="9f634-121">存取系統 API 時發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="9f634-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="9f634-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="9f634-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9f634-123">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="9f634-123">.NET Framework Security</span></span>  
 <span data-ttu-id="9f634-124">您可能會使用 <xref:System.ServiceProcess.ServiceControllerPermissionAccess> 來設定 <xref:System.ServiceProcess.ServiceControllerPermission> 中的權限，藉以限制電腦上對服務的控制。</span><span class="sxs-lookup"><span data-stu-id="9f634-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="9f634-125">您可能會使用 <xref:System.Security.Permissions.PermissionState> 來設定 <xref:System.Security.Permissions.SecurityPermission> 中的權限，藉以限制電腦上對服務資訊的存取。</span><span class="sxs-lookup"><span data-stu-id="9f634-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f634-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f634-126">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [<span data-ttu-id="9f634-127">作法：繼續執行 Windows 服務 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f634-127">How to: Continue a Windows Service (Visual Basic)</span></span>](how-to-continue-a-windows-service-visual-basic.md)
