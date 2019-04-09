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
ms.openlocfilehash: a60c415427a1be994f8081725f20e867dca66aa1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101877"
---
# <a name="listview-control-overview-windows-forms"></a>ListView 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.ListView> 控制項顯示具有圖示的項目清單。 若要建立像 Windows 檔案總管右窗格的使用者介面，您可以使用清單檢視。 控制項有四種檢視模式：LargeIcon、 SmallIcon、 清單和詳細資料。  
  
## <a name="what-you-can-do-with-the-listview-control"></a>您可以執行與 ListView 控制項  
  
> [!NOTE]
>  額外的檢視模式中，圖格，才可使用 Windows XP 和 Windows Server 2003 作業系統上。 如需詳細資訊，請參閱[如何：啟用並排顯示檢視中的 Windows Form ListView 控制項](how-to-enable-tile-view-in-a-windows-forms-listview-control.md)。  
  
 LargeIcon 模式會顯示項目文字旁的大圖示如果控制項是夠大，項目會出現在多個資料行。 不同之處在於它會顯示小圖示的 [smallicon] 模式都是相同的。 清單模式會顯示小圖示，但一律為單一資料行。 詳細資料模式會顯示多個資料行中的項目。 如需詳細資訊，請參閱[如何：資料行以 Windows Form ListView 控制項中加入](how-to-add-columns-to-the-windows-forms-listview-control.md)。 檢視模式由<xref:System.Windows.Forms.ListView.View%2A>屬性。 所有的檢視模式來顯示從影像清單的影像。 如需詳細資訊，請參閱[如何：顯示 Windows Form ListView 控制項的圖示](how-to-display-icons-for-the-windows-forms-listview-control.md)。  
  
 下表列出一些<xref:System.Windows.Forms.ListView>成員和檢視中有效。  
  
|ListView 成員|檢視|  
|---------------------|----------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A> 屬性|<xref:System.Windows.Forms.View.SmallIcon> 或 <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A> 屬性|<xref:System.Windows.Forms.View.SmallIcon> 或 <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A> 方法|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.Columns%2A> 屬性|<xref:System.Windows.Forms.View.Details> 或 <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.DrawSubItem> Event - 事件|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A> 方法|<xref:System.Windows.Forms.View.Details>、 <xref:System.Windows.Forms.View.List>或 <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A> 方法|<xref:System.Windows.Forms.View.SmallIcon> 或 <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A> 方法|<xref:System.Windows.Forms.View.Details> 或 <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.Groups%2A> 屬性|以外的所有檢視 <xref:System.Windows.Forms.View.List>|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A> 屬性|<xref:System.Windows.Forms.View.Details>。|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A> 屬性|<xref:System.Windows.Forms.View.LargeIcon>、 <xref:System.Windows.Forms.View.SmallIcon>或 <xref:System.Windows.Forms.View.Tile>|  
  
 索引鍵內容<xref:System.Windows.Forms.ListView>控制項是<xref:System.Windows.Forms.ListView.Items%2A>，其中包含控制項所顯示的項目。 <xref:System.Windows.Forms.ListView.SelectedItems%2A>屬性包含控制項中目前選取的項目集合。 使用者可以選取多個項目，例如拖放到另一個控制項，一次的數個項目，如果<xref:System.Windows.Forms.ListView.MultiSelect%2A>屬性設定為`true`。 <xref:System.Windows.Forms.ListView>控制項可以顯示的項目旁的核取方塊，如果<xref:System.Windows.Forms.ListView.CheckBoxes%2A>屬性設定為`true`。  
  
 <xref:System.Windows.Forms.ListView.Activation%2A>屬性會決定使用者必須採取的動作類型啟動清單中的項目： 選項<xref:System.Windows.Forms.ItemActivation.Standard>， <xref:System.Windows.Forms.ItemActivation.OneClick>，和<xref:System.Windows.Forms.ItemActivation.TwoClick>。 <xref:System.Windows.Forms.ItemActivation.OneClick> 啟用需要只要按一下以啟動項目。 <xref:System.Windows.Forms.ItemActivation.TwoClick> 啟用要求使用者必須按兩下來啟動項目;只要按一下變更項目文字的色彩。 <xref:System.Windows.Forms.ItemActivation.Standard> 啟用要求使用者必須按兩下來啟動項目，但項目不會變更外觀。  
  
 <xref:System.Windows.Forms.ListView>控制項也支援視覺化樣式，以及其他可用的功能在 Windows XP 平台，包括群組、 並排顯示檢視和 插入標記。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ListView>
- [ListView 控制項](listview-control-windows-forms.md)
- [HOW TO：使用 Windows Forms ListView 控制項新增和移除項目](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [HOW TO：將資料行新增至 Windows Form ListView 控制項](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [HOW TO：顯示 Windows Forms ListView 控制項的圖示](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [HOW TO：使用 Windows Forms ListView 控制項顯示資料行的子項目](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [HOW TO：選取 Windows Forms ListView 控制項的項目](how-to-select-an-item-in-the-windows-forms-listview-control.md)
- [HOW TO：在 Windows Forms ListView 控制項中分組項目](how-to-group-items-in-a-windows-forms-listview-control.md)
- [HOW TO：在 Windows Forms ListView 控制項中顯示插入標記](how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)
- [HOW TO：將搜尋功能新增至 ListView 控制項](how-to-add-search-capabilities-to-a-listview-control.md)
- [HOW TO：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [HOW TO：使用 Windows Forms 建立多窗格使用者介面](how-to-create-a-multipane-user-interface-with-windows-forms.md)
