---
title: 如何：在 Windows Form 中存取索引集合
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: 59e5cea29ee520b1f13f8fae98ae4042cc86fef7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538723"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a><span data-ttu-id="8575e-102">如何：在 Windows Form 中存取索引集合</span><span class="sxs-lookup"><span data-stu-id="8575e-102">How to: Access Keyed Collections in Windows Forms</span></span>
-   <span data-ttu-id="8575e-103">您可以依索引鍵來存取個別的收集項目。</span><span class="sxs-lookup"><span data-stu-id="8575e-103">You can access individual collection items by key.</span></span> <span data-ttu-id="8575e-104">這項功能已加入 Windows Form 應用程式通常會使用的許多集合類別。</span><span class="sxs-lookup"><span data-stu-id="8575e-104">This functionality has been added to many collection classes that are typically used by Windows Forms applications.</span></span> <span data-ttu-id="8575e-105">下列清單顯示一些具有可存取的索引的集合的集合類別：</span><span class="sxs-lookup"><span data-stu-id="8575e-105">The following list shows some of the collection classes that have accessible keyed collections:</span></span>  
  
-   <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
-   <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
-   <xref:System.Windows.Forms.Control.ControlCollection>  
  
-   <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
-   <xref:System.Windows.Forms.TreeNodeCollection>  
  
 <span data-ttu-id="8575e-106">集合中的項目相關聯的索引鍵通常是項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="8575e-106">The key associated with an item in a collection is typically the name of the item.</span></span> <span data-ttu-id="8575e-107">下列程序顯示如何使用來執行一般工作的集合類別。</span><span class="sxs-lookup"><span data-stu-id="8575e-107">The following procedures show you how to use collection classes to perform common tasks.</span></span>  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a><span data-ttu-id="8575e-108">尋找和焦點的控制項集合中的巢狀控制項</span><span class="sxs-lookup"><span data-stu-id="8575e-108">To find and give focus to a nested control in a control collection</span></span>  
  
-   <span data-ttu-id="8575e-109">使用<xref:System.Windows.Forms.Control.ControlCollection.Find%2A>和<xref:System.Windows.Forms.Control.Focus%2A>方法，以指定要尋找並給予焦點的控制項名稱。</span><span class="sxs-lookup"><span data-stu-id="8575e-109">Use the <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> and <xref:System.Windows.Forms.Control.Focus%2A> methods to specify the name of the control to find and give focus to.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a><span data-ttu-id="8575e-110">若要存取的影像集合中的映像</span><span class="sxs-lookup"><span data-stu-id="8575e-110">To access an image in an image collection</span></span>  
  
-   <span data-ttu-id="8575e-111">使用<xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A>屬性來指定您想要存取的映像的名稱。</span><span class="sxs-lookup"><span data-stu-id="8575e-111">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> property to specify the name of the image you want to access.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a><span data-ttu-id="8575e-112">若要將選取的索引標籤設定索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="8575e-112">To set a tab page as the selected tab</span></span>  
  
-   <span data-ttu-id="8575e-113">使用<xref:System.Windows.Forms.TabControl.SelectedTab%2A>屬性連同<xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A>屬性，以指定的索引標籤頁面，設定為選取的索引標籤的名稱。</span><span class="sxs-lookup"><span data-stu-id="8575e-113">Use the <xref:System.Windows.Forms.TabControl.SelectedTab%2A> property together with the <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> property to specify the name of the tab page to set as the selected tab.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8575e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8575e-114">See Also</span></span>  
 [<span data-ttu-id="8575e-115">Windows Forms 使用者入門</span><span class="sxs-lookup"><span data-stu-id="8575e-115">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [<span data-ttu-id="8575e-116">操作說明：使用 Windows Forms ImageList 元件加入或移除影像</span><span class="sxs-lookup"><span data-stu-id="8575e-116">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
