---
title: 如何：使用 XAML 定義資料表
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
ms.openlocfilehash: 2a35a27567d962fc125cb3c408ccab95afa222af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543097"
---
# <a name="how-to-define-a-table-with-xaml"></a><span data-ttu-id="2a5cb-102">如何：使用 XAML 定義資料表</span><span class="sxs-lookup"><span data-stu-id="2a5cb-102">How to: Define a Table with XAML</span></span>
<span data-ttu-id="2a5cb-103">下列範例示範如何定義<xref:System.Windows.Documents.Table>使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2a5cb-103">The following example demonstrates how to define a <xref:System.Windows.Documents.Table> using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  <span data-ttu-id="2a5cb-104">範例資料表有四個資料行 (由<xref:System.Windows.Documents.TableColumn>項目) 和數個資料列 (由<xref:System.Windows.Documents.TableRow>項目) 包含資料以及做為標題、 頁首和頁尾資訊。</span><span class="sxs-lookup"><span data-stu-id="2a5cb-104">The example table has four columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and several rows (represented by <xref:System.Windows.Documents.TableRow> elements) containing data as well as title, header, and footer information.</span></span>  <span data-ttu-id="2a5cb-105">資料列都必須包含在<xref:System.Windows.Documents.TableRowGroup>項目。</span><span class="sxs-lookup"><span data-stu-id="2a5cb-105">Rows must be contained in a <xref:System.Windows.Documents.TableRowGroup> element.</span></span>  <span data-ttu-id="2a5cb-106">資料表中的每個資料列組成一或多個資料格 (由<xref:System.Windows.Documents.TableCell>項目)。</span><span class="sxs-lookup"><span data-stu-id="2a5cb-106">Each row in the table is comprised of one or more cells (represented by <xref:System.Windows.Documents.TableCell> elements).</span></span>  <span data-ttu-id="2a5cb-107">表格儲存格的內容必須包含在<xref:System.Windows.Documents.Block>項目; 在此情況下<xref:System.Windows.Documents.Paragraph>使用項目。</span><span class="sxs-lookup"><span data-stu-id="2a5cb-107">Content in a table cell must be contained in a <xref:System.Windows.Documents.Block> element; in this case <xref:System.Windows.Documents.Paragraph> elements are used.</span></span>  <span data-ttu-id="2a5cb-108">資料表也會裝載超連結 (由<xref:System.Windows.Documents.Hyperlink>項目) 中頁尾資料列。</span><span class="sxs-lookup"><span data-stu-id="2a5cb-108">The table also hosts a hyperlink (represented by the <xref:System.Windows.Documents.Hyperlink> element) in the footer row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a5cb-109">範例</span><span class="sxs-lookup"><span data-stu-id="2a5cb-109">Example</span></span>  
 [!code-xaml[TableSnippetsXAML#_TableXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 <span data-ttu-id="2a5cb-110">下圖顯示此範例中所定義之資料表的轉譯方式。</span><span class="sxs-lookup"><span data-stu-id="2a5cb-110">The following figure shows how the table defined in this example renders.</span></span>  
  
 <span data-ttu-id="2a5cb-111">![轉譯的資料表。](../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")</span><span class="sxs-lookup"><span data-stu-id="2a5cb-111">![Rendered table.](../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")</span></span>
