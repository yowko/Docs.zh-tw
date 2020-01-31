---
title: 收集數位筆跡
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
ms.openlocfilehash: 813a5313a6fbf83c36cdbed1f64ce69a217ad788
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747022"
---
# <a name="collect-ink"></a>收集筆跡

[Windows Presentation Foundation](../index.md) 平台收集數位筆跡當成其功能的核心部分。 本主題討論在 Windows Presentation Foundation （WPF）中收集筆跡的方法。

## <a name="prerequisites"></a>必要條件：

若要使用下列範例，您必須先安裝 Visual Studio 和 Windows SDK。 您也應該瞭解如何撰寫 WPF 的應用程式。 如需 WPF 使用者入門的詳細資訊，請參閱[逐步解說：我的第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。

## <a name="use-the-inkcanvas-element"></a>使用 InkCanvas 元素

<xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> 元素提供最簡單的方式，在 WPF 中收集筆跡。 使用 <xref:System.Windows.Controls.InkCanvas> 元素來接收和顯示筆墨輸入。 您通常是使用手寫筆，其與數位板互動來產生筆跡筆劃以輸入筆跡。 此外，滑鼠也可以代替手寫筆。 建立的筆劃會以 <xref:System.Windows.Ink.Stroke> 物件的形式呈現，並可透過程式設計方式和使用者輸入來操作。 <xref:System.Windows.Controls.InkCanvas> 可讓使用者選取、修改或刪除現有的 <xref:System.Windows.Ink.Stroke>。

藉由使用 XAML，您可以輕鬆地設定筆跡集合，如同將**InkCanvas**元素新增至樹狀結構一樣。 下列範例會將 <xref:System.Windows.Controls.InkCanvas> 新增至 Visual Studio 中建立的預設 WPF 專案：

[!code-xaml[DigitalInkTopics#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

**InkCanvas**元素也可以包含子專案，讓您可以將筆跡注釋功能新增至幾乎任何類型的 XAML 專案。 例如，若要將墨蹟功能加入至文字專案，只要將它設為 <xref:System.Windows.Controls.InkCanvas>的子系即可：

[!code-xaml[DigitalInkTopics#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

新增使用筆跡來標記影像的支援也一樣簡單：

[!code-xaml[DigitalInkTopics#7](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a>InkCollection 模式

<xref:System.Windows.Controls.InkCanvas> 透過其 <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> 屬性提供各種輸入模式的支援。

### <a name="manipulate-ink"></a>操作筆墨

<xref:System.Windows.Controls.InkCanvas> 提供許多筆跡編輯作業的支援。 例如，<xref:System.Windows.Controls.InkCanvas> 支援反向畫筆清除，而且不需要額外的程式碼就可以將功能加入至專案。

#### <a name="selection"></a>選取

設定選取模式就像將 [<xref:System.Windows.Controls.InkCanvasEditingMode>] 屬性設為 [**選取**] 一樣簡單。

下列程式碼會根據 <xref:System.Windows.Forms.CheckBox>的值來設定編輯模式：

[!code-csharp[DigitalInkTopics#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a>DrawingAttributes

使用 [<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>] 屬性來變更筆跡筆劃的外觀。 例如，<xref:System.Windows.Ink.DrawingAttributes> 的 <xref:System.Windows.Ink.DrawingAttributes.Color%2A> 成員會設定所呈現 <xref:System.Windows.Ink.Stroke>的色彩。

下列範例會將所選筆劃的色彩變更為紅色：

[!code-csharp[DigitalInkTopics#9](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes

<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> 屬性可讓您存取屬性，例如要在 <xref:System.Windows.Controls.InkCanvas>中建立之筆劃的高度、寬度和色彩。 變更 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>之後，所有進入 <xref:System.Windows.Controls.InkCanvas> 的未來筆劃都會以新的屬性值呈現。

除了修改程式碼後置檔案中的 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> 之外，您還可以使用 XAML 語法來指定 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> 的屬性。

下一個範例示範如何設定 <xref:System.Windows.Ink.DrawingAttributes.Color%2A> 屬性。 若要使用此程式碼，請在 Visual Studio 中建立名為 "HelloInkCanvas" 的新 WPF 專案。 將*mainwindow.xaml*中的程式碼取代為下列程式碼：

[!code-xaml[HelloInkCanvas#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

接下來，將下列按鈕事件處理常式新增至 Mainwindow.xaml 類別內的程式碼後置檔案中：

[!code-csharp[HelloInkCanvas#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

複製此程式碼之後，請在 Visual Studio 中按**F5** ，以在偵錯工具中執行程式。

請注意，<xref:System.Windows.Controls.StackPanel> 如何將按鈕放在 <xref:System.Windows.Controls.InkCanvas>的頂端。 如果您嘗試將筆跡放在按鈕上方，則 <xref:System.Windows.Controls.InkCanvas> 會收集並轉譯按鈕後方的筆墨。 這是因為按鈕是 <xref:System.Windows.Controls.InkCanvas> 的同級，而不是子系。 而且按鈕的級別高於疊置順序，所以筆跡轉譯在其後。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>
