---
title: "如何：顯示 Windows Form ListView 控制項的圖示"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3a19bdd7007a7e47fa1a8ad975112e53c1b6eb5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a><span data-ttu-id="ab19a-102">如何：顯示 Windows Form ListView 控制項的圖示</span><span class="sxs-lookup"><span data-stu-id="ab19a-102">How to: Display Icons for the Windows Forms ListView Control</span></span>
<span data-ttu-id="ab19a-103">Windows Form<xref:System.Windows.Forms.ListView>控制項可以顯示三個影像清單中的圖示。</span><span class="sxs-lookup"><span data-stu-id="ab19a-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display icons from three image lists.</span></span> <span data-ttu-id="ab19a-104">清單、 詳細資料，以及 SmallIcon 檢視會顯示從影像清單中指定的映像<xref:System.Windows.Forms.ListView.SmallImageList%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ab19a-104">The List, Details, and SmallIcon views display images from the image list specified in the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property.</span></span> <span data-ttu-id="ab19a-105">使用 LargeIcon 檢視會顯示從影像清單中指定的映像<xref:System.Windows.Forms.ListView.LargeImageList%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ab19a-105">The LargeIcon view displays images from the image list specified in the <xref:System.Windows.Forms.ListView.LargeImageList%2A> property.</span></span> <span data-ttu-id="ab19a-106">清單檢視也可以顯示一組額外的設定的圖示<xref:System.Windows.Forms.ListView.StateImageList%2A>大型或小型圖示旁邊的屬性。</span><span class="sxs-lookup"><span data-stu-id="ab19a-106">A list view can also display an additional set of icons, set in the <xref:System.Windows.Forms.ListView.StateImageList%2A> property, next to the large or small icons.</span></span> <span data-ttu-id="ab19a-107">如需影像清單的詳細資訊，請參閱[ImageList 元件](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)和[如何： 加入或移除映像使用 Windows Form ImageList 元件](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。</span><span class="sxs-lookup"><span data-stu-id="ab19a-107">For more information about image lists, see [ImageList Component](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
### <a name="to-display-images-in-a-list-view"></a><span data-ttu-id="ab19a-108">在清單檢視中顯示影像</span><span class="sxs-lookup"><span data-stu-id="ab19a-108">To display images in a list view</span></span>  
  
1.  <span data-ttu-id="ab19a-109">設定適當的屬性 —<xref:System.Windows.Forms.ListView.SmallImageList%2A>， <xref:System.Windows.Forms.ListView.LargeImageList%2A>，或<xref:System.Windows.Forms.ListView.StateImageList%2A>— 加入現有<xref:System.Windows.Forms.ImageList>您想要使用的元件。</span><span class="sxs-lookup"><span data-stu-id="ab19a-109">Set the appropriate property—<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A>, or <xref:System.Windows.Forms.ListView.StateImageList%2A>—to the existing <xref:System.Windows.Forms.ImageList> component you wish to use.</span></span>  
  
     <span data-ttu-id="ab19a-110">使用 [屬性] 視窗中，在設計工具或程式碼，可以設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="ab19a-110">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2.  <span data-ttu-id="ab19a-111">設定<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>或<xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A>屬性每個清單項目具有相關聯的圖示。</span><span class="sxs-lookup"><span data-stu-id="ab19a-111">Set the <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> or <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> property for each list item that has an associated icon.</span></span>  
  
     <span data-ttu-id="ab19a-112">可以設定這些屬性，程式碼或內部**ListViewItem 集合編輯器**。</span><span class="sxs-lookup"><span data-stu-id="ab19a-112">These properties can be set in code, or within the **ListViewItem Collection Editor**.</span></span> <span data-ttu-id="ab19a-113">若要開啟**ListViewItem 集合編輯器**，按一下省略符號按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 旁邊<xref:System.Windows.Forms.ListView.Items%2A>屬性**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="ab19a-113">To open the **ListViewItem Collection Editor**, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.ListView.Items%2A> property on the **Properties** window.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="ab19a-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="ab19a-114">See Also</span></span>  
 [<span data-ttu-id="ab19a-115">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="ab19a-115">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="ab19a-116">操作說明：使用 Windows Forms ListView 控制項加入和移除項目</span><span class="sxs-lookup"><span data-stu-id="ab19a-116">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="ab19a-117">操作說明：將資料行加入至 Windows Forms ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="ab19a-117">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="ab19a-118">操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ab19a-118">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [<span data-ttu-id="ab19a-119">ImageList 元件</span><span class="sxs-lookup"><span data-stu-id="ab19a-119">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
