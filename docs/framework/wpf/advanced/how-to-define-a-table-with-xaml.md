---
title: "如何：使用 XAML 定義資料表 | Microsoft Docs"
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
  - "文件, 使用 XAML 定義資料表"
  - "資料表, 使用 XAML 定義"
  - "XAML, 定義資料表"
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：使用 XAML 定義資料表
下列範例示範如何使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 定義 <xref:System.Windows.Documents.Table>。  範例資料表中包含四個資料行 \(以 <xref:System.Windows.Documents.TableColumn> 項目表示\) 與數個資料列 \(以 <xref:System.Windows.Documents.TableRow> 項目表示\)，內含資料以及標題、頁首與頁尾資訊。  資料列必須包含於 <xref:System.Windows.Documents.TableRowGroup> 項目中。  資料表中的每個資料列各包含一個或多個儲存格 \(以 <xref:System.Windows.Documents.TableCell> 項目表示\)。  資料表儲存格中的內容必須包含在 <xref:System.Windows.Documents.Block> 項目中，在這個案例中會使用 <xref:System.Windows.Documents.Paragraph> 項目。  資料表也會在頁尾資料列中裝載超連結 \(以 <xref:System.Windows.Documents.Hyperlink> 項目表示\)。  
  
## 範例  
 [!code-xml[TableSnippetsXAML#_TableXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 下圖顯示這個範例所定義之資料表的外觀。  
  
 ![所呈現的資料表。](../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")