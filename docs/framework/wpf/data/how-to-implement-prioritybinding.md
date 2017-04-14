---
title: "如何：實作 PriorityBinding | Microsoft Docs"
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
  - "類別, PriorityBinding"
  - "資料繫結, PriorityBinding 類別"
  - "PriorityBinding 類別"
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：實作 PriorityBinding
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的 <xref:System.Windows.Data.PriorityBinding> 是透過指定繫結清單來運作。  繫結清單是從最高優先權排到最低優先權。  如果處理的最高優先權繫結順利傳回值，就絕不再需要處理清單中的其他繫結。  如果最高優先權繫結需要長時間評估，則在較高優先權繫結順利傳回值之前，會先使用下一個順利傳回值的最高優先權。  
  
## 範例  
 為了示範 <xref:System.Windows.Data.PriorityBinding> 的運作方式，已建立具有下列三個屬性的 `AsyncDataSource` 物件：`FastDP`、`SlowerDP` 和 `SlowestDP`。  
  
 `FastDP` 的 get 存取子 \(Accessor\) 會傳回 `_fastDP` 資料成員的值。  
  
 `SlowerDP` 的 get 存取子會先等待 3 秒，再傳回 `_slowerDP` 資料成員的值。  
  
 `SlowestDP` 的 get 存取子會先等待 5 秒，再傳回 `_slowestDP` 資料成員的值。  
  
> [!NOTE]
>  這個範例僅供示範使用。  [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] 方針建議不要定義數量級低於欄位集的屬性。  如需詳細資訊，請參閱 [NIB: Choosing Between Properties and Methods](http://msdn.microsoft.com/zh-tw/55825e8f-7e2e-448a-9505-7217cc91b1af)。  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <xref:System.Windows.Controls.TextBlock.Text%2A> 屬性會繫結至上面使用 <xref:System.Windows.Data.PriorityBinding> 的 `AsyncDS`：  
  
 [!code-xml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 當繫結引擎處理 <xref:System.Windows.Data.Binding> 物件時，是從繫結至 `SlowestDP` 屬性的第一個 <xref:System.Windows.Data.Binding> 開始。  在處理這個 <xref:System.Windows.Data.Binding> 時，因為它會休眠 5 秒，所以並不會順利傳回值，因此會處理下一個 <xref:System.Windows.Data.Binding> 項目。  又因為下一個 <xref:System.Windows.Data.Binding> 會休眠 3 秒，所以並不會順利傳回值。  繫結引擎接著會移至下一個繫結至 `FastDP` 屬性的 <xref:System.Windows.Data.Binding> 項目。  這個 <xref:System.Windows.Data.Binding> 會傳回 "Fast Value" 值。  <xref:System.Windows.Controls.TextBlock> 現在會顯示 "Fast Value" 值。  
  
 而經過 3 秒之後，`SlowerDP` 屬性傳回 "Slower Value" 值。  <xref:System.Windows.Controls.TextBlock> 則會顯示 "Slower Value" 值。  
  
 而經過 5 秒之後，`SlowestDP` 屬性傳回 "Slowest Value" 值。  該繫結由於列在最前面，所以具有最高優先權。  <xref:System.Windows.Controls.TextBlock> 現在會顯示 "Slowest Value" 值。  
  
 如需視為繫結之成功傳回值的詳細資訊，請參閱 <xref:System.Windows.Data.PriorityBinding>。  
  
## 請參閱  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=fullName>   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)