---
title: "如何：繫結至集合並根據選取項目顯示資訊 | Microsoft Docs"
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
  - "資料繫結, 繫結至集合"
  - "資料繫結, 建立資料集合的檢視"
  - "資料繫結, 選取檢視資料"
  - "資料集合, 選取檢視資料"
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：繫結至集合並根據選取項目顯示資訊
在簡單的主從式案例中，您有資料繫結 <xref:System.Windows.Controls.ItemsControl>，例如 <xref:System.Windows.Controls.ListBox>。  根據使用者選取項目，您會顯示所選項目的詳細資訊。  這個範例顯示如何實作此案例。  
  
## 範例  
 在這個範例中，`People` 是 `Person` 類別 \(Class\) 的 <xref:System.Collections.ObjectModel.ObservableCollection%601>。  此 `Person` 類別包含三種屬性：`FirstName`、`LastName` 和 `HomeTown`，全部的型別都是 `string`。  
  
 [!code-xml[CollectionBinding#Source](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xml[CollectionBinding#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl> 使用下列 <xref:System.Windows.DataTemplate>，用於定義如何呈現 `Person` 的資訊：  
  
 [!code-xml[CollectionBinding#DetailTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 以下是範例所產生的螢幕擷取畫面。  <xref:System.Windows.Controls.ContentControl> 會顯示所選人員的其他屬性。  
  
 ![繫結至集合](../../../../docs/framework/wpf/data/media/databinding-collectionbindingsample.png "DataBinding\_CollectionBindingSample")  
  
 在這個範例中應該注意兩件事：  
  
1.  <xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.ContentControl> 繫結至相同來源。  這兩個繫結的 <xref:System.Windows.Data.Binding.Path%2A> 屬性都未指定，因為兩個控制項都是繫結至整個集合物件。  
  
2.  您必須將 <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> 屬性設定為 `true`，才能產生作用。  設定這個屬性，可確保選取的項目一律設定為 <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>。  不過，如果 <xref:System.Windows.Controls.ListBox> 是從 <xref:System.Windows.Data.CollectionViewSource> 取得其資料，則它會自動同步 \(Synchronize\) 選取項目與貨幣。  
  
 請注意，`Person` 類別會以下列方式覆寫 `ToString` 方法。  根據預設，<xref:System.Windows.Controls.ListBox> 會呼叫 `ToString` 並顯示繫結集合中每個物件的字串表示。  這就是為什麼每個 `Person` 會在 <xref:System.Windows.Controls.ListBox> 中顯示為名字。  
  
 [!code-csharp[CollectionBinding#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## 請參閱  
 [使用含階層式資料的主從式模式](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)   
 [使用含階層式 XML 資料的主從式模式](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)