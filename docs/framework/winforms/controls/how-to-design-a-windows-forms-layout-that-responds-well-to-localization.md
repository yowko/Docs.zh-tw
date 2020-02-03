---
title: 設計容易當地語系化的版面配置
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
ms.openlocfilehash: 36ffd532b9f539107307144d25c8d9d5f8ba634a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743290"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="1c27c-102">如何：設計可適當回應當地語系化的 Windows Form 配置</span><span class="sxs-lookup"><span data-stu-id="1c27c-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="1c27c-103">建立準備好當地語系化的表單，將會大幅加速開發國際市場。</span><span class="sxs-lookup"><span data-stu-id="1c27c-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="1c27c-104">您可以使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來實作版面配置，當控制項因 <xref:System.Windows.Forms.Control.Text%2A> 屬性值變更而調整大小時，它會依正常程序回應。</span><span class="sxs-lookup"><span data-stu-id="1c27c-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c27c-105">範例</span><span class="sxs-lookup"><span data-stu-id="1c27c-105">Example</span></span>  
 <span data-ttu-id="1c27c-106">在您翻譯顯示字串值為其他語言時，此表單會示範如何建立可按比例調整的版面配置。</span><span class="sxs-lookup"><span data-stu-id="1c27c-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="1c27c-107">這個翻譯的過程稱為「當地語系化」(localization)。</span><span class="sxs-lookup"><span data-stu-id="1c27c-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="1c27c-108">如需詳細資訊，請參閱[當地語系化](../../../standard/globalization-localization/localization.md)。</span><span class="sxs-lookup"><span data-stu-id="1c27c-108">For more information, see [Localization](../../../standard/globalization-localization/localization.md).</span></span>  
  
 <span data-ttu-id="1c27c-109">在 Visual Studio 中對於本工作有更詳盡的支援。</span><span class="sxs-lookup"><span data-stu-id="1c27c-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="1c27c-110">另請參閱[逐步解說：建立可調整比例以配合當地語系化的配置](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="1c27c-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a><span data-ttu-id="1c27c-111">其他資源</span><span class="sxs-lookup"><span data-stu-id="1c27c-111">Additional resources</span></span>

1. [<span data-ttu-id="1c27c-112">操作說明：在 TableLayoutPanel 控制項中對齊和縮放控制項</span><span class="sxs-lookup"><span data-stu-id="1c27c-112">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [<span data-ttu-id="1c27c-113">逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項</span><span class="sxs-lookup"><span data-stu-id="1c27c-113">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3. [<span data-ttu-id="1c27c-114">操作說明：擴展 TableLayoutPanel 控制項中的資料列和資料行</span><span class="sxs-lookup"><span data-stu-id="1c27c-114">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4. [<span data-ttu-id="1c27c-115">操作說明：編輯 TableLayoutPanel 控制項中的資料行和資料列</span><span class="sxs-lookup"><span data-stu-id="1c27c-115">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5. [<span data-ttu-id="1c27c-116">逐步解說：使用 Windows Forms 控制項中的智慧標籤執行一般工作</span><span class="sxs-lookup"><span data-stu-id="1c27c-116">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6. [<span data-ttu-id="1c27c-117">逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="1c27c-117">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7. [<span data-ttu-id="1c27c-118">逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="1c27c-118">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)  
  
8. <span data-ttu-id="1c27c-119">[如何‎：使用 AutoSize 和 TableLayoutPanel 控制項支援 Windows Forms 的當地語系化](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1c27c-119">[How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span></span>  
  
9. <span data-ttu-id="1c27c-120">[逐步解說：建立適用於資料輸入且可調整大小的 Windows Form](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1c27c-120">[Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1c27c-121">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1c27c-121">Compiling the Code</span></span>  
 <span data-ttu-id="1c27c-122">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="1c27c-122">This example requires:</span></span>  
  
- <span data-ttu-id="1c27c-123">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="1c27c-123">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c27c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c27c-124">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="1c27c-125">當地語系化</span><span class="sxs-lookup"><span data-stu-id="1c27c-125">Localization</span></span>](../../../standard/globalization-localization/localization.md)
