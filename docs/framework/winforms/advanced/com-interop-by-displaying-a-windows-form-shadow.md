---
title: "如何：顯示 Windows Form 和 ShowDialog 方法以支援 COM Interop"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop [Windows Forms], calling methods
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: 87aac8ad-3c04-43b3-9b0c-d0b00df9ee74
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 415ffebbcf196a163932b1b83e32a6128f0bf1a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a><span data-ttu-id="a9e9d-102">如何：顯示 Windows Form 和 ShowDialog 方法以支援 COM Interop</span><span class="sxs-lookup"><span data-stu-id="a9e9d-102">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>
<span data-ttu-id="a9e9d-103">您可以藉由在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 訊息迴圈上顯示 Windows Forms 來解決元件物件模型 (COM) 互通性問題，而此訊息迴圈是使用 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> 方法建立而成。</span><span class="sxs-lookup"><span data-stu-id="a9e9d-103">You can resolve Component Object Model (COM) interoperability problems by displaying your Windows Form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop, which is created by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="a9e9d-104">為了讓表單能夠在 COM 用戶端應用程式中正確運作，您必須在 Windows Forms 訊息迴圈上執行它。</span><span class="sxs-lookup"><span data-stu-id="a9e9d-104">To make a form work correctly from a COM client application, you must run it on a Windows Forms message loop.</span></span> <span data-ttu-id="a9e9d-105">若要執行此工作，請使用下列的其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="a9e9d-105">To do this, use one of the following approaches:</span></span>  
  
-   <span data-ttu-id="a9e9d-106">使用 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> 方法，以顯示 Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="a9e9d-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form;</span></span>  
  
-   <span data-ttu-id="a9e9d-107">在個別執行緒上顯示每個 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="a9e9d-107">Display each Windows Form on a separate thread.</span></span> <span data-ttu-id="a9e9d-108">如需詳細資訊，請參閱 [How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)。</span><span class="sxs-lookup"><span data-stu-id="a9e9d-108">For more information, see [How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="a9e9d-109">程序</span><span class="sxs-lookup"><span data-stu-id="a9e9d-109">Procedure</span></span>  
 <span data-ttu-id="a9e9d-110">若要在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 訊息迴圈上顯示表單，最簡單的方式是使用 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> 方法，因為在所有方法中，它所需實作的程式碼最少。</span><span class="sxs-lookup"><span data-stu-id="a9e9d-110">Using the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method can be the easiest way to display a form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop because, of all the approaches, it requires the least code to implement.</span></span>  
  
 <span data-ttu-id="a9e9d-111"><xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> 方法會暫止 Unmanaged 應用程式的訊息迴圈，並將表單顯示成對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a9e9d-111">The <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method suspends the unmanaged application's message loop and displays the form as a dialog box.</span></span> <span data-ttu-id="a9e9d-112">因為主應用程式的訊息迴圈已經暫止，所以 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> 方法會建立新的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 訊息迴圈來處理表單的訊息。</span><span class="sxs-lookup"><span data-stu-id="a9e9d-112">Because the host application's message loop has been suspended, the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method creates a new [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop to process the form's messages.</span></span>  
  
 <span data-ttu-id="a9e9d-113">使用 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> 方法的缺點是表單會被開啟為強制回應對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a9e9d-113">The disadvantage of using the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method is that the form will be opened as a modal dialog box.</span></span> <span data-ttu-id="a9e9d-114">當 Windows Forms 開啟時，這個行為會封鎖呼叫應用程式中的任何使用者介面 (UI)。</span><span class="sxs-lookup"><span data-stu-id="a9e9d-114">This behavior blocks any user interface (UI) in the calling application while the Windows Form is open.</span></span> <span data-ttu-id="a9e9d-115">當使用者結束表單時， [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 訊息迴圈便會關閉，而先前應用程式的訊息迴圈會再次開始執行。</span><span class="sxs-lookup"><span data-stu-id="a9e9d-115">When the user exits the form, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop closes and the earlier application's message loop starts running again.</span></span>  
  
 <span data-ttu-id="a9e9d-116">您可以在 Windows Forms 中建立類別庫，此類別庫具有顯示表單的方法，然後再建置用於 COM Interop 的類別庫。</span><span class="sxs-lookup"><span data-stu-id="a9e9d-116">You can create a class library in Windows Forms which has a method to show the form, and then build the class library for COM interop.</span></span> <span data-ttu-id="a9e9d-117">您可以在 Visual Basic 6.0 或 Microsoft Foundation Class (MFC) 中使用這個 DLL 檔，並在這些環境中呼叫 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> 方法以顯示表單。</span><span class="sxs-lookup"><span data-stu-id="a9e9d-117">You can use this DLL file from Visual Basic 6.0 or Microsoft Foundation Classes (MFC), and from either of these environments you can call the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the form.</span></span>  
  
#### <a name="to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a><span data-ttu-id="a9e9d-118">若要使用 ShowDialog 方法來顯示 Windows 表單以支援 COM Interop</span><span class="sxs-lookup"><span data-stu-id="a9e9d-118">To support COM interop by displaying a windows form with the ShowDialog method</span></span>  
  
-   <span data-ttu-id="a9e9d-119">在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 元件中，將所有對 <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> 方法的呼叫取代為對 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a9e9d-119">Replace all calls to the <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> method with calls to the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method in your [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9e9d-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="a9e9d-120">See Also</span></span>  
 [<span data-ttu-id="a9e9d-121">將 .NET Framework 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="a9e9d-121">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="a9e9d-122">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span><span class="sxs-lookup"><span data-stu-id="a9e9d-122">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 [<span data-ttu-id="a9e9d-123">Windows Forms 和 Unmanaged 應用程式</span><span class="sxs-lookup"><span data-stu-id="a9e9d-123">Windows Forms and Unmanaged Applications</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)
