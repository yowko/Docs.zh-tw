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
ms.openlocfilehash: f04c873e542ad02c1d2a20b770ded4464af7a6d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645401"
---
# <a name="how-to-alter-the-typography-of-text"></a><span data-ttu-id="05dd0-102">操作說明：修改文字的印刷樣式</span><span class="sxs-lookup"><span data-stu-id="05dd0-102">How-to: Alter the Typography of Text</span></span>
<span data-ttu-id="05dd0-103">下列範例示範如何設定<xref:System.Windows.Documents.TextElement.Typography%2A>屬性，使用<xref:System.Windows.Documents.Paragraph>做為範例項目。</span><span class="sxs-lookup"><span data-stu-id="05dd0-103">The following example shows how to set the <xref:System.Windows.Documents.TextElement.Typography%2A> attribute, using <xref:System.Windows.Documents.Paragraph> as the example element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05dd0-104">範例</span><span class="sxs-lookup"><span data-stu-id="05dd0-104">Example</span></span>  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 <span data-ttu-id="05dd0-105">下圖顯示此範例的轉譯方式。</span><span class="sxs-lookup"><span data-stu-id="05dd0-105">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="05dd0-106">![螢幕擷取畫面：印刷樣式的文字](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement_Typog")</span><span class="sxs-lookup"><span data-stu-id="05dd0-106">![Screenshot: Text with altered typography](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement_Typog")</span></span>  
  
 <span data-ttu-id="05dd0-107">相反地，下圖顯示如何轉譯套用預設印刷樣式屬性的類似範例。</span><span class="sxs-lookup"><span data-stu-id="05dd0-107">In contrast, the following figure shows how a similar example with default typographic properties renders.</span></span>  
  
 <span data-ttu-id="05dd0-108">![螢幕擷取畫面：印刷樣式的文字](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement_Typog_Default")</span><span class="sxs-lookup"><span data-stu-id="05dd0-108">![Screenshot: Text with altered typography](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement_Typog_Default")</span></span>  
  
## <a name="example"></a><span data-ttu-id="05dd0-109">範例</span><span class="sxs-lookup"><span data-stu-id="05dd0-109">Example</span></span>  
 <span data-ttu-id="05dd0-110">下列範例示範如何設定<xref:System.Windows.Controls.TextBox.Typography%2A>屬性以程式設計的方式。</span><span class="sxs-lookup"><span data-stu-id="05dd0-110">The following example shows how to set the <xref:System.Windows.Controls.TextBox.Typography%2A> property programmatically.</span></span>  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
## <a name="see-also"></a><span data-ttu-id="05dd0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05dd0-111">See also</span></span>
- [<span data-ttu-id="05dd0-112">非固定格式文件概觀</span><span class="sxs-lookup"><span data-stu-id="05dd0-112">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)
