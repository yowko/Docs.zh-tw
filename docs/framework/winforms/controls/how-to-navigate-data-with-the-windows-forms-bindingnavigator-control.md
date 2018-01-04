---
title: "如何：使用 Windows Form BindingNavigator 控制項巡覽資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c5b49d84f98213e95c83c5476007297149adc16
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="729c5-102">如何：使用 Windows Form BindingNavigator 控制項巡覽資料</span><span class="sxs-lookup"><span data-stu-id="729c5-102">How to: Navigate Data with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="729c5-103">在 Windows Form 中 <xref:System.Windows.Forms.BindingNavigator> 控制項的問世，可讓開發人員在他們建立的表單上提供使用者簡單資料巡覽和管理使用者介面。</span><span class="sxs-lookup"><span data-stu-id="729c5-103">The advent of the <xref:System.Windows.Forms.BindingNavigator> control in Windows Forms enables developers to provide end users with a simple data navigation and manipulation user interface on the forms they create.</span></span>  
  
 <span data-ttu-id="729c5-104"><xref:System.Windows.Forms.BindingNavigator> 控制項是一種 <xref:System.Windows.Forms.ToolStrip> 控制項，具有預先設定的按鈕，用來巡覽資料集中的第一筆、最後一筆、下一筆和上一筆記錄，以及新增和刪除記錄。</span><span class="sxs-lookup"><span data-stu-id="729c5-104">The <xref:System.Windows.Forms.BindingNavigator> control is a <xref:System.Windows.Forms.ToolStrip> control with buttons preconfigured for navigation to the first, last, next, and previous record in a data set, as well as buttons to add and delete records.</span></span> <span data-ttu-id="729c5-105">新增按鈕到 <xref:System.Windows.Forms.BindingNavigator> 控制項很容易，因為它是 <xref:System.Windows.Forms.ToolStrip> 控制項。</span><span class="sxs-lookup"><span data-stu-id="729c5-105">Adding buttons to the <xref:System.Windows.Forms.BindingNavigator> control is easy, because it is a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  <span data-ttu-id="729c5-106">另請參閱[如何：將載入、儲存和取消按鈕新增至 Windows Forms BindingNavigator 控制項](http://msdn.microsoft.com/library/safa4957\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="729c5-106">Also see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).</span></span>  
  
 <span data-ttu-id="729c5-107">對於每個 <xref:System.Windows.Forms.BindingNavigator> 控制項上的按鈕，並沒有對應於可以程式設計的方式進行相同功能的 <xref:System.Windows.Forms.BindingSource> 元件成員。</span><span class="sxs-lookup"><span data-stu-id="729c5-107">For each button on the <xref:System.Windows.Forms.BindingNavigator> control, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically allows the same functionality.</span></span> <span data-ttu-id="729c5-108">例如，<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> 按鈕對應至 <xref:System.Windows.Forms.BindingSource> 元件的 <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> 方法，<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> 按鈕對應至 <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> 方法等。</span><span class="sxs-lookup"><span data-stu-id="729c5-108">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span> <span data-ttu-id="729c5-109">因此，啟用 <xref:System.Windows.Forms.BindingNavigator> 控制項來巡覽資料記錄相當簡單，如同在表單上設定其 <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> 屬性為適當的 <xref:System.Windows.Forms.BindingSource> 元件。</span><span class="sxs-lookup"><span data-stu-id="729c5-109">As a result, enabling the <xref:System.Windows.Forms.BindingNavigator> control to navigate data records is a simple as setting its <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the appropriate <xref:System.Windows.Forms.BindingSource> component on the form.</span></span>  
  
### <a name="to-set-up-the-bindingnavigator-control"></a><span data-ttu-id="729c5-110">若要設定 BindingNavigator 控制項</span><span class="sxs-lookup"><span data-stu-id="729c5-110">To set up the BindingNavigator control</span></span>  
  
1.  <span data-ttu-id="729c5-111">新增命名為 `bindingSource1` 的 <xref:System.Windows.Forms.BindingSource> 元件和名為 `textBox1` 和 `textBox2` 的兩個 <xref:System.Windows.Forms.TextBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="729c5-111">Add a <xref:System.Windows.Forms.BindingSource> component named `bindingSource1` and two <xref:System.Windows.Forms.TextBox> controls named `textBox1` and `textBox2`.</span></span>  
  
2.  <span data-ttu-id="729c5-112">將 `bindingSource1` 繫結至資料，並將文字方塊控制項繫結至 `bindingSource1`。</span><span class="sxs-lookup"><span data-stu-id="729c5-112">Bind `bindingSource1` to data, and the textbox controls to `bindingSource1`.</span></span> <span data-ttu-id="729c5-113">若要執行此工作，請將下列程式碼貼到您的表單並從表單的建構函式或 <xref:System.Windows.Forms.Form.Load> 事件處理方法呼叫 `LoadData`。</span><span class="sxs-lookup"><span data-stu-id="729c5-113">To do this, paste the following code into your form and call `LoadData` from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="729c5-114">新增名為 `bindingNavigator1` 的 <xref:System.Windows.Forms.BindingNavigator> 控制項至您的表單。</span><span class="sxs-lookup"><span data-stu-id="729c5-114">Add a <xref:System.Windows.Forms.BindingNavigator> control named `bindingNavigator1` to your form.</span></span>  
  
4.  <span data-ttu-id="729c5-115">將 `bindingNavigator1` 的 <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> 屬性設定為 `bindingSource1`。</span><span class="sxs-lookup"><span data-stu-id="729c5-115">Set the <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property for `bindingNavigator1` to `bindingSource1`.</span></span> <span data-ttu-id="729c5-116">您可以用設計工具或在程式碼中執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="729c5-116">You can do this with the designer or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="729c5-117">範例</span><span class="sxs-lookup"><span data-stu-id="729c5-117">Example</span></span>  
 <span data-ttu-id="729c5-118">下列程式碼範例是先前所列步驟的完整範例。</span><span class="sxs-lookup"><span data-stu-id="729c5-118">The following code example is the complete example for the steps listed previously.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="729c5-119">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="729c5-119">Compiling the Code</span></span>  
 <span data-ttu-id="729c5-120">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="729c5-120">This example requires:</span></span>  
  
-   <span data-ttu-id="729c5-121">System、System.Data、System.Drawing、System.Windows.Forms 和 System.Xml 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="729c5-121">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="729c5-122">如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置命令列](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="729c5-122">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="729c5-123">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="729c5-123">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="729c5-124">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="729c5-124">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="729c5-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="729c5-125">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [<span data-ttu-id="729c5-126">BindingNavigator 控制項</span><span class="sxs-lookup"><span data-stu-id="729c5-126">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [<span data-ttu-id="729c5-127">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="729c5-127">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
