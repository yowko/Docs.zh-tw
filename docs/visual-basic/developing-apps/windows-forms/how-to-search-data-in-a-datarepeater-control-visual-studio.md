---
title: "如何：搜尋 DataRepeater 控制項中的資料 (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a3ed7138c142a83584ecd19ccaebe0e31e421ce3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="d956d-102">如何：搜尋 DataRepeater 控制項中的資料 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="d956d-102">How to: Search Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="d956d-103">當您使用<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>包含許多記錄，您可能想要讓的使用者搜尋的特定記錄的控制項。</span><span class="sxs-lookup"><span data-stu-id="d956d-103">When you are using a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control that contains many records, you may want to let users search for a specific record.</span></span> <span data-ttu-id="d956d-104">而不是控制項本身中搜尋資料，您可以藉由查詢的基礎實作搜尋<xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="d956d-104">Rather than searching the data in the control itself, you can implement a search by querying the underlying <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="d956d-105">如果找到項目，然後您可以使用<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A>屬性設為選取的項目，並捲動至檢視。</span><span class="sxs-lookup"><span data-stu-id="d956d-105">If the item is found, you can then use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> property to select the item and scroll it into view.</span></span>  
  
### <a name="to-implement-search"></a><span data-ttu-id="d956d-106">若要實作搜尋</span><span class="sxs-lookup"><span data-stu-id="d956d-106">To implement search</span></span>  
  
1.  <span data-ttu-id="d956d-107">將 <xref:System.Windows.Forms.TextBox> 控制項從 [工具箱]  拖曳到包含 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的表單上。</span><span class="sxs-lookup"><span data-stu-id="d956d-107">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="d956d-108">在 [屬性] 視窗中，將 **Name** 屬性變更為 **SearchTextBox**。</span><span class="sxs-lookup"><span data-stu-id="d956d-108">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="d956d-109">將 <xref:System.Windows.Forms.Button> 控制項從 [工具箱]  拖曳到包含 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項的表單上。</span><span class="sxs-lookup"><span data-stu-id="d956d-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="d956d-110">在 [屬性] 視窗中，將 **Name** 屬性變更為 **SearchButton**。</span><span class="sxs-lookup"><span data-stu-id="d956d-110">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="d956d-111">將 **Text** 屬性變更為 **Search**。</span><span class="sxs-lookup"><span data-stu-id="d956d-111">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="d956d-112">按兩下 <xref:System.Windows.Forms.Button> 控制項開啟 [程式碼編輯器]，然後將下列程式碼加入 `SearchButton_Click` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d956d-112">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     <span data-ttu-id="d956d-113">取代*ProductsBindingSource*名稱<xref:System.Windows.Forms.BindingSource>如您<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>，並取代*ProductID*具有您想要搜尋的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="d956d-113">Replace *ProductsBindingSource* with the name of the <xref:System.Windows.Forms.BindingSource> for your <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, and replace *ProductID* with the name of the field that you want to search.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d956d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d956d-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="d956d-115">DataRepeater 控制項簡介</span><span class="sxs-lookup"><span data-stu-id="d956d-115">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="d956d-116"> DataRepeater 控制項進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="d956d-116">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="d956d-117">操作說明：變更 DataRepeater 控制項的外觀</span><span class="sxs-lookup"><span data-stu-id="d956d-117">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
