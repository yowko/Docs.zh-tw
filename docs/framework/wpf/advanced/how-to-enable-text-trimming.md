---
title: "如何：啟用文字修剪"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], trimming
- documents [WPF], trimmng text
- trimmng text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8f0f24bb6271e63dc50bd063aedfd8185711e7a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-enable-text-trimming"></a><span data-ttu-id="816dc-102">如何：啟用文字修剪</span><span class="sxs-lookup"><span data-stu-id="816dc-102">How to: Enable Text Trimming</span></span>
<span data-ttu-id="816dc-103">此範例示範的使用方式和中的可用值的效果<xref:System.Windows.TextTrimming>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="816dc-103">This example demonstrates the usage and effects of the values available in the <xref:System.Windows.TextTrimming> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="816dc-104">範例</span><span class="sxs-lookup"><span data-stu-id="816dc-104">Example</span></span>  
 <span data-ttu-id="816dc-105">下列範例會定義<xref:System.Windows.Controls.TextBlock>具有項目<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>屬性設定。</span><span class="sxs-lookup"><span data-stu-id="816dc-105">The following example defines a <xref:System.Windows.Controls.TextBlock> element with the <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> attribute set.</span></span>  
  
 [!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## <a name="example"></a><span data-ttu-id="816dc-106">範例</span><span class="sxs-lookup"><span data-stu-id="816dc-106">Example</span></span>  
 <span data-ttu-id="816dc-107">設定對應<xref:System.Windows.TextTrimming>程式碼中的屬性以下所示。</span><span class="sxs-lookup"><span data-stu-id="816dc-107">Setting the corresponding <xref:System.Windows.TextTrimming> property in code is demonstrated below.</span></span>  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 <span data-ttu-id="816dc-108">目前三個選項的修剪文字： **CharacterEllipsis**， **WordEllipsis**，和**無**。</span><span class="sxs-lookup"><span data-stu-id="816dc-108">There are currently three options for trimming text: **CharacterEllipsis**, **WordEllipsis**, and **None**.</span></span>  
  
 <span data-ttu-id="816dc-109">當<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>設**CharacterEllipsis**，修剪文字，再繼續使用省略符號在最接近的修剪邊緣的字元。</span><span class="sxs-lookup"><span data-stu-id="816dc-109">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **CharacterEllipsis**, text is trimmed and continued with an ellipsis at the character closest to the trimming edge.</span></span>  <span data-ttu-id="816dc-110">此設定是要修剪文字，使其更接近修剪界限，但可能會導致部分修剪文字。</span><span class="sxs-lookup"><span data-stu-id="816dc-110">This setting tends to trim text to fit more closely to the trimming boundary, but may result in words being partially trimmed.</span></span>  <span data-ttu-id="816dc-111">下圖顯示這項設定的效果<xref:System.Windows.Controls.TextBlock>類似於上述定義的一個。</span><span class="sxs-lookup"><span data-stu-id="816dc-111">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="816dc-112">![範例：TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")</span><span class="sxs-lookup"><span data-stu-id="816dc-112">![Example: TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")</span></span>  
  
 <span data-ttu-id="816dc-113">當<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>設**WordEllipsis**，修剪文字，再繼續使用省略符號的修剪邊緣最接近的第一個完整單字的結尾。</span><span class="sxs-lookup"><span data-stu-id="816dc-113">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **WordEllipsis**, text is trimmed and continued with an ellipsis at the end of the first full word closest to the trimming edge.</span></span>  <span data-ttu-id="816dc-114">此設定不會顯示部分修剪的文字的方式，但通常不是要修剪文字十分接近，修剪邊緣做為**CharacterEllipsis**設定。</span><span class="sxs-lookup"><span data-stu-id="816dc-114">This setting will not show partially trimmed words, but tends not to trim text as closely to the trimming edge as the **CharacterEllipsis** setting.</span></span>  <span data-ttu-id="816dc-115">下圖顯示這項設定的效果<xref:System.Windows.Controls.TextBlock>上面定義。</span><span class="sxs-lookup"><span data-stu-id="816dc-115">The following figure shows the effect of this setting on the <xref:System.Windows.Controls.TextBlock> defined above.</span></span>  
  
 <span data-ttu-id="816dc-116">![範例：TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")</span><span class="sxs-lookup"><span data-stu-id="816dc-116">![Example: TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")</span></span>  
  
 <span data-ttu-id="816dc-117">當<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>設**無**，會執行任何的文字修剪。</span><span class="sxs-lookup"><span data-stu-id="816dc-117">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **None**, no text trimming is performed.</span></span>  <span data-ttu-id="816dc-118">在此情況下，只會將文字裁剪到父文字容器的界限。</span><span class="sxs-lookup"><span data-stu-id="816dc-118">In this case, text is simply cropped to the boundary of the parent text container.</span></span>  <span data-ttu-id="816dc-119">下圖顯示這項設定的效果<xref:System.Windows.Controls.TextBlock>類似於上述定義的一個。</span><span class="sxs-lookup"><span data-stu-id="816dc-119">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="816dc-120">![範例：TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")</span><span class="sxs-lookup"><span data-stu-id="816dc-120">![Example: TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")</span></span>
