---
title: 如何：旋轉筆墨
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], rotating
- rotating ink [WPF]
ms.assetid: fac36cc9-dd01-41ca-9bde-9d33e3790bbe
ms.openlocfilehash: 51b06ec98b916a9f2f90a84b42007ef4c596ac60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-rotate-ink"></a>如何：旋轉筆墨
## <a name="example"></a>範例  
 下列範例會將複製的筆墨<xref:System.Windows.Controls.InkCanvas>至<xref:System.Windows.Controls.Canvas>包含<xref:System.Windows.Controls.InkPresenter>。  當應用程式複製筆墨時，它也會旋轉筆跡順時針旋轉 90 度。  
  
 [!code-xaml[HowToRotateInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRotateInk/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[HowToRotateInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRotateInk/CSharp/Window1.xaml.cs#2)]  
  
## <a name="example"></a>範例  
 下列範例為自訂<xref:System.Windows.Documents.Adorner>的上一個圖示旋轉筆劃<xref:System.Windows.Controls.InkPresenter>。  
  
 [!code-csharp[AdornerForStrokes#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/RotatingAdornerForStrokes.cs#1)]
 [!code-vb[AdornerForStrokes#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornerForStrokes/VisualBasic/RotatingAdornerForStrokes.vb#1)]  
  
 下列範例是[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案，可定義<xref:System.Windows.Controls.InkPresenter>並填入筆墨。 `Window_Loaded`事件處理常式會將自訂的裝飾項<xref:System.Windows.Controls.InkPresenter>。  
  
 [!code-xaml[AdornerForStrokes#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[AdornerForStrokes#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornerForStrokes/CSharp/Window1.xaml.cs#3)]
 [!code-vb[AdornerForStrokes#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornerForStrokes/VisualBasic/Window1.xaml.vb#3)]
