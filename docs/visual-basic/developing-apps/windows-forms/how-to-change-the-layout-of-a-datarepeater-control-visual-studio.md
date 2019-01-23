---
title: HOW TO：變更 DataRepeater 控制項 (Visual Studio) 的配置
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, changing layout style
- DataRepeater, changing orientation
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
ms.openlocfilehash: 3389daa6383444b48faab4c5383b281e44349bce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625597"
---
# <a name="how-to-change-the-layout-of-a-datarepeater-control-visual-studio"></a><span data-ttu-id="02baa-102">HOW TO：變更 DataRepeater 控制項 (Visual Studio) 的配置</span><span class="sxs-lookup"><span data-stu-id="02baa-102">How to: Change the Layout of a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="02baa-103"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項可以顯示在 （項目捲動垂直） 的垂直或水平 （項目捲動水平） 的方向。</span><span class="sxs-lookup"><span data-stu-id="02baa-103">The <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control can be displayed in either a vertical (items scroll vertically) or horizontal (items scroll horizontally) orientation.</span></span> <span data-ttu-id="02baa-104">您可以變更方向，在設計階段或執行階段變更<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="02baa-104">You can change the orientation at design time or at run time by changing the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property.</span></span> <span data-ttu-id="02baa-105">如果您變更<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>在執行階段的屬性，您可能也想要調整大小<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>和重新調整子控制項位置。</span><span class="sxs-lookup"><span data-stu-id="02baa-105">If you change the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property at run time, you may also want to resize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> and reposition the child controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02baa-106">如果您重新調整控制項位置上<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>在執行階段，您必須呼叫<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>和<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>開頭和結尾程式碼區塊，重新調整控制項位置的方法。</span><span class="sxs-lookup"><span data-stu-id="02baa-106">If you reposition controls on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> at run time, you will need to call the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> and <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> methods at the beginning and end of the code block that repositions the controls.</span></span>  
  
### <a name="to-change-the-layout-at-design-time"></a><span data-ttu-id="02baa-107">若要在設計階段變更版面配置</span><span class="sxs-lookup"><span data-stu-id="02baa-107">To change the layout at design time</span></span>  
  
1.  <span data-ttu-id="02baa-108">在 Windows Form 設計工具中，選取 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</span><span class="sxs-lookup"><span data-stu-id="02baa-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="02baa-109">您必須選擇其外部框線<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項中下方區域的控制項，不會在右上角按一下<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>區域。</span><span class="sxs-lookup"><span data-stu-id="02baa-109">You must select the outer border of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control by clicking in the lower region of the control, not in the upper <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> region.</span></span>  
  
2.  <span data-ttu-id="02baa-110">在 [屬性] 視窗中，設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>屬性設為<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical>或<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>。</span><span class="sxs-lookup"><span data-stu-id="02baa-110">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property to either <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.</span></span>  
  
### <a name="to-change-the-layout-at-run-time"></a><span data-ttu-id="02baa-111">若要在執行階段變更版面配置</span><span class="sxs-lookup"><span data-stu-id="02baa-111">To change the layout at run time</span></span>  
  
1.  <span data-ttu-id="02baa-112">將下列程式碼新增至按鈕或功能表`Click`事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="02baa-112">Add the following code to a button or menu `Click` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  <span data-ttu-id="02baa-113">在大部分情況下，您會想要新增如下所示的範例 > 一節，來調整大小的程式碼<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>和重新排列控制項，以配合新的方向。</span><span class="sxs-lookup"><span data-stu-id="02baa-113">In most cases, you will want to add code similar to that shown in the Example section to resize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> and rearrange controls to fit the new orientation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02baa-114">範例</span><span class="sxs-lookup"><span data-stu-id="02baa-114">Example</span></span>  
 <span data-ttu-id="02baa-115">下列範例示範如何回應<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged>事件處理常式中的事件。</span><span class="sxs-lookup"><span data-stu-id="02baa-115">The following example shows how to respond to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> event in an event handler.</span></span> <span data-ttu-id="02baa-116">此範例中，您需要<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項，名為`DataRepeater1`表單，而且該它<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>包含兩個<xref:System.Windows.Forms.TextBox>控制項，名為`TextBox1`和`TextBox2`。</span><span class="sxs-lookup"><span data-stu-id="02baa-116">This example requires that you have a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control named `DataRepeater1` on a form and that its <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> contain two <xref:System.Windows.Forms.TextBox> controls named `TextBox1` and `TextBox2`.</span></span>  
  
 [!code-csharp[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="02baa-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02baa-117">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>
- [<span data-ttu-id="02baa-118">DataRepeater 控制項簡介</span><span class="sxs-lookup"><span data-stu-id="02baa-118">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="02baa-119"> DataRepeater 控制項進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="02baa-119">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="02baa-120">如何：變更 DataRepeater 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="02baa-120">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
