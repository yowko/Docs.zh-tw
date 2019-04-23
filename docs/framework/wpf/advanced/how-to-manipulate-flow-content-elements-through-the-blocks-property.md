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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150133"
---
# <a name="how-to-manipulate-flow-content-elements-through-the-blocks-property"></a><span data-ttu-id="6c2f0-102">HOW TO：透過 Blocks 屬性管理動態內容項目</span><span class="sxs-lookup"><span data-stu-id="6c2f0-102">How to: Manipulate Flow Content Elements through the Blocks Property</span></span>
<span data-ttu-id="6c2f0-103">這些範例會展示一些較常見可透過非固定格式內容的項目執行的作業**區塊**屬性。</span><span class="sxs-lookup"><span data-stu-id="6c2f0-103">These examples demonstrate some of the more common operations that can be performed on flow content elements through the **Blocks** property.</span></span> <span data-ttu-id="6c2f0-104">這個屬性用來新增和移除項目從<xref:System.Windows.Documents.BlockCollection>。</span><span class="sxs-lookup"><span data-stu-id="6c2f0-104">This property is used to add and remove items from <xref:System.Windows.Documents.BlockCollection>.</span></span> <span data-ttu-id="6c2f0-105">非固定格式內容項目該功能**區塊**屬性包括：</span><span class="sxs-lookup"><span data-stu-id="6c2f0-105">Flow content elements that feature a **Blocks** property include:</span></span>  
  
-   <xref:System.Windows.Documents.Figure>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.ListItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="6c2f0-106">這些範例會使用<xref:System.Windows.Documents.Section>為非固定格式內容項目，但這些技術都適用於裝載非固定格式內容項目集合的所有項目。</span><span class="sxs-lookup"><span data-stu-id="6c2f0-106">These examples happen to use <xref:System.Windows.Documents.Section> as the flow content element, but these techniques are applicable to all elements that host a flow content element collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c2f0-107">範例</span><span class="sxs-lookup"><span data-stu-id="6c2f0-107">Example</span></span>  
 <span data-ttu-id="6c2f0-108">下列範例會建立新<xref:System.Windows.Documents.Section>，然後使用**新增**方法來加入至新的段落**一節**內容。</span><span class="sxs-lookup"><span data-stu-id="6c2f0-108">The following example creates a new <xref:System.Windows.Documents.Section> and then uses the **Add** method to add a new Paragraph to the **Section** contents.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
## <a name="example"></a><span data-ttu-id="6c2f0-109">範例</span><span class="sxs-lookup"><span data-stu-id="6c2f0-109">Example</span></span>  
 <span data-ttu-id="6c2f0-110">下列範例會建立新<xref:System.Windows.Documents.Paragraph>項目，並將它插入開頭<xref:System.Windows.Documents.Section>。</span><span class="sxs-lookup"><span data-stu-id="6c2f0-110">The following example creates a new <xref:System.Windows.Documents.Paragraph> element and inserts it at the beginning of the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksinsert)]  
  
## <a name="example"></a><span data-ttu-id="6c2f0-111">範例</span><span class="sxs-lookup"><span data-stu-id="6c2f0-111">Example</span></span>  
 <span data-ttu-id="6c2f0-112">下列範例會取得最上層的數目<xref:System.Windows.Documents.Block>中所包含的項目<xref:System.Windows.Documents.Section>。</span><span class="sxs-lookup"><span data-stu-id="6c2f0-112">The following example gets the number of top-level <xref:System.Windows.Documents.Block> elements contained in the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksCount](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblockscount)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksCount](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblockscount)]  
  
## <a name="example"></a><span data-ttu-id="6c2f0-113">範例</span><span class="sxs-lookup"><span data-stu-id="6c2f0-113">Example</span></span>  
 <span data-ttu-id="6c2f0-114">下列範例會刪除最後一個<xref:System.Windows.Documents.Block>中的項目<xref:System.Windows.Documents.Section>。</span><span class="sxs-lookup"><span data-stu-id="6c2f0-114">The following example deletes the last <xref:System.Windows.Documents.Block> element in the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksremovelast)]  
  
## <a name="example"></a><span data-ttu-id="6c2f0-115">範例</span><span class="sxs-lookup"><span data-stu-id="6c2f0-115">Example</span></span>  
 <span data-ttu-id="6c2f0-116">下列範例會清除所有內容 (<xref:System.Windows.Documents.Block>項目) 從<xref:System.Windows.Documents.Section>。</span><span class="sxs-lookup"><span data-stu-id="6c2f0-116">The following example clears all of the contents (<xref:System.Windows.Documents.Block> elements) from the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksClear](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksclear)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksclear)]  
  
## <a name="see-also"></a><span data-ttu-id="6c2f0-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c2f0-117">See also</span></span>

- <xref:System.Windows.Documents.BlockCollection>
- <xref:System.Windows.Documents.InlineCollection>
- <xref:System.Windows.Documents.ListItemCollection>
- [<span data-ttu-id="6c2f0-118">非固定格式文件概觀</span><span class="sxs-lookup"><span data-stu-id="6c2f0-118">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="6c2f0-119">透過 RowGroups 屬性管理表格的資料列群組</span><span class="sxs-lookup"><span data-stu-id="6c2f0-119">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="6c2f0-120">透過 Columns 屬性管理表格的資料行</span><span class="sxs-lookup"><span data-stu-id="6c2f0-120">Manipulate a Table's Columns through the Columns Property</span></span>](how-to-manipulate-table-columns-through-the-columns-property.md)
- [<span data-ttu-id="6c2f0-121">透過 RowGroups 屬性管理表格的資料列群組</span><span class="sxs-lookup"><span data-stu-id="6c2f0-121">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
