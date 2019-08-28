---
title: 作法：開啟置放在 RichTextBox 控制項上的檔案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], RichTextBox
- RichTextBox [WPF], drag-and-drop
- drag-and-drop [WPF], open a dropped file
ms.assetid: 6bb8bb54-f576-41db-a9a7-24102ddeb490
ms.openlocfilehash: 408d48856362fa8a77a44e2cc97cb2d5ff608dcf
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046358"
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>HOW TO：開啟置放在 RichTextBox 控制項上的檔案

在中[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], 、<xref:System.Windows.Controls.RichTextBox>和<xref:System.Windows.Documents.FlowDocument>控制項都有內建的拖放功能。 <xref:System.Windows.Controls.TextBox> 內建功能可讓您將文字拖放到控制項的內部和之間。 不過, 它不會藉由將檔案放在控制項上來開啟檔案。 這些控制項也會將拖放事件標示為已處理。 因此, 根據預設, 您無法新增自己的事件處理常式, 以提供開啟已卸載檔案的功能。

若要在這些控制項中加入拖放事件的其他處理, 請使用<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>方法來加入拖放事件的事件處理常式。 將參數設定為`true` , 讓指定的處理常式針對已標示為沿著事件路由的另一個專案處理的路由事件叫用。 `handledEventsToo`

> [!TIP]
> 您可以藉由處理拖放事件的預覽版本, 並將<xref:System.Windows.Controls.TextBox>預覽<xref:System.Windows.Controls.RichTextBox>事件標示<xref:System.Windows.Documents.FlowDocument>為已處理, 來取代、和的內建拖放功能。 不過, 這會停用內建的拖放功能, 因此不建議您這麼做。

## <a name="example"></a>範例

下列範例示範如何在上<xref:System.Windows.DragDrop.DragOver> <xref:System.Windows.Controls.RichTextBox>加入和<xref:System.Windows.DragDrop.Drop>事件的處理常式。 這個範例會使用<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>方法, 並將`handledEventsToo`參數設定`true`為, 以便叫用<xref:System.Windows.Controls.RichTextBox>事件處理常式, 即使將這些事件標示為已處理也一樣。 事件處理常式中的程式碼會新增功能, 以開啟在上<xref:System.Windows.Controls.RichTextBox>放置的文字檔。

若要測試此範例, 請將文字檔或 rtf 格式檔案從 Windows Explorer 拖曳至<xref:System.Windows.Controls.RichTextBox>。 檔案將會在中<xref:System.Windows.Controls.RichTextBox>開啟。 如果您在卸載檔案之前按下 SHIFT 鍵, 檔案將會以純文字的形式開啟。

[!code-xaml[DragDropSnippets#RtbXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]

[!code-csharp[DragDropSnippets#RtbHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
[!code-vb[DragDropSnippets#RtbHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
