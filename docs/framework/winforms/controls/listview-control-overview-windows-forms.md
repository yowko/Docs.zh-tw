---
title: ListView 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- ListView
helpviewer_keywords:
- lists
- ListView control [Windows Forms], about ListView control
- list views
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
ms.openlocfilehash: 7b7eac942a7e857ad731c0f77389e84aee287c08
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952157"
---
# <a name="listview-control-overview-windows-forms"></a>ListView 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.ListView> 控制項顯示具有圖示的項目清單。 若要建立像 Windows 檔案總管右窗格的使用者介面，您可以使用清單檢視。 控制項有四個視圖模式:LargeIcon、SmallIcon、List 和 Details。  
  
## <a name="what-you-can-do-with-the-listview-control"></a>如何使用 ListView 控制項  
  
> [!NOTE]
> 您只能在 Windows XP 和 Windows Server 2003 作業系統上使用額外的視圖模式 (磚)。 如需詳細資訊，請參閱[如何：在 Windows Forms ListView 控制項](how-to-enable-tile-view-in-a-windows-forms-listview-control.md)中啟用並排顯示。  
  
 LargeIcon 模式會顯示專案文字旁邊的大圖示;如果控制項夠大, 這些專案就會出現在多個資料行中。 SmallIcon 模式是相同的, 不同之處在于它會顯示小圖示。 [清單] 模式會顯示小圖示, 但一定會出現在單一資料行中。 [詳細資料] 模式會顯示多個資料行中的專案。 如需詳細資訊，請參閱[如何：將資料行新增至 Windows Forms ListView](how-to-add-columns-to-the-windows-forms-listview-control.md)控制項。 View 模式是由<xref:System.Windows.Forms.ListView.View%2A>屬性所決定。 所有的視圖模式都可以顯示影像清單中的影像。 如需詳細資訊，請參閱[如何：顯示 Windows Forms ListView 控制項](how-to-display-icons-for-the-windows-forms-listview-control.md)的圖示。  
  
 下表列出一些<xref:System.Windows.Forms.ListView>成員及其在中有效的視圖。  
  
|ListView 成員|檢視|  
|---------------------|----------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A> 屬性|<xref:System.Windows.Forms.View.SmallIcon> 或 <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A> 屬性|<xref:System.Windows.Forms.View.SmallIcon> 或 <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A> 方法|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.Columns%2A> 屬性|<xref:System.Windows.Forms.View.Details> 或 <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.DrawSubItem> 事件|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A> 方法|<xref:System.Windows.Forms.View.Details>、 <xref:System.Windows.Forms.View.List>或 <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A> 方法|<xref:System.Windows.Forms.View.SmallIcon> 或 <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A> 方法|<xref:System.Windows.Forms.View.Details> 或 <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.Groups%2A> 屬性|除了以外的所有視圖<xref:System.Windows.Forms.View.List>|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A> 屬性|<xref:System.Windows.Forms.View.Details>.|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A> 屬性|<xref:System.Windows.Forms.View.LargeIcon>、 <xref:System.Windows.Forms.View.SmallIcon>或 <xref:System.Windows.Forms.View.Tile>|  
  
 <xref:System.Windows.Forms.ListView>控制項的索引鍵屬性為<xref:System.Windows.Forms.ListView.Items%2A>, 其中包含控制項所顯示的專案。 <xref:System.Windows.Forms.ListView.SelectedItems%2A>屬性包含目前在控制項中選取之專案的集合。 使用者可以選取多個專案, 例如, 如果<xref:System.Windows.Forms.ListView.MultiSelect%2A>屬性設定為`true`, 則會一次將數個專案拖放到另一個控制項。 如果屬性設定為`true`,控制項可以顯示專案旁的核取方塊。<xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.ListView.CheckBoxes%2A>  
  
 屬性會決定使用者必須採取哪些類型的動作來啟動清單中的專案: 選項包括<xref:System.Windows.Forms.ItemActivation.Standard>、 <xref:System.Windows.Forms.ItemActivation.OneClick>和<xref:System.Windows.Forms.ItemActivation.TwoClick>。 <xref:System.Windows.Forms.ListView.Activation%2A> <xref:System.Windows.Forms.ItemActivation.OneClick>啟用時, 只需要按一下即可啟動專案。 <xref:System.Windows.Forms.ItemActivation.TwoClick>啟用時, 使用者必須按兩下以啟動專案。按一下即可變更專案文字的色彩。 <xref:System.Windows.Forms.ItemActivation.Standard>啟用時, 使用者必須按兩下來啟動專案, 但該專案不會變更外觀。  
  
 <xref:System.Windows.Forms.ListView>控制項也支援 Windows XP 平臺上可用的視覺化樣式和其他功能, 包括群組、磚視圖和插入標記。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ListView>
- [ListView 控制項](listview-control-windows-forms.md)
- [如何：使用 Windows Forms ListView 控制項新增和移除專案](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [如何：將資料行新增至 Windows Forms ListView 控制項](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [如何：顯示 Windows Forms ListView 控制項的圖示](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [如何：在具有 Windows Forms ListView 控制項的資料行中顯示子項](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [如何：選取 Windows Forms ListView 控制項中的專案](how-to-select-an-item-in-the-windows-forms-listview-control.md)
- [如何：Windows Forms ListView 控制項中的群組專案](how-to-group-items-in-a-windows-forms-listview-control.md)
- [如何：在 Windows Forms ListView 控制項中顯示插入標記](how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)
- [如何：將搜尋功能新增至 ListView 控制項](how-to-add-search-capabilities-to-a-listview-control.md)
- [如何：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [如何：建立具有 Windows Forms 的多窗格使用者介面](how-to-create-a-multipane-user-interface-with-windows-forms.md)
