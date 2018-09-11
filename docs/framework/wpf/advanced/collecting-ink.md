---
title: WPF 應用程式中收集筆跡
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], collecting
- InkCanvas element [WPF]
- properties [WPF], DrawingAttributes
- collecting digital ink [WPF]
- digital ink [WPF], collecting
- properties [WPF], DefaultDrawingAttributes
- DefaultDrawingAttributes property [WPF]
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
ms.openlocfilehash: 25f9c0141a97d8e52e0883b14fd3e1f4574a05ea
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2018
ms.locfileid: "44360683"
---
# <a name="collect-ink"></a>收集筆墨

[Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) 平台收集數位筆跡當成其功能的核心部分。 本主題討論收集筆跡 Windows Presentation Foundation (WPF) 中的方法。

## <a name="prerequisites"></a>必要條件

若要使用下列的範例，您必須先安裝 Visual Studio 和[!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]。 您也應該了解如何撰寫 wpf 應用程式。 如需有關如何開始使用 WPF 的詳細資訊，請參閱[逐步解說： 我第一個 WPF 桌面應用程式](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。

## <a name="use-the-inkcanvas-element"></a>使用 InkCanvas 項目

<xref:System.Windows.Controls.InkCanvas?displayProperty=fullName>項目提供 WPF 中收集筆跡最簡單的方式。 使用<xref:System.Windows.Controls.InkCanvas>接收並顯示筆跡輸入的項目。 您通常是使用手寫筆，其與數位板互動來產生筆跡筆劃以輸入筆跡。 此外，滑鼠也可以代替手寫筆。 建立的筆劃統稱為<xref:System.Windows.Ink.Stroke>物件，而且它們可以操作以程式設計方式及使用者輸入。 <xref:System.Windows.Controls.InkCanvas>可讓使用者選取、 修改或刪除現有<xref:System.Windows.Ink.Stroke>。

藉由使用 XAML，您可以設定筆跡收集新增輕鬆**InkCanvas**至樹狀結構的項目。 下列範例會將<xref:System.Windows.Controls.InkCanvas>Visual Studio 中建立的預設 WPF 專案：

[!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

**InkCanvas**元素也可以包含子項目，讓您可以將筆跡註釋功能新增至幾乎任何類型的 XAML 項目。 比方說，若要將筆跡功能新增至文字項目，讓它的子系<xref:System.Windows.Controls.InkCanvas>:

[!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

新增標記筆墨的映像的支援也一樣簡單：

[!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a>InkCollection 模式

<xref:System.Windows.Controls.InkCanvas>提供支援，針對各種輸入模式透過其<xref:System.Windows.Controls.InkCanvas.EditingMode%2A>屬性。

### <a name="manipulate-ink"></a>操作筆跡

<xref:System.Windows.Controls.InkCanvas>提供許多筆跡編輯作業的支援。 比方說，<xref:System.Windows.Controls.InkCanvas>支援畫筆後清除，並使用任何額外的程式碼，才能將功能新增至項目。

#### <a name="selection"></a>選取

設定選取模式很簡單，只要設定<xref:System.Windows.Controls.InkCanvasEditingMode>屬性，以**選取**。

下列程式碼設定的值為基礎的編輯模式<xref:System.Windows.Forms.CheckBox>:

[!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a>DrawingAttributes

使用<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>来變更筆跡筆劃的外觀屬性。 比方說，<xref:System.Windows.Ink.DrawingAttributes.Color%2A>隸屬<xref:System.Windows.Ink.DrawingAttributes>設定的色彩呈現的<xref:System.Windows.Ink.Stroke>。

下列範例會將選取的筆劃的色彩變更為紅色：

[!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes

<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>屬性可存取的屬性，例如高度、 寬度和色彩在中建立的筆劃<xref:System.Windows.Controls.InkCanvas>。 一旦變更<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>，輸入的所有未來筆劃<xref:System.Windows.Controls.InkCanvas>新的屬性值，以呈現。

除了修改<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>在程式碼後置檔案中，您可以使用 XAML 語法指定<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>屬性。

下一個範例示範如何設定<xref:System.Windows.Ink.DrawingAttributes.Color%2A>屬性。 若要使用此程式碼，建立新的 WPF 專案，Visual Studio 中稱為"HelloInkCanvas"。 中的程式碼取代*MainWindow.xaml*為下列程式碼的檔案：

[!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

接下來，加入下列的按鈕事件處理常式的程式碼後置檔案，在 MainWindow 類別：

[!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

複製此程式碼之後, 按下**F5**在 Visual Studio 中偵錯工具中執行程式。

請注意如何<xref:System.Windows.Controls.StackPanel>將按鈕的上方放置<xref:System.Windows.Controls.InkCanvas>。 如果您嘗試透過頂端的按鈕時，筆墨<xref:System.Windows.Controls.InkCanvas>收集並呈現在按鈕後方的筆墨。 這是因為按鈕的同層級<xref:System.Windows.Controls.InkCanvas>相對於子系。 而且按鈕的級別高於疊置順序，所以筆跡轉譯在其後。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>