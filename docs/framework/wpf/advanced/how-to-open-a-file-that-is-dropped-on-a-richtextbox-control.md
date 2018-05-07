---
title: 如何：開啟置放在 RichTextBox 控制項上的檔案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], RichTextBox
- RichTextBox [WPF], drag-and-drop
- drag-and-drop [WPF], open a dropped file
ms.assetid: 6bb8bb54-f576-41db-a9a7-24102ddeb490
ms.openlocfilehash: f3c10ae76a9afcc04578c590cc57cd43c3ab7a1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>如何：開啟置放在 RichTextBox 控制項上的檔案
在[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、 <xref:System.Windows.Controls.TextBox>， <xref:System.Windows.Controls.RichTextBox>，和<xref:System.Windows.Documents.FlowDocument>控制項所有具有內建的拖放功能。 內建功能可讓拖放文字與控制項間。 不過，不會啟用拖放控制項上的檔案來開啟檔案。 這些控制項也標記為已處理拖放事件。 如此一來，根據預設，您無法加入您自己的事件處理常式，以提供的功能來開啟卸除的檔案。  
  
 若要新增這些控制項的拖放事件的額外處理，使用<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>方法，將您的事件處理常式的拖放事件。 設定`handledEventsToo`參數`true`來指定要叫用的已標示為已由另一個項目，此事件路由上的路由事件的處理常式。  
  
> [!TIP]
>  您可以取代內建的拖放功能<xref:System.Windows.Controls.TextBox>， <xref:System.Windows.Controls.RichTextBox>，和<xref:System.Windows.Documents.FlowDocument>方法是處理拖放事件的預覽版本，並標示為已處理的預覽事件。 不過，這將會停用內建的拖放功能，並不建議使用。  
  
## <a name="example"></a>範例  
 下列範例示範如何加入處理常式<xref:System.Windows.DragDrop.DragOver>和<xref:System.Windows.DragDrop.Drop>上的事件<xref:System.Windows.Controls.RichTextBox>。 這個範例會使用<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>方法和集合`handledEventsToo`參數`true`以便即使將會叫用事件處理常式<xref:System.Windows.Controls.RichTextBox>標記為已處理這些事件。 中的事件處理常式的程式碼會將功能加入開啟文字檔上卸除<xref:System.Windows.Controls.RichTextBox>。  
  
 若要測試此範例中，從 Windows 檔案總管拖曳文字檔案或 rtf 文字格式 (RTF) 檔案<xref:System.Windows.Controls.RichTextBox>。 該檔案開啟<xref:System.Windows.Controls.RichTextBox>。 如果您按下 SHIFT 鍵，再卸除檔案，將會以純文字格式開啟檔案。  
  
 [!code-xaml[DragDropSnippets#RtbXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
