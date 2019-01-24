---
title: HOW TO：建立適用於資料輸入且可調整大小的 Windows Form
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
ms.openlocfilehash: a632b243715ee42243c184aa2aca25abb6347f9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733320"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a><span data-ttu-id="acfe1-102">HOW TO：建立適用於資料輸入且可調整大小的 Windows Form</span><span class="sxs-lookup"><span data-stu-id="acfe1-102">How to: Create a Resizable Windows Form for Data Entry</span></span>
<span data-ttu-id="acfe1-103">良好的配置會適當回應在父表單維度中的變更。</span><span class="sxs-lookup"><span data-stu-id="acfe1-103">A good layout responds well to changes in the dimensions of its parent form.</span></span> <span data-ttu-id="acfe1-104">您可以使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來排列表單的配置，以和表單維度變更一致的方式調整控制項大小及置放控制項。</span><span class="sxs-lookup"><span data-stu-id="acfe1-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to arrange the layout of your form to resize and position your controls in a consistent way as the form's dimensions change.</span></span> <span data-ttu-id="acfe1-105">當控制項內容中的變更造成配置變更時，<xref:System.Windows.Forms.TableLayoutPanel> 控制項也很有用。</span><span class="sxs-lookup"><span data-stu-id="acfe1-105">The <xref:System.Windows.Forms.TableLayoutPanel> control is also useful when changes in the contents of your controls cause changes in the layout.</span></span> <span data-ttu-id="acfe1-106">這個程序所涵蓋的流程可在 Visual Studio 環境中完成。</span><span class="sxs-lookup"><span data-stu-id="acfe1-106">The process covered in this procedure can be done within the Visual Studio environment.</span></span>  <span data-ttu-id="acfe1-107">另請參閱[逐步解說：建立適用於資料輸入且可調整大小的 Windows Form](https://msdn.microsoft.com/library/991eahec\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="acfe1-107">Also see [Walkthrough: Creating a Resizable Windows Form for Data Entry](https://msdn.microsoft.com/library/991eahec\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="acfe1-108">範例</span><span class="sxs-lookup"><span data-stu-id="acfe1-108">Example</span></span>  
 <span data-ttu-id="acfe1-109">下列範例示範如何使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來建置在使用者調整表單大小時會適當回應的配置。</span><span class="sxs-lookup"><span data-stu-id="acfe1-109">The following example demonstrates how to use a <xref:System.Windows.Forms.TableLayoutPanel> control to build a layout that responds well when the user resizes the form.</span></span> <span data-ttu-id="acfe1-110">它也會示範可適當回應當地語系化的配置。</span><span class="sxs-lookup"><span data-stu-id="acfe1-110">It also demonstrates a layout that responds well to localization.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="acfe1-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="acfe1-111">Compiling the Code</span></span>  
 <span data-ttu-id="acfe1-112">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="acfe1-112">This example requires:</span></span>  
  
-   <span data-ttu-id="acfe1-113">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="acfe1-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="acfe1-114">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="acfe1-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="acfe1-115">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="acfe1-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="acfe1-116">另請參閱[How to:編譯並執行完整的 Windows Form 程式碼範例使用 Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="acfe1-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acfe1-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acfe1-117">See also</span></span>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="acfe1-118">如何：錨定和停駐 TableLayoutPanel 控制項中的子控制項</span><span class="sxs-lookup"><span data-stu-id="acfe1-118">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="acfe1-119">如何：設計可適當回應當地語系化的 Windows Forms 配置</span><span class="sxs-lookup"><span data-stu-id="acfe1-119">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [<span data-ttu-id="acfe1-120">Microsoft Windows 使用者經驗, 使用者介面開發人員和設計人員的正式方針。Redmond，WA:Microsoft Press，1999年。(USBN:0-7356-0566-1)</span><span class="sxs-lookup"><span data-stu-id="acfe1-120">Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span></span>](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
