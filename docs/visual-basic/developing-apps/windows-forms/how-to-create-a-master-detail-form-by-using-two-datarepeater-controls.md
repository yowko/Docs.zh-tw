---
title: "如何︰ 使用兩個 DataRepeater 控制項 (Visual Studio) 建立主從式表單 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 4ed0b1fa0e7fac96cef3bde61efac66681f2507b
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a><span data-ttu-id="8c607-102">如何：使用兩個 DataRepeater 控制項建立主從式表單 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="8c607-102">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>
<span data-ttu-id="8c607-103">您可以使用兩個或多個顯示相關的資料<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項建立主從式表單。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="8c607-103">You can display related data by using two or more <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls to create a master/detail form.</span></span> <span data-ttu-id="8c607-104">比方說，您可能想要顯示一份客戶清單中其中一個<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>，以及當使用者選取客戶時，顯示該客戶的訂單清單中第二個<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="8c607-104">For example, you might want to display a list of customers in one <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, and when the user selects a customer, display a list of that customer's orders in a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
 <span data-ttu-id="8c607-105">您可以顯示相關的資料的詳細資料的項目共用相同的主要資料表節點，從**資料來源**視窗拖曳至<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="8c607-105">You can display related data by dragging detail items that share the same master table node from the **Data Sources** window onto a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="8c607-106">比方說，如果您有有客戶資料表和相關的 Orders 資料表的資料來源，您看到這兩個資料表中的樹狀檢視中的最上層節點**資料來源**視窗。</span><span class="sxs-lookup"><span data-stu-id="8c607-106">For example, if you have a data source that has a Customers table and a related Orders table, you see both tables as top-level nodes in the tree view in the **Data Sources** window.</span></span> <span data-ttu-id="8c607-107">展開 [客戶] 節點，您可以看到資料行。</span><span class="sxs-lookup"><span data-stu-id="8c607-107">Expand the Customers node so that you can see the columns.</span></span> <span data-ttu-id="8c607-108">請注意，在清單中的最後一欄可展開的節點，表示 「 訂單 」 資料表。</span><span class="sxs-lookup"><span data-stu-id="8c607-108">Notice that the last column in the list is an expandable node that represents the Orders table.</span></span> <span data-ttu-id="8c607-109">此節點代表客戶的相關的訂單。</span><span class="sxs-lookup"><span data-stu-id="8c607-109">This node represents the related orders for a customer.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a><span data-ttu-id="8c607-110">若要在兩個 DataRepeater 控制項中顯示相關的資料</span><span class="sxs-lookup"><span data-stu-id="8c607-110">To display related data in two DataRepeater controls</span></span>  
  
1.  <span data-ttu-id="8c607-111">拖放兩<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項從**Visual Basic PowerPacks**索引標籤中**工具箱**到表單或容器控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="8c607-111">Drag two <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="8c607-112">拖曳調整大小和位置控點，控制項的大小和位置的並行。</span><span class="sxs-lookup"><span data-stu-id="8c607-112">Drag the sizing and position handles to size the controls and position them side-by-side.</span></span>  
  
3.  <span data-ttu-id="8c607-113">按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。</span><span class="sxs-lookup"><span data-stu-id="8c607-113">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8c607-114">如果**資料來源**視窗是空的加入資料來源。</span><span class="sxs-lookup"><span data-stu-id="8c607-114">If the **Data Sources** window is empty, add a data source to it.</span></span> <span data-ttu-id="8c607-115">如需詳細資訊，請參閱[加入新的資料來源](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources)。</span><span class="sxs-lookup"><span data-stu-id="8c607-115">For more information, see [Add new data sources](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
4.  <span data-ttu-id="8c607-116">在**資料來源** 視窗中，選取主要資料表中的最上層節點。</span><span class="sxs-lookup"><span data-stu-id="8c607-116">In the **Data Sources** window, select the top-level node for the master table.</span></span>  
  
5.  <span data-ttu-id="8c607-117">卸除類型變更主要資料表的詳細資訊，即可**詳細資料**資料表節點的下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="8c607-117">Change the drop type of the master table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="8c607-118">在主要資料表節點拖曳至第一個項目樣板區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="8c607-118">Drag the master table node onto the item template region of the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
7.  <span data-ttu-id="8c607-119">展開 [主資料表] 節點，然後選取相關資料表的詳細資料節點。</span><span class="sxs-lookup"><span data-stu-id="8c607-119">Expand the master table node and select the detail node for the related table.</span></span>  
  
8.  <span data-ttu-id="8c607-120">將詳細資料表的卸除類型變更為詳細資料，依序按一下**詳細資料**資料表節點的下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="8c607-120">Change the drop type of the detail table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
9. <span data-ttu-id="8c607-121">選取這個資料表節點，並將它拖曳到第二個項目樣板區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="8c607-121">Select this table node and drag it onto the item template region of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c607-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c607-122">See Also</span></span>  
 <span data-ttu-id="8c607-123"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="8c607-123"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span></span>   
<span data-ttu-id="8c607-124"> [DataRepeater 控制項簡介](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="8c607-124"> [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="8c607-125"> [如何︰ 在 DataRepeater 控制項中顯示繫結的資料](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="8c607-125"> [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="8c607-126"> [如何︰ 顯示相關的資料在 Windows Form 應用程式](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd) </span><span class="sxs-lookup"><span data-stu-id="8c607-126"> [How to: Display Related Data in a Windows Forms Application](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd) </span></span>  
<span data-ttu-id="8c607-127"> [如何︰ 變更 DataRepeater 控制項的外觀](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="8c607-127"> [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="8c607-128"> [ DataRepeater 控制項進行疑難排解](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="8c607-128"> [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span></span>
