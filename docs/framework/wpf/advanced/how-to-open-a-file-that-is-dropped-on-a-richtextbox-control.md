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
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a><span data-ttu-id="5587f-102">HOW TO：開啟置放在 RichTextBox 控制項上的檔案</span><span class="sxs-lookup"><span data-stu-id="5587f-102">How to: Open a File That is Dropped on a RichTextBox Control</span></span>

<span data-ttu-id="5587f-103">在中[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], 、<xref:System.Windows.Controls.RichTextBox>和<xref:System.Windows.Documents.FlowDocument>控制項都有內建的拖放功能。 <xref:System.Windows.Controls.TextBox></span><span class="sxs-lookup"><span data-stu-id="5587f-103">In [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], the <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Documents.FlowDocument> controls all have built-in drag-and-drop functionality.</span></span> <span data-ttu-id="5587f-104">內建功能可讓您將文字拖放到控制項的內部和之間。</span><span class="sxs-lookup"><span data-stu-id="5587f-104">The built-in functionality enables drag-and-drop of text within and between the controls.</span></span> <span data-ttu-id="5587f-105">不過, 它不會藉由將檔案放在控制項上來開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="5587f-105">However, it does not enable opening a file by dropping the file on the control.</span></span> <span data-ttu-id="5587f-106">這些控制項也會將拖放事件標示為已處理。</span><span class="sxs-lookup"><span data-stu-id="5587f-106">These controls also mark the drag-and-drop events as handled.</span></span> <span data-ttu-id="5587f-107">因此, 根據預設, 您無法新增自己的事件處理常式, 以提供開啟已卸載檔案的功能。</span><span class="sxs-lookup"><span data-stu-id="5587f-107">As a result, by default, you cannot add your own event handlers to provide functionality to open dropped files.</span></span>

<span data-ttu-id="5587f-108">若要在這些控制項中加入拖放事件的其他處理, 請使用<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>方法來加入拖放事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5587f-108">To add additional handling for drag-and-drop events in these controls, use the <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> method to add your event handlers for the drag-and-drop events.</span></span> <span data-ttu-id="5587f-109">將參數設定為`true` , 讓指定的處理常式針對已標示為沿著事件路由的另一個專案處理的路由事件叫用。 `handledEventsToo`</span><span class="sxs-lookup"><span data-stu-id="5587f-109">Set the `handledEventsToo` parameter to `true` to have the specified handler be invoked for a routed event that has already been marked as handled by another element along the event route.</span></span>

> [!TIP]
> <span data-ttu-id="5587f-110">您可以藉由處理拖放事件的預覽版本, 並將<xref:System.Windows.Controls.TextBox>預覽<xref:System.Windows.Controls.RichTextBox>事件標示<xref:System.Windows.Documents.FlowDocument>為已處理, 來取代、和的內建拖放功能。</span><span class="sxs-lookup"><span data-stu-id="5587f-110">You can replace the built-in drag-and-drop functionality of <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Documents.FlowDocument> by handling the preview versions of the drag-and-drop events and marking the preview events as handled.</span></span> <span data-ttu-id="5587f-111">不過, 這會停用內建的拖放功能, 因此不建議您這麼做。</span><span class="sxs-lookup"><span data-stu-id="5587f-111">However, this will disable the built-in drag-and-drop functionality, and is not recommended.</span></span>

## <a name="example"></a><span data-ttu-id="5587f-112">範例</span><span class="sxs-lookup"><span data-stu-id="5587f-112">Example</span></span>

<span data-ttu-id="5587f-113">下列範例示範如何在上<xref:System.Windows.DragDrop.DragOver> <xref:System.Windows.Controls.RichTextBox>加入和<xref:System.Windows.DragDrop.Drop>事件的處理常式。</span><span class="sxs-lookup"><span data-stu-id="5587f-113">The following example demonstrates how to add handlers for the <xref:System.Windows.DragDrop.DragOver> and <xref:System.Windows.DragDrop.Drop> events on a <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="5587f-114">這個範例會使用<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>方法, 並將`handledEventsToo`參數設定`true`為, 以便叫用<xref:System.Windows.Controls.RichTextBox>事件處理常式, 即使將這些事件標示為已處理也一樣。</span><span class="sxs-lookup"><span data-stu-id="5587f-114">This example uses the <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> method and sets the `handledEventsToo` parameter to `true` so that the events handlers will be invoked even though the <xref:System.Windows.Controls.RichTextBox> marks these events as handled.</span></span> <span data-ttu-id="5587f-115">事件處理常式中的程式碼會新增功能, 以開啟在上<xref:System.Windows.Controls.RichTextBox>放置的文字檔。</span><span class="sxs-lookup"><span data-stu-id="5587f-115">The code in the event handlers adds functionality to open a text file that is dropped on the <xref:System.Windows.Controls.RichTextBox>.</span></span>

<span data-ttu-id="5587f-116">若要測試此範例, 請將文字檔或 rtf 格式檔案從 Windows Explorer 拖曳至<xref:System.Windows.Controls.RichTextBox>。</span><span class="sxs-lookup"><span data-stu-id="5587f-116">To test this example, drag a text file or a rich text format (RTF) file from Windows Explorer to the <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="5587f-117">檔案將會在中<xref:System.Windows.Controls.RichTextBox>開啟。</span><span class="sxs-lookup"><span data-stu-id="5587f-117">The file will be opened in the <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="5587f-118">如果您在卸載檔案之前按下 SHIFT 鍵, 檔案將會以純文字的形式開啟。</span><span class="sxs-lookup"><span data-stu-id="5587f-118">If you press the SHIFT key before the dropping the file, the file will be opened as plain text.</span></span>

[!code-xaml[DragDropSnippets#RtbXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]

[!code-csharp[DragDropSnippets#RtbHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
[!code-vb[DragDropSnippets#RtbHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
