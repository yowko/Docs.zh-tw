---
title: HOW TO：DataRepeater 控制項 (Visual Studio) 中顯示未繫結的控制項
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
ms.openlocfilehash: a20e1ba83d1963bc3d4c135817767ee02fcbdeda
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730785"
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="8a02a-102">HOW TO：DataRepeater 控制項 (Visual Studio) 中顯示未繫結的控制項</span><span class="sxs-lookup"><span data-stu-id="8a02a-102">How to: Display Unbound Controls in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="8a02a-103">除了繫結的控制項，您可能想要新增其他控制項來<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>，例如靜態標籤或映像中的每個項目上重複<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</span><span class="sxs-lookup"><span data-stu-id="8a02a-103">In addition to bound controls, you may want to add other controls to a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, such as a static label or an image that is repeated on each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a02a-104">您也必須擁有至少一個繫結的控制項<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>或將不會顯示在執行階段。</span><span class="sxs-lookup"><span data-stu-id="8a02a-104">You must also have at least one bound control on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> or nothing will be displayed at run time.</span></span>  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a><span data-ttu-id="8a02a-105">未繫結的控制項加入 DataRepeater</span><span class="sxs-lookup"><span data-stu-id="8a02a-105">To add unbound controls to a DataRepeater</span></span>  
  
1.  <span data-ttu-id="8a02a-106">拖曳<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項從**Visual Basic PowerPacks**索引標籤**工具箱**到表單或容器控制項。</span><span class="sxs-lookup"><span data-stu-id="8a02a-106">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="8a02a-107">拖曳調整大小和位置的控點大小和控制項的位置。</span><span class="sxs-lookup"><span data-stu-id="8a02a-107">Drag the sizing and position handles to size and position the control.</span></span>  
  
     <span data-ttu-id="8a02a-108">您可以調整大小，並藉由變更控制項的位置**大小**並**位置**屬性 視窗中的屬性。</span><span class="sxs-lookup"><span data-stu-id="8a02a-108">You can also size and position the control by changing the **Size** and **Position** properties in the Properties window.</span></span>  
  
3.  <span data-ttu-id="8a02a-109">將至少一個資料繫結控制項加入<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</span><span class="sxs-lookup"><span data-stu-id="8a02a-109">Add at least one data-bound control to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="8a02a-110">如需詳細資訊，請參閱[＜How to：DataRepeater 控制項中顯示繫結的資料](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="8a02a-110">For more information, see [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).</span></span>  
  
4.  <span data-ttu-id="8a02a-111">將控制項從**工具箱**上的項目範本區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</span><span class="sxs-lookup"><span data-stu-id="8a02a-111">Drag a control from the **Toolbox** onto the item template region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="8a02a-112">請注意，此控制項有兩個矩形區域。</span><span class="sxs-lookup"><span data-stu-id="8a02a-112">Note that the control has two rectangular regions.</span></span> <span data-ttu-id="8a02a-113">內部的區域*項目範本*; 將重複控制項新增至範本中的每個項目中<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項在執行階段。</span><span class="sxs-lookup"><span data-stu-id="8a02a-113">The inner region is the *item template*; controls added to the template will be repeated in each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at run time.</span></span> <span data-ttu-id="8a02a-114">外部的區域*viewport*，其中會顯示的項目; 會加入到此區域中的控制項將不會顯示在執行階段。</span><span class="sxs-lookup"><span data-stu-id="8a02a-114">The outer region is the *viewport*, where the items will be displayed; controls that are added to this region will not be displayed at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a02a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a02a-115">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [<span data-ttu-id="8a02a-116">DataRepeater 控制項簡介</span><span class="sxs-lookup"><span data-stu-id="8a02a-116">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="8a02a-117"> DataRepeater 控制項進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="8a02a-117">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="8a02a-118">如何：DataRepeater 控制項中顯示繫結的資料</span><span class="sxs-lookup"><span data-stu-id="8a02a-118">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="8a02a-119">如何：使用兩個 DataRepeater 控制項 (Visual Studio) 來建立主從式表單</span><span class="sxs-lookup"><span data-stu-id="8a02a-119">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
- [<span data-ttu-id="8a02a-120">如何：變更 DataRepeater 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="8a02a-120">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
