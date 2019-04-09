---
title: HOW TO：設計可適當回應當地語系化的 Windows Forms 配置
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
ms.openlocfilehash: 095427ce633ee6db5a448c8f3f69304ed25ab82a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142593"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="0ca25-102">HOW TO：設計可適當回應當地語系化的 Windows Forms 配置</span><span class="sxs-lookup"><span data-stu-id="0ca25-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="0ca25-103">建立準備好當地語系化的表單，將會大幅加速開發國際市場。</span><span class="sxs-lookup"><span data-stu-id="0ca25-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="0ca25-104">您可以使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來實作版面配置，當控制項因 <xref:System.Windows.Forms.Control.Text%2A> 屬性值變更而調整大小時，它會依正常程序回應。</span><span class="sxs-lookup"><span data-stu-id="0ca25-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ca25-105">範例</span><span class="sxs-lookup"><span data-stu-id="0ca25-105">Example</span></span>  
 <span data-ttu-id="0ca25-106">在您翻譯顯示字串值為其他語言時，此表單會示範如何建立可按比例調整的版面配置。</span><span class="sxs-lookup"><span data-stu-id="0ca25-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="0ca25-107">這個翻譯的過程稱為「當地語系化」(localization)。</span><span class="sxs-lookup"><span data-stu-id="0ca25-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="0ca25-108">如需詳細資訊，請參閱[當地語系化](../../../standard/globalization-localization/localization.md)。</span><span class="sxs-lookup"><span data-stu-id="0ca25-108">For more information, see [Localization](../../../standard/globalization-localization/localization.md).</span></span>  
  
 <span data-ttu-id="0ca25-109">在 Visual Studio 中對於本工作有更詳盡的支援。</span><span class="sxs-lookup"><span data-stu-id="0ca25-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="0ca25-110">另請參閱[逐步解說：建立版面配置調整比例以配合當地語系化](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="0ca25-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a><span data-ttu-id="0ca25-111">其他資源</span><span class="sxs-lookup"><span data-stu-id="0ca25-111">Additional resources</span></span>
1.  [<span data-ttu-id="0ca25-112">HOW TO：在 TableLayoutPanel 控制項中對齊和縮放控制項</span><span class="sxs-lookup"><span data-stu-id="0ca25-112">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [<span data-ttu-id="0ca25-113">逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項</span><span class="sxs-lookup"><span data-stu-id="0ca25-113">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3.  [<span data-ttu-id="0ca25-114">HOW TO：擴展 TableLayoutPanel 控制項中的資料列和資料行</span><span class="sxs-lookup"><span data-stu-id="0ca25-114">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4.  [<span data-ttu-id="0ca25-115">HOW TO：編輯 TableLayoutPanel 控制項中的資料行和資料列</span><span class="sxs-lookup"><span data-stu-id="0ca25-115">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5.  [<span data-ttu-id="0ca25-116">逐步解說：使用 Windows Forms 控制項的智慧標籤執行一般工作</span><span class="sxs-lookup"><span data-stu-id="0ca25-116">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6.  [<span data-ttu-id="0ca25-117">逐步解說：使用 TableLayoutPanel 排列 Windows Forms 的控制項</span><span class="sxs-lookup"><span data-stu-id="0ca25-117">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7.  [<span data-ttu-id="0ca25-118">逐步解說：使用邊框間距、邊界和自動調整屬性配置 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="0ca25-118">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)  
  
8.  [<span data-ttu-id="0ca25-119">HOW TO：支援使用 AutoSize 和 TableLayoutPanel 控制項的 Windows Form 的當地語系化</span><span class="sxs-lookup"><span data-stu-id="0ca25-119">How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))  
  
9. [<span data-ttu-id="0ca25-120">逐步解說：建立適用於資料輸入且可調整大小的 Windows Form</span><span class="sxs-lookup"><span data-stu-id="0ca25-120">Walkthrough: Creating a Resizable Windows Form for Data Entry</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0ca25-121">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0ca25-121">Compiling the Code</span></span>  
 <span data-ttu-id="0ca25-122">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="0ca25-122">This example requires:</span></span>  
  
-   <span data-ttu-id="0ca25-123">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="0ca25-123">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0ca25-124">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="0ca25-124">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0ca25-125">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="0ca25-125">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ca25-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ca25-126">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="0ca25-127">當地語系化</span><span class="sxs-lookup"><span data-stu-id="0ca25-127">Localization</span></span>](../../../standard/globalization-localization/localization.md)
