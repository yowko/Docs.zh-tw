---
title: HOW TO：指定超連結是否要加上底線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
ms.openlocfilehash: 9e8eb54d4710095a1aba052b16e49c528bd17c0e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371034"
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a><span data-ttu-id="10b31-102">HOW TO：指定超連結是否要加上底線</span><span class="sxs-lookup"><span data-stu-id="10b31-102">How to: Specify Whether a Hyperlink is Underlined</span></span>
<span data-ttu-id="10b31-103"><xref:System.Windows.Documents.Hyperlink>物件是內嵌層級非固定格式內容項目，可讓您將非固定格式內容內超連結。</span><span class="sxs-lookup"><span data-stu-id="10b31-103">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="10b31-104">根據預設，<xref:System.Windows.Documents.Hyperlink>使用<xref:System.Windows.TextDecoration>物件，以顯示底線。</span><span class="sxs-lookup"><span data-stu-id="10b31-104">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="10b31-105"><xref:System.Windows.TextDecoration> 物件可以具現化，需要大量的效能，特別是如果您有許多<xref:System.Windows.Documents.Hyperlink>物件。</span><span class="sxs-lookup"><span data-stu-id="10b31-105"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="10b31-106">若要大量使用<xref:System.Windows.Documents.Hyperlink>項目，您可能要考慮這類觸發事件時，才顯示底線<xref:System.Windows.ContentElement.MouseEnter>事件。</span><span class="sxs-lookup"><span data-stu-id="10b31-106">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="10b31-107">在下列範例中，「 我的 MSN 」 連結，底線是動態的它才會出現<xref:System.Windows.ContentElement.MouseEnter>觸發事件。</span><span class="sxs-lookup"><span data-stu-id="10b31-107">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 <span data-ttu-id="10b31-108">![顯示 Textdecoration 的超](./media/textdecoration03.png "TextDecoration03")</span><span class="sxs-lookup"><span data-stu-id="10b31-108">![Hyperlinks displaying TextDecorations](./media/textdecoration03.png "TextDecoration03")</span></span>  
<span data-ttu-id="10b31-109">定義與 Textdecoration 的超連結</span><span class="sxs-lookup"><span data-stu-id="10b31-109">Hyperlinks defined with TextDecorations</span></span>  
  
## <a name="example"></a><span data-ttu-id="10b31-110">範例</span><span class="sxs-lookup"><span data-stu-id="10b31-110">Example</span></span>  
 <span data-ttu-id="10b31-111">下列標記範例示範<xref:System.Windows.Documents.Hyperlink>定義不含底線與：</span><span class="sxs-lookup"><span data-stu-id="10b31-111">The following markup sample shows a <xref:System.Windows.Documents.Hyperlink> defined with and without an underline:</span></span>  
  
 [!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 <span data-ttu-id="10b31-112">下列程式碼範例示範如何建立如底線<xref:System.Windows.Documents.Hyperlink>上<xref:System.Windows.ContentElement.MouseEnter>事件，並將它移除上<xref:System.Windows.ContentElement.MouseLeave>事件。</span><span class="sxs-lookup"><span data-stu-id="10b31-112">The following code sample shows how to create an underline for the <xref:System.Windows.Documents.Hyperlink> on the <xref:System.Windows.ContentElement.MouseEnter> event, and remove it on the <xref:System.Windows.ContentElement.MouseLeave> event.</span></span>  
  
 [!code-csharp[Performance#PerformanceSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a><span data-ttu-id="10b31-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10b31-113">See also</span></span>
- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [<span data-ttu-id="10b31-114">最佳化 WPF 應用程式效能</span><span class="sxs-lookup"><span data-stu-id="10b31-114">Optimizing WPF Application Performance</span></span>](optimizing-wpf-application-performance.md)
- [<span data-ttu-id="10b31-115">建立文字裝飾</span><span class="sxs-lookup"><span data-stu-id="10b31-115">Create a Text Decoration</span></span>](how-to-create-a-text-decoration.md)
