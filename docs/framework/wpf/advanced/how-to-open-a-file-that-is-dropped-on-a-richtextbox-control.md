---
title: HOW TO：開啟置放在 RichTextBox 控制項上的檔案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], RichTextBox
- RichTextBox [WPF], drag-and-drop
- drag-and-drop [WPF], open a dropped file
ms.assetid: 6bb8bb54-f576-41db-a9a7-24102ddeb490
ms.openlocfilehash: 8ffa4c9919788060dc4524e127c181ee8282e6f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768598"
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>HOW TO：開啟置放在 RichTextBox 控制項上的檔案
在  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]，則<xref:System.Windows.Controls.TextBox>， <xref:System.Windows.Controls.RichTextBox>，和<xref:System.Windows.Documents.FlowDocument>控制項都會有內建的拖放功能。 內建功能可讓拖放在與控制項之間的文字。 不過，它不會啟用拖放控制項上的檔案來開啟檔案。 這些控制項也標記為已處理的拖放事件。 如此一來，根據預設，您無法新增您自己的事件處理常式，以提供功能來開啟已卸除的檔案。  
  
 若要在這些控制項中新增額外處理的拖放事件，請使用<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>新增您的拖放事件的事件處理常式的方法。 設定`handledEventsToo`參數來`true`能夠指定要叫用已標示為已由另一個項目，此事件路由的路由事件的處理常式。  
  
> [!TIP]
>  您可以取代內建的拖放功能<xref:System.Windows.Controls.TextBox>， <xref:System.Windows.Controls.RichTextBox>，和<xref:System.Windows.Documents.FlowDocument>處理拖放事件的預覽版本，並將預覽事件標示為已處理。 不過，這將會停用內建的拖放功能，並不建議使用。  
  
## <a name="example"></a>範例  
 下列範例示範如何加入處理常式<xref:System.Windows.DragDrop.DragOver>並<xref:System.Windows.DragDrop.Drop>上的事件<xref:System.Windows.Controls.RichTextBox>。 這個範例會使用<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>方法，並將`handledEventsToo`參數來`true`以便即使將會叫用事件處理常式<xref:System.Windows.Controls.RichTextBox>標記為已處理的這些事件。 中的事件處理常式的程式碼將功能加入至開啟置放在的文字檔案<xref:System.Windows.Controls.RichTextBox>。  
  
 若要測試此範例中，從以 Windows 檔案總管拖曳文字檔案或 rtf 格式 (RTF) 檔案<xref:System.Windows.Controls.RichTextBox>。 檔案將會開啟<xref:System.Windows.Controls.RichTextBox>。 如果您按下 SHIFT 鍵再卸除檔案，將以純文字格式開啟檔案。  
  
 [!code-xaml[DragDropSnippets#RtbXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
