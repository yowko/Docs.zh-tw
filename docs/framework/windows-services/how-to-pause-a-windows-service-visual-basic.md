---
title: "如何：暫停 Windows 服務 (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
f1_keywords: ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
caps.latest.revision: "17"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 90f2b01fae057a05cc71f77cecea3fdf85c832b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="34011-102">如何：暫停 Windows 服務 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34011-102">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="34011-103">這個範例會使用<xref:System.ServiceProcess.ServiceController>元件暫停本機電腦上的 IIS 管理服務。</span><span class="sxs-lookup"><span data-stu-id="34011-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34011-104">範例</span><span class="sxs-lookup"><span data-stu-id="34011-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="34011-105">這個程式碼範例也可用為 IntelliSense 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="34011-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="34011-106">在程式碼片段選擇器中，位於**Windows 作業系統 > Windows 服務**。</span><span class="sxs-lookup"><span data-stu-id="34011-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="34011-107">如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="34011-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="34011-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="34011-108">Compiling the Code</span></span>  
 <span data-ttu-id="34011-109">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="34011-109">This example requires:</span></span>  
  
-   <span data-ttu-id="34011-110">System.serviceprocess.dll 專案參考。</span><span class="sxs-lookup"><span data-stu-id="34011-110">A project reference to System.serviceprocess.dll.</span></span>  
  
-   <span data-ttu-id="34011-111"><xref:System.ServiceProcess> 命名空間成員的存取權。</span><span class="sxs-lookup"><span data-stu-id="34011-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="34011-112">新增 `Imports` 陳述式 (如果未在程式碼中完整限定成員名稱)。</span><span class="sxs-lookup"><span data-stu-id="34011-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="34011-113">如需詳細資訊，請參閱 [Imports 陳述式 (.NET 命名空間和類型)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。</span><span class="sxs-lookup"><span data-stu-id="34011-113">For more information, see [Imports Statement (.NET Namespace and Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="34011-114">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="34011-114">Robust Programming</span></span>  
 <span data-ttu-id="34011-115"><xref:System.ServiceProcess.ServiceController.MachineName%2A>屬性<xref:System.ServiceProcess.ServiceController>類別是預設的本機電腦。</span><span class="sxs-lookup"><span data-stu-id="34011-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="34011-116">若要參考另一部電腦上的 Windows 服務，變更<xref:System.ServiceProcess.ServiceController.MachineName%2A>屬性設為該電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="34011-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="34011-117">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="34011-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="34011-118">無法暫停服務。</span><span class="sxs-lookup"><span data-stu-id="34011-118">The service cannot be paused.</span></span> <span data-ttu-id="34011-119">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="34011-119">(<xref:System.InvalidOperationException>)</span></span>  
  
-   <span data-ttu-id="34011-120">存取系統 API 時發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="34011-120">An error occurred when accessing a system API.</span></span> <span data-ttu-id="34011-121">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="34011-121">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="34011-122">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="34011-122">.NET Framework Security</span></span>  
 <span data-ttu-id="34011-123">控制服務的電腦上可能會受到使用<xref:System.ServiceProcess.ServiceControllerPermissionAccess>中設定權限<xref:System.ServiceProcess.ServiceControllerPermission>。</span><span class="sxs-lookup"><span data-stu-id="34011-123">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="34011-124">服務資訊的存取權可能會受到使用<xref:System.Security.Permissions.PermissionState>中設定權限<xref:System.Security.Permissions.SecurityPermission>。</span><span class="sxs-lookup"><span data-stu-id="34011-124">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34011-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="34011-125">See Also</span></span>  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>  
 [<span data-ttu-id="34011-126">如何：繼續執行 Windows 服務 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34011-126">How to: Continue a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
