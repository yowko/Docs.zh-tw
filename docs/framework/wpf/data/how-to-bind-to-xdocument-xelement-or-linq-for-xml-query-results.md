---
title: "如何：繫結至 XML 查詢結果的 XDocument、XElement 或 LINQ | Microsoft Docs"
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
  - "資料繫結 [WPF], 繫結至 XDocument"
  - "資料繫結 [WPF], 繫結至 XElement"
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# 如何：繫結至 XML 查詢結果的 XDocument、XElement 或 LINQ
在下列範例中，會示範如何使用 <xref:System.Xml.Linq.XDocument> 將 XML 資料繫結至 <xref:System.Windows.Controls.ItemsControl>。  
  
## 範例  
 下列 XAML 程式碼會定義 <xref:System.Windows.Controls.ItemsControl>，並將 `Planet` 型別之資料的資料樣板 \(Template\) 包含在 `http://planetsNS` XML 命名空間 \(Namespace\) 中。  佔用命名空間的 XML 資料型別必須將命名空間包含在括號內，而且如果此型別出現 XAML 標記延伸可能出現的位置，則它必須在命名空間前面加上括號逸出序列 \(Escape Sequence\)。  這個程式碼會繫結至與 <xref:System.Xml.Linq.XElement> 類別 \(Class\) 的 <xref:System.Xml.Linq.XContainer.Element%2A> 和 <xref:System.Xml.Linq.XElement.Attribute%2A> 方法對應的動態屬性。  動態屬性 \(Property\) 能讓 XAML 繫結至共用方法名稱的動態屬性 \(Property\)。  若要了解詳細資訊，請參閱 [LINQ to XML 動態屬性](../Topic/LINQ%20to%20XML%20Dynamic%20Properties.md)。  請注意 XML 的預設命名空間宣告不適用於屬性 \(Attribute\) 名稱的方式。  
  
 [!code-xml[XLinqExample#StackPanelResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xml[XLinqExample#ItemsControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 下列 C\# 程式碼會呼叫 <xref:System.Xml.Linq.XDocument.Load%2A>，並將堆疊面板資料內容設定為 `http://planetsNS` XML 命名空間中名為 `SolarSystemPlanets` 之項目的所有子項目。  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 使用 <xref:System.Windows.Data.ObjectDataProvider> 可以將 XML 資料儲存成 XAML 資源。  如需完整的範例，請參閱 [L2DBForm.xaml 原始程式碼](../Topic/L2DBForm.xaml%20Source%20Code.md)。  在下列範例中，會示範程式碼如何將資料內容設定為物件資源。  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 與 <xref:System.Xml.Linq.XContainer.Element%2A> 和 <xref:System.Xml.Linq.XElement.Attribute%2A> 對應的動態屬性提供了 XAML 內的彈性。  您的程式碼也能繫結至 LINQ for XML 查詢的結果。  這個範例會繫結至依項目值排序的查詢結果。  
  
 [!code-csharp[XLinqExample#BindToResults](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## 請參閱  
 [繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)   
 [使用 LINQ to XML 進行 WPF 資料繫結概觀](../Topic/WPF%20Data%20Binding%20with%20LINQ%20to%20XML%20Overview.md)   
 [使用 LINQ to XML 進行 WPF 資料繫結範例](../Topic/WPF%20Data%20Binding%20Using%20LINQ%20to%20XML%20Example.md)   
 [LINQ to XML 動態屬性](../Topic/LINQ%20to%20XML%20Dynamic%20Properties.md)