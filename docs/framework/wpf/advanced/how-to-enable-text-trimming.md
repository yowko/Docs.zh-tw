---
title: HOW TO：啟用文字修剪
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], trimming
- documents [WPF], trimmng text
- trimmng text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
ms.openlocfilehash: 367e1f46524d8135d8269a2e2159dfe7c2468c45
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354462"
---
# <a name="how-to-enable-text-trimming"></a><span data-ttu-id="bb4ea-102">HOW TO：啟用文字修剪</span><span class="sxs-lookup"><span data-stu-id="bb4ea-102">How to: Enable Text Trimming</span></span>
<span data-ttu-id="bb4ea-103">此範例示範使用方式和效果中的可用值<xref:System.Windows.TextTrimming>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="bb4ea-103">This example demonstrates the usage and effects of the values available in the <xref:System.Windows.TextTrimming> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb4ea-104">範例</span><span class="sxs-lookup"><span data-stu-id="bb4ea-104">Example</span></span>  
 <span data-ttu-id="bb4ea-105">下列範例會定義<xref:System.Windows.Controls.TextBlock>具有項目<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>屬性設定。</span><span class="sxs-lookup"><span data-stu-id="bb4ea-105">The following example defines a <xref:System.Windows.Controls.TextBlock> element with the <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> attribute set.</span></span>  
  
 [!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## <a name="example"></a><span data-ttu-id="bb4ea-106">範例</span><span class="sxs-lookup"><span data-stu-id="bb4ea-106">Example</span></span>  
 <span data-ttu-id="bb4ea-107">設定對應<xref:System.Windows.TextTrimming>在程式碼中的屬性以下所示。</span><span class="sxs-lookup"><span data-stu-id="bb4ea-107">Setting the corresponding <xref:System.Windows.TextTrimming> property in code is demonstrated below.</span></span>  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 <span data-ttu-id="bb4ea-108">目前三個選項可修剪文字：**CharacterEllipsis**， **WordEllipsis**，以及**None**。</span><span class="sxs-lookup"><span data-stu-id="bb4ea-108">There are currently three options for trimming text: **CharacterEllipsis**, **WordEllipsis**, and **None**.</span></span>  
  
 <span data-ttu-id="bb4ea-109">當<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>設定為**CharacterEllipsis**，會修剪文字，並繼續使用省略符號在最接近修剪邊緣的字元。</span><span class="sxs-lookup"><span data-stu-id="bb4ea-109">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **CharacterEllipsis**, text is trimmed and continued with an ellipsis at the character closest to the trimming edge.</span></span>  <span data-ttu-id="bb4ea-110">此設定是要修剪文字，使其更接近修剪界限，但可能會導致部分修剪文字。</span><span class="sxs-lookup"><span data-stu-id="bb4ea-110">This setting tends to trim text to fit more closely to the trimming boundary, but may result in words being partially trimmed.</span></span>  <span data-ttu-id="bb4ea-111">下圖顯示這項設定的效果<xref:System.Windows.Controls.TextBlock>類似上面所定義。</span><span class="sxs-lookup"><span data-stu-id="bb4ea-111">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="bb4ea-112">![例如：TextTrimming.CharacterEllipsis](./media/texttrimming-character.png "TextTrimming_Character")</span><span class="sxs-lookup"><span data-stu-id="bb4ea-112">![Example: TextTrimming.CharacterEllipsis](./media/texttrimming-character.png "TextTrimming_Character")</span></span>  
  
 <span data-ttu-id="bb4ea-113">當<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>設定為**WordEllipsis**，會修剪文字，並繼續使用最接近修剪邊緣的第一個完整文字結尾的省略符號。</span><span class="sxs-lookup"><span data-stu-id="bb4ea-113">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **WordEllipsis**, text is trimmed and continued with an ellipsis at the end of the first full word closest to the trimming edge.</span></span>  <span data-ttu-id="bb4ea-114">此設定不會顯示部分修剪的文字，但傾向不修剪的文字修剪邊緣**CharacterEllipsis**設定。</span><span class="sxs-lookup"><span data-stu-id="bb4ea-114">This setting will not show partially trimmed words, but tends not to trim text as closely to the trimming edge as the **CharacterEllipsis** setting.</span></span>  <span data-ttu-id="bb4ea-115">下圖顯示這項設定的效果<xref:System.Windows.Controls.TextBlock>上面所定義。</span><span class="sxs-lookup"><span data-stu-id="bb4ea-115">The following figure shows the effect of this setting on the <xref:System.Windows.Controls.TextBlock> defined above.</span></span>  
  
 <span data-ttu-id="bb4ea-116">![例如：TextTrimming.WordEllipsis](./media/texttrimming-word.png "TextTrimming_Word")</span><span class="sxs-lookup"><span data-stu-id="bb4ea-116">![Example: TextTrimming.WordEllipsis](./media/texttrimming-word.png "TextTrimming_Word")</span></span>  
  
 <span data-ttu-id="bb4ea-117">當<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>設定為**無**，會執行任何的文字修剪。</span><span class="sxs-lookup"><span data-stu-id="bb4ea-117">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **None**, no text trimming is performed.</span></span>  <span data-ttu-id="bb4ea-118">在此情況下，只會將文字裁剪到父文字容器的界限。</span><span class="sxs-lookup"><span data-stu-id="bb4ea-118">In this case, text is simply cropped to the boundary of the parent text container.</span></span>  <span data-ttu-id="bb4ea-119">下圖顯示這項設定的效果<xref:System.Windows.Controls.TextBlock>類似上面所定義。</span><span class="sxs-lookup"><span data-stu-id="bb4ea-119">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="bb4ea-120">![例如：TextTrimming.None](./media/texttrimming-none.png "TextTrimming_None")</span><span class="sxs-lookup"><span data-stu-id="bb4ea-120">![Example: TextTrimming.None](./media/texttrimming-none.png "TextTrimming_None")</span></span>
