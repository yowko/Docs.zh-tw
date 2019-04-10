---
title: HOW TO：使用 ToolStripControlHost 包裝 Windows Forms 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStrip control [Windows Forms], wrapping controls
- toolbars [Windows Forms], wrapping controls
- ToolStrip control [Windows Forms], hosting controls
ms.assetid: e2ce4990-661d-4882-a116-8a9eb575dc84
ms.openlocfilehash: ccf82b2ea767d69797af1ffa38381a7cc0fd3b67
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307999"
---
# <a name="how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost"></a><span data-ttu-id="3eadc-102">HOW TO：使用 ToolStripControlHost 包裝 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="3eadc-102">How to: Wrap a Windows Forms Control with ToolStripControlHost</span></span>
<xref:System.Windows.Forms.ToolStripControlHost> <span data-ttu-id="3eadc-103">設計來啟用任意 Windows Form 控制項的裝載使用<xref:System.Windows.Forms.ToolStripControlHost>建構函式或擴充<xref:System.Windows.Forms.ToolStripControlHost>本身。</span><span class="sxs-lookup"><span data-stu-id="3eadc-103">is designed to enable hosting of arbitrary Windows Forms controls by using the <xref:System.Windows.Forms.ToolStripControlHost> constructor or by extending <xref:System.Windows.Forms.ToolStripControlHost> itself.</span></span> <span data-ttu-id="3eadc-104">藉由擴充 <xref:System.Windows.Forms.ToolStripControlHost> 及實作屬性和方法 (這些會公開控制項經常使用的屬性和方法)，包裝控制項變得更容易。</span><span class="sxs-lookup"><span data-stu-id="3eadc-104">It is easier to wrap the control by extending <xref:System.Windows.Forms.ToolStripControlHost> and implementing properties and methods that expose frequently used properties and methods of the control.</span></span> <span data-ttu-id="3eadc-105">您也可以公開在 <xref:System.Windows.Forms.ToolStripControlHost> 層級的控制項事件。</span><span class="sxs-lookup"><span data-stu-id="3eadc-105">You can also expose events for the control at the <xref:System.Windows.Forms.ToolStripControlHost> level.</span></span>  
  
### <a name="to-host-a-control-in-a-toolstripcontrolhost-by-derivation"></a><span data-ttu-id="3eadc-106">由衍生在 ToolStripControlHost 中裝載控制項</span><span class="sxs-lookup"><span data-stu-id="3eadc-106">To host a control in a ToolStripControlHost by derivation</span></span>  
  
1. <span data-ttu-id="3eadc-107">擴充 <xref:System.Windows.Forms.ToolStripControlHost>。</span><span class="sxs-lookup"><span data-stu-id="3eadc-107">Extend <xref:System.Windows.Forms.ToolStripControlHost>.</span></span> <span data-ttu-id="3eadc-108">實作預設建構函式，它會呼叫在所需控制項中傳遞的基底類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="3eadc-108">Implement a default constructor that calls the base class constructor passing in the desired control.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#10)]  
  
2. <span data-ttu-id="3eadc-109">宣告相同類型的屬性做為包裝的控制項，並傳回 `Control` 做為屬性存取子中控制項的正確類型。</span><span class="sxs-lookup"><span data-stu-id="3eadc-109">Declare a property of the same type as the wrapped control and return `Control` as the correct type of control in the property's accessor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#11)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#11)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#11)]  
  
3. <span data-ttu-id="3eadc-110">藉由擴充類別中的屬性和方法，公開其他常用之已包裝控制項的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="3eadc-110">Expose other frequently used properties and methods of the wrapped control with properties and methods in the extended class.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#12)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#12)]  
  
4. <span data-ttu-id="3eadc-111">覆寫 <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A> 和 <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> 方法 (此為選擇性)，並加入您想要公開的控制項事件。</span><span class="sxs-lookup"><span data-stu-id="3eadc-111">Optionally, override the <xref:System.Windows.Forms.ToolStripControlHost.OnSubscribeControlEvents%2A>, and <xref:System.Windows.Forms.ToolStripControlHost.OnUnsubscribeControlEvents%2A> methods and add the control events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#16)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#16)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#16)]  
  
5. <span data-ttu-id="3eadc-112">提供您想要公開的事件之必要的包裝。</span><span class="sxs-lookup"><span data-stu-id="3eadc-112">Provide the necessary wrapping for the events you want to expose.</span></span>  
  
     [!code-cpp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#17)]
     [!code-csharp[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#17)]
     [!code-vb[System.Windows.Forms.ToolStripControlHost#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="3eadc-113">範例</span><span class="sxs-lookup"><span data-stu-id="3eadc-113">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CPP/form1.cpp#13)]
 [!code-csharp[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/CS/form1.cs#13)]
 [!code-vb[System.Windows.Forms.ToolStripControlHost#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripControlHost/VB/form1.vb#13)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3eadc-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="3eadc-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="3eadc-115">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="3eadc-115">This example requires:</span></span>  
  
-   <span data-ttu-id="3eadc-116">System 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="3eadc-116">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="3eadc-117">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="3eadc-117">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="3eadc-118">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="3eadc-118">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eadc-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3eadc-119">See also</span></span>

- <xref:System.Windows.Forms.ToolStripControlHost>
- [<span data-ttu-id="3eadc-120">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="3eadc-120">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="3eadc-121">ToolStrip 控制項架構</span><span class="sxs-lookup"><span data-stu-id="3eadc-121">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="3eadc-122">ToolStrip 技術摘要</span><span class="sxs-lookup"><span data-stu-id="3eadc-122">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
