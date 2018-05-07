---
title: 如何：指定超連結是否要加上底線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
ms.openlocfilehash: 3d57039d959aa63c031ef467cd2f8398fc3ffd96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a>如何：指定超連結是否要加上底線
<xref:System.Windows.Documents.Hyperlink>物件是可讓您將主機動態內容內的超連結的內嵌層級流動內容項目。 根據預設，<xref:System.Windows.Documents.Hyperlink>使用<xref:System.Windows.TextDecoration>物件，以顯示底線。 <xref:System.Windows.TextDecoration> 物件可以是具現化，耗用的效能，特別是如果您有許多<xref:System.Windows.Documents.Hyperlink>物件。 若要大量使用<xref:System.Windows.Documents.Hyperlink>項目，您可能要考慮這類觸發事件時，才顯示底線<xref:System.Windows.ContentElement.MouseEnter>事件。  
  
 在下列範例中，"My MSN 」 連結的底線是動態的它只會<xref:System.Windows.ContentElement.MouseEnter>觸發事件。  
  
 ![顯示 Textdecoration 的超連結](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
定義與 Textdecoration 的超連結  
  
## <a name="example"></a>範例  
 下列的標記範例示範<xref:System.Windows.Documents.Hyperlink>定義逾時或無底線：  
  
 [!code-xaml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 下列程式碼範例示範如何建立的底線<xref:System.Windows.Documents.Hyperlink>上<xref:System.Windows.ContentElement.MouseEnter>事件，並將它移除上<xref:System.Windows.ContentElement.MouseLeave>事件。  
  
 [!code-csharp[Performance#PerformanceSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [建立文字裝飾](../../../../docs/framework/wpf/advanced/how-to-create-a-text-decoration.md)
