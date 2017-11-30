---
title: "如何：變更 Windows Form TabControl 的外觀"
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
- cpp
helpviewer_keywords:
- icons [Windows Forms], displaying on tabs
- TabControl control [Windows Forms], changing page appearance
- tabs [Windows Forms], controlling appearance
- buttons [Windows Forms], displaying tabs as
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b244930f0837d3b1d548e0f7a8c77dd80e1ce039
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a><span data-ttu-id="0b563-102">如何：變更 Windows Form TabControl 的外觀</span><span class="sxs-lookup"><span data-stu-id="0b563-102">How to: Change the Appearance of the Windows Forms TabControl</span></span>
<span data-ttu-id="0b563-103">您可以使用的屬性，以變更 Windows Form 中的索引標籤的外觀<xref:System.Windows.Forms.TabControl>和<xref:System.Windows.Forms.TabPage>組成個別的索引標籤控制項上的物件。</span><span class="sxs-lookup"><span data-stu-id="0b563-103">You can change the appearance of tabs in Windows Forms by using properties of the <xref:System.Windows.Forms.TabControl> and the <xref:System.Windows.Forms.TabPage> objects that make up the individual tabs on the control.</span></span> <span data-ttu-id="0b563-104">藉由設定這些屬性，您可以顯示索引標籤上的映像、 顯示垂直而非水平索引標籤、 顯示多個資料列的索引標籤，和啟用或以程式設計的方式停用索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0b563-104">By setting these properties, you can display images on tabs, display tabs vertically instead of horizontally, display multiple rows of tabs, and enable or disable tabs programmatically.</span></span>  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a><span data-ttu-id="0b563-105">標籤組件的索引標籤上顯示圖示</span><span class="sxs-lookup"><span data-stu-id="0b563-105">To display an icon on the label part of a tab</span></span>  
  
1.  <span data-ttu-id="0b563-106">新增<xref:System.Windows.Forms.ImageList>控制項加入表單。</span><span class="sxs-lookup"><span data-stu-id="0b563-106">Add an <xref:System.Windows.Forms.ImageList> control to the form.</span></span>  
  
2.  <span data-ttu-id="0b563-107">將影像加入至映像清單。</span><span class="sxs-lookup"><span data-stu-id="0b563-107">Add images to the image list.</span></span>  
  
     <span data-ttu-id="0b563-108">如需影像清單的詳細資訊，請參閱[ImageList 元件](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)和[如何： 加入或移除映像使用 Windows Form ImageList 元件](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。</span><span class="sxs-lookup"><span data-stu-id="0b563-108">For more information about image lists, see [ImageList Component](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
3.  <span data-ttu-id="0b563-109">設定<xref:System.Windows.Forms.TabControl.ImageList%2A>屬性<xref:System.Windows.Forms.TabControl>至<xref:System.Windows.Forms.ImageList>控制項。</span><span class="sxs-lookup"><span data-stu-id="0b563-109">Set the <xref:System.Windows.Forms.TabControl.ImageList%2A> property of the <xref:System.Windows.Forms.TabControl> to the <xref:System.Windows.Forms.ImageList> control.</span></span>  
  
4.  <span data-ttu-id="0b563-110">設定<xref:System.Windows.Forms.TabPage.ImageIndex%2A>屬性<xref:System.Windows.Forms.TabPage>為適當的映像清單中的索引。</span><span class="sxs-lookup"><span data-stu-id="0b563-110">Set the <xref:System.Windows.Forms.TabPage.ImageIndex%2A> property of the <xref:System.Windows.Forms.TabPage> to the index of an appropriate image in the list.</span></span>  
  
### <a name="to-create-multiple-rows-of-tabs"></a><span data-ttu-id="0b563-111">若要建立多個資料列的索引標籤</span><span class="sxs-lookup"><span data-stu-id="0b563-111">To create multiple rows of tabs</span></span>  
  
1.  <span data-ttu-id="0b563-112">新增您想要的索引標籤頁的數目。</span><span class="sxs-lookup"><span data-stu-id="0b563-112">Add the number of tab pages you want.</span></span>  
  
2.  <span data-ttu-id="0b563-113">設定<xref:System.Windows.Forms.TabControl.Multiline%2A>屬性<xref:System.Windows.Forms.TabControl>至`true`。</span><span class="sxs-lookup"><span data-stu-id="0b563-113">Set the <xref:System.Windows.Forms.TabControl.Multiline%2A> property of the <xref:System.Windows.Forms.TabControl> to `true`.</span></span>  
  
3.  <span data-ttu-id="0b563-114">如果索引標籤已經不在多個資料列，設定<xref:System.Windows.Forms.Control.Width%2A>屬性<xref:System.Windows.Forms.TabControl>為窄比所有索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0b563-114">If the tabs do not already appear in multiple rows, set the <xref:System.Windows.Forms.Control.Width%2A> property of the <xref:System.Windows.Forms.TabControl> to be narrower than all the tabs.</span></span>  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a><span data-ttu-id="0b563-115">若要排列控制項的側邊的索引標籤</span><span class="sxs-lookup"><span data-stu-id="0b563-115">To arrange tabs on the side of the control</span></span>  
  
-   <span data-ttu-id="0b563-116">設定<xref:System.Windows.Forms.TabControl.Alignment%2A>屬性<xref:System.Windows.Forms.TabControl>至<xref:System.Windows.Forms.TabAlignment.Left>或<xref:System.Windows.Forms.TabAlignment.Right>。</span><span class="sxs-lookup"><span data-stu-id="0b563-116">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAlignment.Left> or <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a><span data-ttu-id="0b563-117">以程式設計方式啟用或停用索引標籤上的所有控制項</span><span class="sxs-lookup"><span data-stu-id="0b563-117">To programmatically enable or disable all controls on a tab</span></span>  
  
1.  <span data-ttu-id="0b563-118">設定<xref:System.Windows.Forms.TabPage.Enabled%2A>屬性<xref:System.Windows.Forms.TabPage>至`true`或`false`。</span><span class="sxs-lookup"><span data-stu-id="0b563-118">Set the <xref:System.Windows.Forms.TabPage.Enabled%2A> property of the <xref:System.Windows.Forms.TabPage> to `true` or `false`.</span></span>  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a><span data-ttu-id="0b563-119">若要為按鈕會顯示索引標籤</span><span class="sxs-lookup"><span data-stu-id="0b563-119">To display tabs as buttons</span></span>  
  
-   <span data-ttu-id="0b563-120">設定<xref:System.Windows.Forms.TabControl.Appearance%2A>屬性<xref:System.Windows.Forms.TabControl>至<xref:System.Windows.Forms.TabAppearance.Buttons>或<xref:System.Windows.Forms.TabAppearance.FlatButtons>。</span><span class="sxs-lookup"><span data-stu-id="0b563-120">Set the <xref:System.Windows.Forms.TabControl.Appearance%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAppearance.Buttons> or <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b563-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b563-121">See Also</span></span>  
 [<span data-ttu-id="0b563-122">TabControl 控制項</span><span class="sxs-lookup"><span data-stu-id="0b563-122">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="0b563-123">TabControl 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="0b563-123">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="0b563-124">操作說明：將控制項加入至索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="0b563-124">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [<span data-ttu-id="0b563-125">操作說明：停用索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="0b563-125">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="0b563-126">操作說明：使用 Windows Forms TabControl 加入和移除索引標籤</span><span class="sxs-lookup"><span data-stu-id="0b563-126">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
