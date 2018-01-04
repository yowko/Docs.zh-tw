---
title: "如何：使用 XAML 定義資料表"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b932c7df822edabc5626f20af2bfc1eb3a7f93ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-table-with-xaml"></a>如何：使用 XAML 定義資料表
下列範例示範如何定義<xref:System.Windows.Documents.Table>使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。  範例資料表有四個資料行 (由<xref:System.Windows.Documents.TableColumn>項目) 和數個資料列 (由<xref:System.Windows.Documents.TableRow>項目) 包含資料以及做為標題、 頁首和頁尾資訊。  資料列都必須包含在<xref:System.Windows.Documents.TableRowGroup>項目。  資料表中的每個資料列組成一或多個資料格 (由<xref:System.Windows.Documents.TableCell>項目)。  表格儲存格的內容必須包含在<xref:System.Windows.Documents.Block>項目; 在此情況下<xref:System.Windows.Documents.Paragraph>使用項目。  資料表也會裝載超連結 (由<xref:System.Windows.Documents.Hyperlink>項目) 中頁尾資料列。  
  
## <a name="example"></a>範例  
 [!code-xaml[TableSnippetsXAML#_TableXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 下圖顯示此範例中所定義之資料表的轉譯方式。  
  
 ![轉譯的資料表。](../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")
