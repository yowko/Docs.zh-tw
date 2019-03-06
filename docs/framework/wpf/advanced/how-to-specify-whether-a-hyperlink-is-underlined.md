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
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a>HOW TO：指定超連結是否要加上底線
<xref:System.Windows.Documents.Hyperlink>物件是內嵌層級非固定格式內容項目，可讓您將非固定格式內容內超連結。 根據預設，<xref:System.Windows.Documents.Hyperlink>使用<xref:System.Windows.TextDecoration>物件，以顯示底線。 <xref:System.Windows.TextDecoration> 物件可以具現化，需要大量的效能，特別是如果您有許多<xref:System.Windows.Documents.Hyperlink>物件。 若要大量使用<xref:System.Windows.Documents.Hyperlink>項目，您可能要考慮這類觸發事件時，才顯示底線<xref:System.Windows.ContentElement.MouseEnter>事件。  
  
 在下列範例中，「 我的 MSN 」 連結，底線是動態的它才會出現<xref:System.Windows.ContentElement.MouseEnter>觸發事件。  
  
 ![顯示 Textdecoration 的超](./media/textdecoration03.png "TextDecoration03")  
定義與 Textdecoration 的超連結  
  
## <a name="example"></a>範例  
 下列標記範例示範<xref:System.Windows.Documents.Hyperlink>定義不含底線與：  
  
 [!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 下列程式碼範例示範如何建立如底線<xref:System.Windows.Documents.Hyperlink>上<xref:System.Windows.ContentElement.MouseEnter>事件，並將它移除上<xref:System.Windows.ContentElement.MouseLeave>事件。  
  
 [!code-csharp[Performance#PerformanceSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [最佳化 WPF 應用程式效能](optimizing-wpf-application-performance.md)
- [建立文字裝飾](how-to-create-a-text-decoration.md)
