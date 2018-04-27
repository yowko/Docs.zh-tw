---
title: 如何：在自己的執行緒上顯示每個 Windows Form 以支援 COM Interop
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f5d8a0351fc206aad9d88f9ca3f7c930ff853ff7
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a><span data-ttu-id="e533f-102">如何：在自己的執行緒上顯示每個 Windows Form 以支援 COM Interop</span><span class="sxs-lookup"><span data-stu-id="e533f-102">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>
<span data-ttu-id="e533f-103">您可以藉由在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 訊息迴圈上顯示表單來解決 COM 互通性問題，這可使用 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> 方法來建立。</span><span class="sxs-lookup"><span data-stu-id="e533f-103">You can resolve COM interoperability problems by displaying your form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop, which you can create by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="e533f-104">若要讓 Windows Form 在 COM 用戶端應用程式正確運作，您必須在 Windows Form 訊息迴圈上執行表單。</span><span class="sxs-lookup"><span data-stu-id="e533f-104">To make a Windows Form work correctly from a COM client application, you must run the form on a Windows Forms message loop.</span></span> <span data-ttu-id="e533f-105">若要執行此工作，請使用下列的其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="e533f-105">To do this, use one of the following approaches:</span></span>  
  
-   <span data-ttu-id="e533f-106">使用 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> 方法，以顯示 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="e533f-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form.</span></span> <span data-ttu-id="e533f-107">如需詳細資訊，請參閱[如何：顯示 Windows Form 和 ShowDialog 方法以支援 COM Interop](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)。</span><span class="sxs-lookup"><span data-stu-id="e533f-107">For more information, see [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).</span></span>  
  
-   <span data-ttu-id="e533f-108">在個別執行緒上顯示每個 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="e533f-108">Display each Windows Form on a separate thread.</span></span>  
  
 <span data-ttu-id="e533f-109">沒有對 Visual Studio 中的這項功能有廣泛的支援。</span><span class="sxs-lookup"><span data-stu-id="e533f-109">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="e533f-110">另請參閱 [逐步解說：在自己的執行緒上顯示每個 Windows Form 以支援 COM Interop](http://msdn.microsoft.com/library/ms233639\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="e533f-110">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e533f-111">範例</span><span class="sxs-lookup"><span data-stu-id="e533f-111">Example</span></span>  
 <span data-ttu-id="e533f-112">下列程式碼範例示範如何在個別的執行緒上顯示表單，並呼叫 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> 方法在該執行緒上啟動 Windows Form 訊息幫浦。</span><span class="sxs-lookup"><span data-stu-id="e533f-112">The following code example demonstrates how to display the form on a separate thread and call the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method to start a Windows Forms message pump on that thread.</span></span> <span data-ttu-id="e533f-113">若要使用此方法，您必須使用 <xref:System.Windows.Forms.Control.Invoke%2A> 方法封送處理任何呼叫至來自 Unmanaged 應用程式的表單。</span><span class="sxs-lookup"><span data-stu-id="e533f-113">To use this approach, you must marshal any calls to the form from the unmanaged application by using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span>  
  
 <span data-ttu-id="e533f-114">此方法需要表單的每個執行個體使用它自己的訊息迴圈在自己的執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="e533f-114">This approach requires that each instance of a form runs on its own thread by using its own message loop.</span></span> <span data-ttu-id="e533f-115">在每個執行緒中，您不能執行一個以上的訊息迴圈。</span><span class="sxs-lookup"><span data-stu-id="e533f-115">You cannot have more than one message loop running per thread.</span></span> <span data-ttu-id="e533f-116">因此，您無法變更用戶端應用程式的訊息迴圈。</span><span class="sxs-lookup"><span data-stu-id="e533f-116">Therefore, you cannot change the client application's message loop.</span></span> <span data-ttu-id="e533f-117">不過，您可以修改 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 元件來啟動會使用自己的訊息迴圈之新執行緒。</span><span class="sxs-lookup"><span data-stu-id="e533f-117">However, you can modify the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] component to start a new thread that uses its own message loop.</span></span>  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e533f-118">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e533f-118">Compiling the Code</span></span>  
  
-   <span data-ttu-id="e533f-119">請將 `COMForm`、 `Form1`和 `FormManager` 類型編譯至稱為 `COMWinform.dll`的組件中。</span><span class="sxs-lookup"><span data-stu-id="e533f-119">Compile the `COMForm`, `Form1`, and `FormManager` types into an assembly called `COMWinform.dll`.</span></span> <span data-ttu-id="e533f-120">請使用 [Packaging an Assembly for COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)所述的其中一種方法來登錄 COM Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="e533f-120">Register the assembly for COM interop by using one of the methods described in [Packaging an Assembly for COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span> <span data-ttu-id="e533f-121">您現在可以在 Unmanaged 應用程式中使用該組件和對應的類型程式庫 (.tlb) 檔案。</span><span class="sxs-lookup"><span data-stu-id="e533f-121">You can now use the assembly and its corresponding type library (.tlb) file in unmanaged applications.</span></span> <span data-ttu-id="e533f-122">例如，您可以使用類型程式庫做為 Visual Basic 6.0 可執行檔專案中的參考。</span><span class="sxs-lookup"><span data-stu-id="e533f-122">For example, you can use the type library as a reference in a Visual Basic 6.0 executable project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e533f-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e533f-123">See Also</span></span>  
 [<span data-ttu-id="e533f-124">將 .NET Framework 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="e533f-124">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="e533f-125">封裝 COM 的組件</span><span class="sxs-lookup"><span data-stu-id="e533f-125">Packaging an Assembly for COM</span></span>](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [<span data-ttu-id="e533f-126">向 COM 註冊組件</span><span class="sxs-lookup"><span data-stu-id="e533f-126">Registering Assemblies with COM</span></span>](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [<span data-ttu-id="e533f-127">操作說明：顯示 Windows Forms 和 ShowDialog 方法以支援 COM Interop</span><span class="sxs-lookup"><span data-stu-id="e533f-127">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [<span data-ttu-id="e533f-128">Windows Forms 和 Unmanaged 應用程式概觀</span><span class="sxs-lookup"><span data-stu-id="e533f-128">Windows Forms and Unmanaged Applications Overview</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)
