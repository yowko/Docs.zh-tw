---
title: HOW TO：使用 XAML 定義資料表
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
ms.openlocfilehash: 7398af6fddae56238e1af3ee4e726420c01ab7ea
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376919"
---
# <a name="how-to-define-a-table-with-xaml"></a>HOW TO：使用 XAML 定義資料表
下列範例示範如何定義<xref:System.Windows.Documents.Table>使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。  範例資料表有四個資料行 (由<xref:System.Windows.Documents.TableColumn>項目) 和數個資料列 (由<xref:System.Windows.Documents.TableRow>項目) 包含資料以及做為標題、 頁首與頁尾的資訊。  資料列都必須包含在<xref:System.Windows.Documents.TableRowGroup>項目。  在資料表中的每個資料列組成一或多個資料格 (由<xref:System.Windows.Documents.TableCell>項目)。  中的資料表資料格的內容必須包含在<xref:System.Windows.Documents.Block>項目; 在此情況下<xref:System.Windows.Documents.Paragraph>使用項目。  資料表也會裝載超連結 (由<xref:System.Windows.Documents.Hyperlink>項目) 中的頁尾資料列。  
  
## <a name="example"></a>範例  
 [!code-xaml[TableSnippetsXAML#_TableXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 下圖顯示此範例中所定義之資料表的轉譯方式。  
  
 ![轉譯的資料表。](./media/tableeg.png "TableEG")
