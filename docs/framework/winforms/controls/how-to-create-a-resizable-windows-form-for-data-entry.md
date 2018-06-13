---
title: 如何：建立適用於資料輸入且可調整大小的 Windows Form
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
ms.openlocfilehash: a7768b3c6be10373e742cbeea0028d1aee0b261d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531787"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a><span data-ttu-id="33729-102">如何：建立適用於資料輸入且可調整大小的 Windows Form</span><span class="sxs-lookup"><span data-stu-id="33729-102">How to: Create a Resizable Windows Form for Data Entry</span></span>
<span data-ttu-id="33729-103">良好的配置會適當回應在父表單維度中的變更。</span><span class="sxs-lookup"><span data-stu-id="33729-103">A good layout responds well to changes in the dimensions of its parent form.</span></span> <span data-ttu-id="33729-104">您可以使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來排列表單的配置，以和表單維度變更一致的方式調整控制項大小及置放控制項。</span><span class="sxs-lookup"><span data-stu-id="33729-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to arrange the layout of your form to resize and position your controls in a consistent way as the form's dimensions change.</span></span> <span data-ttu-id="33729-105">當控制項內容中的變更造成配置變更時，<xref:System.Windows.Forms.TableLayoutPanel> 控制項也很有用。</span><span class="sxs-lookup"><span data-stu-id="33729-105">The <xref:System.Windows.Forms.TableLayoutPanel> control is also useful when changes in the contents of your controls cause changes in the layout.</span></span> <span data-ttu-id="33729-106">這個程序所涵蓋的流程可在 Visual Studio 環境中完成。</span><span class="sxs-lookup"><span data-stu-id="33729-106">The process covered in this procedure can be done within the Visual Studio environment.</span></span>  <span data-ttu-id="33729-107">另請參閱[逐步解說：建立適用於資料輸入且可調整大小的 Windows Form](http://msdn.microsoft.com/library/991eahec\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="33729-107">Also see [Walkthrough: Creating a Resizable Windows Form for Data Entry](http://msdn.microsoft.com/library/991eahec\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="33729-108">範例</span><span class="sxs-lookup"><span data-stu-id="33729-108">Example</span></span>  
 <span data-ttu-id="33729-109">下列範例示範如何使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來建置在使用者調整表單大小時會適當回應的配置。</span><span class="sxs-lookup"><span data-stu-id="33729-109">The following example demonstrates how to use a <xref:System.Windows.Forms.TableLayoutPanel> control to build a layout that responds well when the user resizes the form.</span></span> <span data-ttu-id="33729-110">它也會示範可適當回應當地語系化的配置。</span><span class="sxs-lookup"><span data-stu-id="33729-110">It also demonstrates a layout that responds well to localization.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="33729-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="33729-111">Compiling the Code</span></span>  
 <span data-ttu-id="33729-112">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="33729-112">This example requires:</span></span>  
  
-   <span data-ttu-id="33729-113">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="33729-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="33729-114">Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="33729-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="33729-115">您也可以將程式碼貼入新的專案，以建置 Visual Studio 中的這個範例。</span><span class="sxs-lookup"><span data-stu-id="33729-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="33729-116">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="33729-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33729-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33729-117">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="33729-118">操作說明：錨定和停駐 TableLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="33729-118">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="33729-119">操作說明：設計可適當回應當地語系化的 Windows Forms 配置</span><span class="sxs-lookup"><span data-stu-id="33729-119">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [<span data-ttu-id="33729-120">Microsoft Windows 使用者經驗, 使用者介面開發人員和設計人員的正式方針。Redmond, WA: Microsoft Press, 1999.(USBN: 0-7356-0566-1)</span><span class="sxs-lookup"><span data-stu-id="33729-120">Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span></span>](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)
