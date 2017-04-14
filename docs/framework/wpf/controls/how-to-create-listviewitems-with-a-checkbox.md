---
title: "如何：使用 CheckBox 建立 ListViewItems | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ListView 控制項"
  - "核取方塊控制項"
  - "ListView 控制項中，核取方塊控制項"
  - "核取方塊控制項，ListView 控制項"
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：使用 CheckBox 建立 ListViewItems
這個範例示範如何顯示的資料行<xref:System.Windows.Controls.CheckBox>控制項<xref:System.Windows.Controls.ListView>使用控制項<xref:System.Windows.Controls.GridView>。  
  
## <a name="example"></a>範例  
 若要建立包含的資料行<xref:System.Windows.Controls.CheckBox>控制項<xref:System.Windows.Controls.ListView>，建立<xref:System.Windows.DataTemplate> ，其中包含<xref:System.Windows.Controls.CheckBox>。 然後設定<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>的<xref:System.Windows.Controls.GridViewColumn>至<xref:System.Windows.DataTemplate>。  
  
 下列範例所示<xref:System.Windows.DataTemplate> ，其中包含<xref:System.Windows.Controls.CheckBox>。 範例會繫結<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>屬性<xref:System.Windows.Controls.CheckBox>至<xref:System.Windows.Controls.ListBoxItem.IsSelected%2A>屬性值為<xref:System.Windows.Controls.ListViewItem> ，其中包含它。 因此，當<xref:System.Windows.Controls.ListViewItem> ，其中包含<xref:System.Windows.Controls.CheckBox>選取時，<xref:System.Windows.Controls.CheckBox>已核取。  
  
 [!code-xml[ListViewChkBox#CheckBoxDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 下列範例示範如何建立資料行的<xref:System.Windows.Controls.CheckBox>控制項。 若要將欄中，範例會設定<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>屬性<xref:System.Windows.Controls.GridViewColumn>至<xref:System.Windows.DataTemplate>。  
  
 [!code-xml[ListViewChkBox#GridViewColumnCheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Control>   
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [How to 主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)