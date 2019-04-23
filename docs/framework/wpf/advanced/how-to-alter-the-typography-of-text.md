---
title: 操作說明：修改文字的印刷樣式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- setting Typography attributes [WPF]
- Typography attribute [WPF], setting
ms.assetid: 19a3b49b-60a2-4c11-a786-e26b4c965588
ms.openlocfilehash: 4c027424632f8671ba8d7cae1c899ef3a53edc26
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078859"
---
# <a name="how-to-alter-the-typography-of-text"></a><span data-ttu-id="88fde-102">操作說明：修改文字的印刷樣式</span><span class="sxs-lookup"><span data-stu-id="88fde-102">How-to: Alter the Typography of Text</span></span>
<span data-ttu-id="88fde-103">下列範例示範如何設定<xref:System.Windows.Documents.TextElement.Typography%2A>屬性，使用<xref:System.Windows.Documents.Paragraph>做為範例項目。</span><span class="sxs-lookup"><span data-stu-id="88fde-103">The following example shows how to set the <xref:System.Windows.Documents.TextElement.Typography%2A> attribute, using <xref:System.Windows.Documents.Paragraph> as the example element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88fde-104">範例</span><span class="sxs-lookup"><span data-stu-id="88fde-104">Example</span></span>  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 <span data-ttu-id="88fde-105">下圖顯示此範例的轉譯方式。</span><span class="sxs-lookup"><span data-stu-id="88fde-105">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="88fde-106">![螢幕擷取畫面：印刷樣式的文字](./media/textelement-typog.png "TextElement_Typog")</span><span class="sxs-lookup"><span data-stu-id="88fde-106">![Screenshot: Text with altered typography](./media/textelement-typog.png "TextElement_Typog")</span></span>  
  
 <span data-ttu-id="88fde-107">相反地，下圖顯示如何轉譯套用預設印刷樣式屬性的類似範例。</span><span class="sxs-lookup"><span data-stu-id="88fde-107">In contrast, the following figure shows how a similar example with default typographic properties renders.</span></span>  
  
 <span data-ttu-id="88fde-108">![螢幕擷取畫面：印刷樣式的文字](./media/textelement-typog-default.png "TextElement_Typog_Default")</span><span class="sxs-lookup"><span data-stu-id="88fde-108">![Screenshot: Text with altered typography](./media/textelement-typog-default.png "TextElement_Typog_Default")</span></span>  
  
## <a name="example"></a><span data-ttu-id="88fde-109">範例</span><span class="sxs-lookup"><span data-stu-id="88fde-109">Example</span></span>  
 <span data-ttu-id="88fde-110">下列範例示範如何設定<xref:System.Windows.Controls.TextBox.Typography%2A>屬性以程式設計的方式。</span><span class="sxs-lookup"><span data-stu-id="88fde-110">The following example shows how to set the <xref:System.Windows.Controls.TextBox.Typography%2A> property programmatically.</span></span>  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
## <a name="see-also"></a><span data-ttu-id="88fde-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88fde-111">See also</span></span>

- [<span data-ttu-id="88fde-112">非固定格式文件概觀</span><span class="sxs-lookup"><span data-stu-id="88fde-112">Flow Document Overview</span></span>](flow-document-overview.md)
