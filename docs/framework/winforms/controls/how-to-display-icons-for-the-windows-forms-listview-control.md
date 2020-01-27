---
title: 顯示 ListView 控制項的圖示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], displaying icons
- icons [Windows Forms], displaying for ListView controls
- lists [Windows Forms], displaying icons
- ImageList component [Windows Forms], with ListView control
- list views [Windows Forms], displaying icons
ms.assetid: 9d577542-8595-429b-99e5-078770ec9d35
ms.openlocfilehash: 5fc54c448dae95cab50cdafa8403769fb421dffa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744500"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a><span data-ttu-id="ca459-102">如何：顯示 Windows Form ListView 控制項的圖示</span><span class="sxs-lookup"><span data-stu-id="ca459-102">How to: Display Icons for the Windows Forms ListView Control</span></span>
<span data-ttu-id="ca459-103">Windows Forms <xref:System.Windows.Forms.ListView> 控制項可以顯示三個影像清單中的圖示。</span><span class="sxs-lookup"><span data-stu-id="ca459-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display icons from three image lists.</span></span> <span data-ttu-id="ca459-104">[清單]、[詳細資料] 和 [SmallIcon] 視圖會顯示 [<xref:System.Windows.Forms.ListView.SmallImageList%2A>] 屬性中所指定影像清單中的影像。</span><span class="sxs-lookup"><span data-stu-id="ca459-104">The List, Details, and SmallIcon views display images from the image list specified in the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property.</span></span> <span data-ttu-id="ca459-105">[LargeIcon] 視圖會顯示 [<xref:System.Windows.Forms.ListView.LargeImageList%2A>] 屬性中所指定影像清單中的影像。</span><span class="sxs-lookup"><span data-stu-id="ca459-105">The LargeIcon view displays images from the image list specified in the <xref:System.Windows.Forms.ListView.LargeImageList%2A> property.</span></span> <span data-ttu-id="ca459-106">清單視圖也可以在 [<xref:System.Windows.Forms.ListView.StateImageList%2A>] 屬性中，于大型或小圖示旁顯示一組額外的圖示。</span><span class="sxs-lookup"><span data-stu-id="ca459-106">A list view can also display an additional set of icons, set in the <xref:System.Windows.Forms.ListView.StateImageList%2A> property, next to the large or small icons.</span></span> <span data-ttu-id="ca459-107">如需影像清單的詳細資訊，請參閱[ImageList 元件](imagelist-component-windows-forms.md)和[如何：使用 Windows Forms ImageList 元件來新增或移除影像](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。</span><span class="sxs-lookup"><span data-stu-id="ca459-107">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
### <a name="to-display-images-in-a-list-view"></a><span data-ttu-id="ca459-108">若要在清單視圖中顯示影像</span><span class="sxs-lookup"><span data-stu-id="ca459-108">To display images in a list view</span></span>  
  
1. <span data-ttu-id="ca459-109">將適當的屬性（<xref:System.Windows.Forms.ListView.SmallImageList%2A>、<xref:System.Windows.Forms.ListView.LargeImageList%2A>或 <xref:System.Windows.Forms.ListView.StateImageList%2A>）設定為您想要使用的現有 <xref:System.Windows.Forms.ImageList> 元件。</span><span class="sxs-lookup"><span data-stu-id="ca459-109">Set the appropriate property—<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, or <xref:System.Windows.Forms.ListView.StateImageList%2A>—to the existing <xref:System.Windows.Forms.ImageList> component you wish to use.</span></span>  
  
     <span data-ttu-id="ca459-110">這些屬性可以在設計工具中，使用屬性視窗或程式碼來設定。</span><span class="sxs-lookup"><span data-stu-id="ca459-110">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2. <span data-ttu-id="ca459-111">針對具有相關聯圖示的每個清單專案，設定 [<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>] 或 [<xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A>] 屬性。</span><span class="sxs-lookup"><span data-stu-id="ca459-111">Set the <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> or <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> property for each list item that has an associated icon.</span></span>  
  
     <span data-ttu-id="ca459-112">這些屬性可以在程式碼中設定，或在 [ **ListViewItem 集合編輯器**] 內設定。</span><span class="sxs-lookup"><span data-stu-id="ca459-112">These properties can be set in code, or within the **ListViewItem Collection Editor**.</span></span> <span data-ttu-id="ca459-113">若要開啟 [ **ListViewItem 集合編輯器**]，請按一下省略號按鈕（![[**屬性**] 視窗上 [<xref:System.Windows.Forms.ListView.Items%2A>] 屬性旁邊的 Visual Studio.](./media/visual-studio-ellipsis-button.png)）屬性視窗中的省略號按鈕（...）。</span><span class="sxs-lookup"><span data-stu-id="ca459-113">To open the **ListViewItem Collection Editor**, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ListView.Items%2A> property on the **Properties** window.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="ca459-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="ca459-114">See also</span></span>

- [<span data-ttu-id="ca459-115">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="ca459-115">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
- [<span data-ttu-id="ca459-116">操作說明：使用 Windows Forms ListView 控制項加入和移除項目</span><span class="sxs-lookup"><span data-stu-id="ca459-116">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="ca459-117">操作說明：將資料行加入至 Windows Forms ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="ca459-117">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [<span data-ttu-id="ca459-118">操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ca459-118">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [<span data-ttu-id="ca459-119">ImageList 元件</span><span class="sxs-lookup"><span data-stu-id="ca459-119">ImageList Component</span></span>](imagelist-component-windows-forms.md)
