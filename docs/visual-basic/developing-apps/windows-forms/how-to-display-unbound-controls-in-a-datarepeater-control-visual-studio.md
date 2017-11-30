---
title: "如何：在 DataRepeater 控制項中顯示未繫結的控制項 (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3e96219f0ea8b8198967e9fa3c6e5afb824352db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="0a9b7-102">如何：在 DataRepeater 控制項中顯示未繫結的控制項 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="0a9b7-102">How to: Display Unbound Controls in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="0a9b7-103">除了繫結控制項，您可能想要將其他控制項加入<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>，例如靜態標籤或映像中的每個項目上的重複<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</span><span class="sxs-lookup"><span data-stu-id="0a9b7-103">In addition to bound controls, you may want to add other controls to a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, such as a static label or an image that is repeated on each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a9b7-104">您也必須擁有至少一個繫結的控制項<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>或執行任何動作將會顯示在執行階段。</span><span class="sxs-lookup"><span data-stu-id="0a9b7-104">You must also have at least one bound control on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> or nothing will be displayed at run time.</span></span>  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a><span data-ttu-id="0a9b7-105">若要將未繫結的控制項加入 DataRepeater</span><span class="sxs-lookup"><span data-stu-id="0a9b7-105">To add unbound controls to a DataRepeater</span></span>  
  
1.  <span data-ttu-id="0a9b7-106">拖曳<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項從**Visual Basic PowerPacks**索引標籤中**工具箱**到表單或容器控制項。</span><span class="sxs-lookup"><span data-stu-id="0a9b7-106">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="0a9b7-107">拖曳調整大小和位置控點大小，並置於控制項。</span><span class="sxs-lookup"><span data-stu-id="0a9b7-107">Drag the sizing and position handles to size and position the control.</span></span>  
  
     <span data-ttu-id="0a9b7-108">您可以調整大小，並藉由變更定位控制項**大小**和**位置**[屬性] 視窗中的屬性。</span><span class="sxs-lookup"><span data-stu-id="0a9b7-108">You can also size and position the control by changing the **Size** and **Position** properties in the Properties window.</span></span>  
  
3.  <span data-ttu-id="0a9b7-109">將至少一個資料繫結控制項加入<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</span><span class="sxs-lookup"><span data-stu-id="0a9b7-109">Add at least one data-bound control to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="0a9b7-110">如需詳細資訊，請參閱[How to： 在 DataRepeater 控制項中顯示繫結資料](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="0a9b7-110">For more information, see [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).</span></span>  
  
4.  <span data-ttu-id="0a9b7-111">將控制項從**工具箱**到的項目範本區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</span><span class="sxs-lookup"><span data-stu-id="0a9b7-111">Drag a control from the **Toolbox** onto the item template region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="0a9b7-112">請注意控制項有兩個矩形區域。</span><span class="sxs-lookup"><span data-stu-id="0a9b7-112">Note that the control has two rectangular regions.</span></span> <span data-ttu-id="0a9b7-113">內部的區域是*項目範本*; 將每個項目中重複加入範本中的控制項<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項在執行階段。</span><span class="sxs-lookup"><span data-stu-id="0a9b7-113">The inner region is the *item template*; controls added to the template will be repeated in each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at run time.</span></span> <span data-ttu-id="0a9b7-114">外部區域是*檢視區*，其中的項目會顯示; 加入到此區域的控制項將不會顯示在執行階段。</span><span class="sxs-lookup"><span data-stu-id="0a9b7-114">The outer region is the *viewport*, where the items will be displayed; controls that are added to this region will not be displayed at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a9b7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a9b7-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="0a9b7-116">DataRepeater 控制項簡介</span><span class="sxs-lookup"><span data-stu-id="0a9b7-116">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="0a9b7-117"> DataRepeater 控制項進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="0a9b7-117">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="0a9b7-118">操作說明：在 DataRepeater 控制項中顯示繫結資料</span><span class="sxs-lookup"><span data-stu-id="0a9b7-118">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="0a9b7-119">如何： 利用兩個 DataRepeater 控制項 (Visual Studio) 來建立主從式表單</span><span class="sxs-lookup"><span data-stu-id="0a9b7-119">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [<span data-ttu-id="0a9b7-120">操作說明：變更 DataRepeater 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="0a9b7-120">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
