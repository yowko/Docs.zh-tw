---
title: HOW TO：DataRepeater 控制項 (Visual Studio) 中顯示繫結的資料
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
ms.openlocfilehash: dbcd814edb78c54ce5629a1a8761142674fe6135
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684615"
---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="2a146-102">HOW TO：DataRepeater 控制項 (Visual Studio) 中顯示繫結的資料</span><span class="sxs-lookup"><span data-stu-id="2a146-102">How to: Display Bound Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="2a146-103">最常見的用法<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項是顯示從資料庫或其他資料來源繫結的資料。</span><span class="sxs-lookup"><span data-stu-id="2a146-103">The most common use of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control is to display bound data from a database or other data source.</span></span>  
  
 <span data-ttu-id="2a146-104">除了繫結的控制項，您可能想要新增其他控制項，例如靜態標籤或影像中每個項目上重複<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</span><span class="sxs-lookup"><span data-stu-id="2a146-104">In addition to bound controls, you may want to add other controls, such as a static label or an image that is repeated on each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="2a146-105">如需詳細資訊，請參閱[＜How to：顯示未繫結的 DataRepeater 控制項中的控制項](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="2a146-105">For more information, see [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).</span></span>  
  
 <span data-ttu-id="2a146-106">您也可以繫結至資料來源在執行階段藉由設定<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>屬性，以`True`並指派資料來源，以便<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="2a146-106">You can also bind to a data source at run time by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> property to `True` and assigning a data source to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> property.</span></span> <span data-ttu-id="2a146-107">在此情況下，您必須管理與資料來源的所有互動。</span><span class="sxs-lookup"><span data-stu-id="2a146-107">In this case, you will need to manage all interaction with the data source.</span></span> <span data-ttu-id="2a146-108">如需詳細資訊，請參閱 < [DataRepeater 控制項中的虛擬模式](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="2a146-108">For more information, see [Virtual Mode in the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a><span data-ttu-id="2a146-109">若要建立資料繫結 DataRepeater</span><span class="sxs-lookup"><span data-stu-id="2a146-109">To create a data-bound DataRepeater</span></span>  
  
1.  <span data-ttu-id="2a146-110">拖曳<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項從**Visual Basic PowerPacks**索引標籤**工具箱**到表單或容器控制項。</span><span class="sxs-lookup"><span data-stu-id="2a146-110">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="2a146-111">拖曳調整大小和位置的控點大小和控制項的位置。</span><span class="sxs-lookup"><span data-stu-id="2a146-111">Drag the sizing and position handles to size and position the control.</span></span>  
  
     <span data-ttu-id="2a146-112">請注意，此控制項有兩個矩形區域。</span><span class="sxs-lookup"><span data-stu-id="2a146-112">Note that the control has two rectangular regions.</span></span> <span data-ttu-id="2a146-113">上方區域是*項目範本*; 將重複控制項新增至範本中的每個項目中<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項在執行階段。</span><span class="sxs-lookup"><span data-stu-id="2a146-113">The upper region is the *item template*; controls added to the template will be repeated in each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at run time.</span></span> <span data-ttu-id="2a146-114">較低的區域*viewport*，會顯示項目。</span><span class="sxs-lookup"><span data-stu-id="2a146-114">The lower region is the *viewport*, where the items will be displayed.</span></span>  
  
     <span data-ttu-id="2a146-115">您可以調整大小，並藉由變更放置控制項或項目範本**大小**並**位置**屬性 視窗中的屬性。</span><span class="sxs-lookup"><span data-stu-id="2a146-115">You can also size and position the control or the item template by changing the **Size** and **Position** properties in the Properties window.</span></span>  
  
3.  <span data-ttu-id="2a146-116">按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。</span><span class="sxs-lookup"><span data-stu-id="2a146-116">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2a146-117">如果**Zdroje dat**視窗是空的加入資料來源。</span><span class="sxs-lookup"><span data-stu-id="2a146-117">If the **Data Sources** window is empty, add a data source to it.</span></span> <span data-ttu-id="2a146-118">如需詳細資訊，請參閱[新增資料來源](/visualstudio/data-tools/add-new-data-sources)。</span><span class="sxs-lookup"><span data-stu-id="2a146-118">For more information, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
4.  <span data-ttu-id="2a146-119">在 [ **Zdroje dat** ] 視窗中，選取包含您想要繫結資料的資料表的最上層節點。</span><span class="sxs-lookup"><span data-stu-id="2a146-119">In the **Data Sources** window, select the top-level node for the table that contains the data that you want to bind.</span></span>  
  
5.  <span data-ttu-id="2a146-120">變更資料表的卸除類型`Details`依序按一下`Details`資料表節點上的下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="2a146-120">Change the drop type of the table to `Details` by clicking `Details` in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="2a146-121">選取 [資料表] 節點，然後將它拖曳至的項目範本區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</span><span class="sxs-lookup"><span data-stu-id="2a146-121">Select the table node and drag it onto the item template region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="2a146-122">您可以指定每個欄位顯示何種控制項。</span><span class="sxs-lookup"><span data-stu-id="2a146-122">You can specify which types of controls are displayed for each field.</span></span> <span data-ttu-id="2a146-123">如需詳細資訊，請參閱 <<c0> [ 設定要從資料來源視窗拖曳時要建立的控制項](/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window)。</span><span class="sxs-lookup"><span data-stu-id="2a146-123">For more information, see [Set the control to be created when dragging from the Data Sources window](/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a146-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a146-124">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [<span data-ttu-id="2a146-125">DataRepeater 控制項簡介</span><span class="sxs-lookup"><span data-stu-id="2a146-125">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="2a146-126">如何：DataRepeater 控制項中顯示未繫結的控制項</span><span class="sxs-lookup"><span data-stu-id="2a146-126">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="2a146-127">如何：使用兩個 DataRepeater 控制項 (Visual Studio) 來建立主從式表單</span><span class="sxs-lookup"><span data-stu-id="2a146-127">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
- [<span data-ttu-id="2a146-128">如何：變更 DataRepeater 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="2a146-128">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="2a146-129"> DataRepeater 控制項進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="2a146-129">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
