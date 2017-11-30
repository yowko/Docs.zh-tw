---
title: "如何：使用含階層式資料的主從式模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb546a3429012a49ee7652a3470460935fc76d70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>如何：使用含階層式資料的主從式模式
這個範例示範如何實作的主檔/明細 」 案例。  
  
## <a name="example"></a>範例  
 在此範例中，`LeagueList`是一組`Leagues`。 每個`League`具有`Name`和集合`Divisions`，而且每個`Division`有一個名稱和集合`Teams`。 每個`Team`小組名稱。  
  
 [!code-xaml[MasterDetail#HowTo1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 以下是範例的螢幕擷取畫面。 `Divisions` <xref:System.Windows.Controls.ListBox>自動追蹤中的選取項目`Leagues`<xref:System.Windows.Controls.ListBox>並顯示對應的資料。 `Teams` <xref:System.Windows.Controls.ListBox>會追蹤其他兩個選取項目<xref:System.Windows.Controls.ListBox>控制項。  
  
 ![主要 &#45; 詳細資料範例](../../../../docs/framework/wpf/data/media/databindingmasterdetailsample.png "DataBindingMasterDetailSample")  
  
 請注意，在此範例中的兩個事項如下：  
  
1.  三個<xref:System.Windows.Controls.ListBox>控制項繫結至相同的來源。 您設定<xref:System.Windows.Data.Binding.Path%2A>繫結來指定您想要的資料層級屬性<xref:System.Windows.Controls.ListBox>顯示。  
  
2.  您必須設定<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>屬性`true`上<xref:System.Windows.Controls.ListBox>控制項，其中您追蹤選取範圍。 設定這個屬性可確保已選取的項目一律會設為<xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>。 或者，如果<xref:System.Windows.Controls.ListBox>取得它的資料<xref:System.Windows.Data.CollectionViewSource>，自動同步選取範圍和貨幣。  
  
 當您使用的技巧是稍有不同[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]資料。 如需範例，請參閱[階層式 XML 資料搭配使用主版詳細資料模式](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.HierarchicalDataTemplate>  
 [繫結至集合並根據選取項目顯示資訊](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [操作說明主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
