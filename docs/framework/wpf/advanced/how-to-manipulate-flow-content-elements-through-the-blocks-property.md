---
title: HOW TO：透過 Blocks 屬性管理動態內容項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], manipulating flow content elements through Blocks property
- flow content elements [WPF], manipulating through Blocks property
- properties [WPF], Blocks [WPF], manipulating flow content elements
- Blocks property [WPF], manipulating flow content elements
ms.assetid: aeda4ece-b979-4818-a093-ef938e908751
ms.openlocfilehash: e0e1e1333a54946f3bdf474e353de0301eb42447
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150133"
---
# <a name="how-to-manipulate-flow-content-elements-through-the-blocks-property"></a>HOW TO：透過 Blocks 屬性管理動態內容項目
這些範例會展示一些較常見可透過非固定格式內容的項目執行的作業**區塊**屬性。 這個屬性用來新增和移除項目從<xref:System.Windows.Documents.BlockCollection>。 非固定格式內容項目該功能**區塊**屬性包括：  
  
-   <xref:System.Windows.Documents.Figure>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.ListItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
 這些範例會使用<xref:System.Windows.Documents.Section>為非固定格式內容項目，但這些技術都適用於裝載非固定格式內容項目集合的所有項目。  
  
## <a name="example"></a>範例  
 下列範例會建立新<xref:System.Windows.Documents.Section>，然後使用**新增**方法來加入至新的段落**一節**內容。  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
## <a name="example"></a>範例  
 下列範例會建立新<xref:System.Windows.Documents.Paragraph>項目，並將它插入開頭<xref:System.Windows.Documents.Section>。  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksinsert)]  
  
## <a name="example"></a>範例  
 下列範例會取得最上層的數目<xref:System.Windows.Documents.Block>中所包含的項目<xref:System.Windows.Documents.Section>。  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksCount](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblockscount)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksCount](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblockscount)]  
  
## <a name="example"></a>範例  
 下列範例會刪除最後一個<xref:System.Windows.Documents.Block>中的項目<xref:System.Windows.Documents.Section>。  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksremovelast)]  
  
## <a name="example"></a>範例  
 下列範例會清除所有內容 (<xref:System.Windows.Documents.Block>項目) 從<xref:System.Windows.Documents.Section>。  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksClear](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksclear)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksclear)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Documents.BlockCollection>
- <xref:System.Windows.Documents.InlineCollection>
- <xref:System.Windows.Documents.ListItemCollection>
- [非固定格式文件概觀](flow-document-overview.md)
- [透過 RowGroups 屬性管理資料表的資料列群組](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [透過 Columns 屬性管理資料表的資料行](how-to-manipulate-table-columns-through-the-columns-property.md)
- [透過 RowGroups 屬性管理資料表的資料列群組](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
