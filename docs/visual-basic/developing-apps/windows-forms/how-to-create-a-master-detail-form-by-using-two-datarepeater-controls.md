---
title: "如何： 使用兩個 DataRepeater 控制項 (Visual Studio) 建立主從式表單"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02f98cce74f99d8a00bc916b38e5c290045926a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a><span data-ttu-id="4a948-102">如何：使用兩個 DataRepeater 控制項建立主從式表單 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="4a948-102">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>
<span data-ttu-id="4a948-103">您可以使用兩個或多個顯示相關的資料<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項建立主從式表單。</span><span class="sxs-lookup"><span data-stu-id="4a948-103">You can display related data by using two or more <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls to create a master/detail form.</span></span> <span data-ttu-id="4a948-104">比方說，您可以在其中一個顯示客戶清單<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>，當使用者選取的客戶，顯示該客戶的訂單清單的第二個和<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。</span><span class="sxs-lookup"><span data-stu-id="4a948-104">For example, you might want to display a list of customers in one <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, and when the user selects a customer, display a list of that customer's orders in a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
 <span data-ttu-id="4a948-105">您可以顯示相關的資料的詳細資料的項目共用相同的主資料表節點，從**資料來源**視窗拖曳至<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</span><span class="sxs-lookup"><span data-stu-id="4a948-105">You can display related data by dragging detail items that share the same master table node from the **Data Sources** window onto a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="4a948-106">比方說，如果您有具有 Customers 資料表和相關的 Orders 資料表的資料來源，您看到這兩個資料表中的樹狀檢視中的最上層節點**資料來源**視窗。</span><span class="sxs-lookup"><span data-stu-id="4a948-106">For example, if you have a data source that has a Customers table and a related Orders table, you see both tables as top-level nodes in the tree view in the **Data Sources** window.</span></span> <span data-ttu-id="4a948-107">展開 Customers 節點，您可以看到資料行。</span><span class="sxs-lookup"><span data-stu-id="4a948-107">Expand the Customers node so that you can see the columns.</span></span> <span data-ttu-id="4a948-108">請注意，在清單中的最後一欄可展開的節點代表 「 訂單 」 資料表。</span><span class="sxs-lookup"><span data-stu-id="4a948-108">Notice that the last column in the list is an expandable node that represents the Orders table.</span></span> <span data-ttu-id="4a948-109">此節點代表客戶相關的訂單。</span><span class="sxs-lookup"><span data-stu-id="4a948-109">This node represents the related orders for a customer.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a><span data-ttu-id="4a948-110">若要在兩個 DataRepeater 控制項中顯示相關的資料</span><span class="sxs-lookup"><span data-stu-id="4a948-110">To display related data in two DataRepeater controls</span></span>  
  
1.  <span data-ttu-id="4a948-111">拖放兩<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制從**Visual Basic PowerPacks**索引標籤中**工具箱**到表單或容器控制項。</span><span class="sxs-lookup"><span data-stu-id="4a948-111">Drag two <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controls from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="4a948-112">拖曳調整大小和位置控點，控制項的大小和位置來並行。</span><span class="sxs-lookup"><span data-stu-id="4a948-112">Drag the sizing and position handles to size the controls and position them side-by-side.</span></span>  
  
3.  <span data-ttu-id="4a948-113">按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。</span><span class="sxs-lookup"><span data-stu-id="4a948-113">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a948-114">如果**資料來源**視窗是空的加入資料來源。</span><span class="sxs-lookup"><span data-stu-id="4a948-114">If the **Data Sources** window is empty, add a data source to it.</span></span> <span data-ttu-id="4a948-115">如需詳細資訊，請參閱[新增資料來源](/visualstudio/data-tools/add-new-data-sources)。</span><span class="sxs-lookup"><span data-stu-id="4a948-115">For more information, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
4.  <span data-ttu-id="4a948-116">在**資料來源**視窗中，選取主要資料表中的最上層節點。</span><span class="sxs-lookup"><span data-stu-id="4a948-116">In the **Data Sources** window, select the top-level node for the master table.</span></span>  
  
5.  <span data-ttu-id="4a948-117">主要資料表的卸除類型變更為詳細資料，依序按一下**詳細資料**資料表節點上的下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="4a948-117">Change the drop type of the master table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="4a948-118">主要資料表節點拖曳至第一個項目範本區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</span><span class="sxs-lookup"><span data-stu-id="4a948-118">Drag the master table node onto the item template region of the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
7.  <span data-ttu-id="4a948-119">展開主要資料表節點，然後選取相關資料表的詳細資料節點。</span><span class="sxs-lookup"><span data-stu-id="4a948-119">Expand the master table node and select the detail node for the related table.</span></span>  
  
8.  <span data-ttu-id="4a948-120">詳細資料表的卸除類型變更為詳細資料，依序按一下**詳細資料**資料表節點上的下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="4a948-120">Change the drop type of the detail table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
9. <span data-ttu-id="4a948-121">選取這個資料表節點，然後將它拖曳至第二個項目範本區域<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>控制項。</span><span class="sxs-lookup"><span data-stu-id="4a948-121">Select this table node and drag it onto the item template region of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a948-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a948-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="4a948-123">DataRepeater 控制項簡介</span><span class="sxs-lookup"><span data-stu-id="4a948-123">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="4a948-124">操作說明：在 DataRepeater 控制項中顯示繫結資料</span><span class="sxs-lookup"><span data-stu-id="4a948-124">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="4a948-125">如何：在 Windows Forms 應用程式中顯示相關的資料</span><span class="sxs-lookup"><span data-stu-id="4a948-125">How to: Display Related Data in a Windows Forms Application</span></span>](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)  
 [<span data-ttu-id="4a948-126">操作說明：變更 DataRepeater 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="4a948-126">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="4a948-127"> DataRepeater 控制項進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="4a948-127">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
