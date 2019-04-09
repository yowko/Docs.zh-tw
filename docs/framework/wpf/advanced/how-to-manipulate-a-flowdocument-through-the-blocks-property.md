---
title: HOW TO：透過 Blocks 屬性管理 FlowDocument
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'documents [WPF], manipulating FlowDocuments through Blocks property [WPF], , '
- ', '
ms.assetid: cbb7291e-3f1b-433e-9e16-f4d93ced14e8
ms.openlocfilehash: c307d85bf24e2d8a20226856181e0758758d40c0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130880"
---
# <a name="how-to-manipulate-a-flowdocument-through-the-blocks-property"></a>HOW TO：透過 Blocks 屬性管理 FlowDocument
這些範例會展示一些較常見的作業，可對<xref:System.Windows.Documents.FlowDocument>透過<xref:System.Windows.Documents.FlowDocument.Blocks%2A>屬性。  
  
## <a name="example"></a>範例  
 下列範例會建立新<xref:System.Windows.Documents.FlowDocument>，然後附加新<xref:System.Windows.Documents.Paragraph>項目<xref:System.Windows.Documents.FlowDocument>。  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksadd)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksadd)]  
  
## <a name="example"></a>範例  
 下列範例會建立新<xref:System.Windows.Documents.Paragraph>項目，並將它插入開頭<xref:System.Windows.Documents.FlowDocument>。  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksinsert)]  
  
## <a name="example"></a>範例  
 下列範例會取得最上層的數目<xref:System.Windows.Documents.Block>中所包含的項目<xref:System.Windows.Documents.FlowDocument>。  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksCount](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblockscount)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksCount](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblockscount)]  
  
## <a name="example"></a>範例  
 下列範例會刪除最後一個<xref:System.Windows.Documents.Block>中的項目<xref:System.Windows.Documents.FlowDocument>。  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksremovelast)]  
  
## <a name="example"></a>範例  
 下列範例會清除所有內容 (<xref:System.Windows.Documents.Block>項目) 從<xref:System.Windows.Documents.FlowDocument>。  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksClear](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksclear)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksclear)]  
  
## <a name="see-also"></a>另請參閱

- [透過 RowGroups 屬性管理資料表的資料列群組](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [透過 Columns 屬性管理資料表的資料行](how-to-manipulate-table-columns-through-the-columns-property.md)
- [透過 RowGroups 屬性管理資料表的資料列群組](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
