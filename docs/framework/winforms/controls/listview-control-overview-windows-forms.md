---
title: "ListView 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ListView
helpviewer_keywords:
- lists
- ListView control [Windows Forms], about ListView control
- list views
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bda009beb429345d05aeba4e04f2ce1f07e627da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="listview-control-overview-windows-forms"></a>ListView 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.ListView> 控制項顯示具有圖示的項目清單。 若要建立像 Windows 檔案總管右窗格的使用者介面，您可以使用清單檢視。 控制項有四個檢視模式： 使用 LargeIcon、 SmallIcon、 清單和詳細資料。  
  
## <a name="what-you-can-do-with-the-listview-control"></a>您可以執行使用 ListView 控制項  
  
> [!NOTE]
>  額外的檢視模式中，圖格，才可以使用 Windows XP 和 Windows Server 2003 作業系統。 如需詳細資訊，請參閱[How to： 在 Windows Form ListView 控制項中啟用並排顯示檢視](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md)。  
  
 使用 LargeIcon 模式會顯示大圖示旁邊的項目文字。如果控制項為夠大，項目會出現在多個資料行中。 不同之處在於它會顯示小圖示的 SmallIcon 模式都是相同的。 清單模式顯示小圖示，但一律是單一資料行中。 詳細資料模式下顯示多個資料行中的項目。 如需詳細資訊，請參閱[How to： 將資料行加入 Windows Form ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)。 檢視模式由<xref:System.Windows.Forms.ListView.View%2A>屬性。 所有的檢視模式可以顯示從影像清單的映像。 如需詳細資訊，請參閱[如何： 顯示 Windows Form ListView 控制項的圖示](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)。  
  
 下表列出一些<xref:System.Windows.Forms.ListView>成員以及中是有效的檢視。  
  
|ListView 成員|檢視|  
|---------------------|----------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A> 屬性|<xref:System.Windows.Forms.View.SmallIcon> 或 <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A> 屬性|<xref:System.Windows.Forms.View.SmallIcon> 或 <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A> 方法|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.Columns%2A> 屬性|<xref:System.Windows.Forms.View.Details> 或 <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.DrawSubItem>事件|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A> 方法|<xref:System.Windows.Forms.View.Details>、<xref:System.Windows.Forms.View.List> 或 <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A> 方法|<xref:System.Windows.Forms.View.SmallIcon> 或 <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A> 方法|<xref:System.Windows.Forms.View.Details> 或 <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.Groups%2A> 屬性|以外的所有模式<xref:System.Windows.Forms.View.List>|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A> 屬性|<xref:System.Windows.Forms.View.Details>.|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A> 屬性|<xref:System.Windows.Forms.View.LargeIcon>、<xref:System.Windows.Forms.View.SmallIcon> 或 <xref:System.Windows.Forms.View.Tile>|  
  
 索引鍵內容<xref:System.Windows.Forms.ListView>控制項是<xref:System.Windows.Forms.ListView.Items%2A>，其中包含由控制項所顯示的項目。 <xref:System.Windows.Forms.ListView.SelectedItems%2A>屬性包含控制項中目前選取的項目集合。 使用者可以選取多個項目，例如拖放到另一個控制項，一次的數個項目，如果<xref:System.Windows.Forms.ListView.MultiSelect%2A>屬性設定為`true`。 <xref:System.Windows.Forms.ListView>控制項可以顯示的項目旁邊的核取方塊，如果<xref:System.Windows.Forms.ListView.CheckBoxes%2A>屬性設定為`true`。  
  
 <xref:System.Windows.Forms.ListView.Activation%2A>屬性會決定使用者必須採取的動作類型啟用清單中的項目： 選項<xref:System.Windows.Forms.ItemActivation.Standard>， <xref:System.Windows.Forms.ItemActivation.OneClick>，和<xref:System.Windows.Forms.ItemActivation.TwoClick>。 <xref:System.Windows.Forms.ItemActivation.OneClick>啟用需要只要按一下来啟動的項目。 <xref:System.Windows.Forms.ItemActivation.TwoClick>啟用要求使用者按兩下以啟動項目。只要按一下變更項目文字的色彩。 <xref:System.Windows.Forms.ItemActivation.Standard>啟用要求使用者按兩下以啟動項，但項目不會變更外觀。  
  
 <xref:System.Windows.Forms.ListView>控制項也支援視覺化樣式和其他可用的功能在 Windows XP 平台，包括群組、 並排顯示檢視和 插入標記。 如需詳細資訊，請參閱[Windows XP 功能和 Windows Form 控制項](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ListView>  
 [ListView 控制項](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [操作說明：使用 Windows Forms ListView 控制項加入和移除項目](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [操作說明：將資料行加入至 Windows Forms ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [操作說明：顯示 Windows Forms ListView 控制項的圖示](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [操作說明：使用 Windows Forms ListView 控制項以資料行顯示子項目](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [操作說明：選取 Windows Forms ListView 控制項中的項目](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)  
 [操作說明：在 Windows Forms ListView 控制項中群組項目](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)  
 [操作說明：在 Windows Forms ListView 控制項中顯示插入標記](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)  
 [操作說明：將搜尋能力加入至 ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
 [操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [逐步解說：利用 Windows Forms 建立多窗格使用者介面](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)
