---
title: 收集筆墨
ms.date: 03/30/2017
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
ms.openlocfilehash: d441f606a577a2c0506a0f9ae510b3ea1045bba9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541066"
---
# <a name="collecting-ink"></a>收集筆墨
[Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) 平台收集數位筆跡當成其功能的核心部分。 本主題討論的筆墨 Windows Presentation Foundation (WPF) 中集合的方法。  
  
## <a name="prerequisites"></a>必要條件  
 若要使用下列範例，您必須先安裝 [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] 和 [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]。 您也應該了解如何撰寫適用於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的應用程式。 如需開始使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，請參閱[逐步解說： 第一個 WPF 桌面應用程式](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。  
  
## <a name="using-the-inkcanvas-element"></a>使用 InkCanvas 項目  
 <xref:System.Windows.Controls.InkCanvas>項目會提供最簡單的方式收集中的筆墨[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。 <xref:System.Windows.Controls.InkCanvas>項目是類似於[Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/microsoft.ink.inkoverlay\(v=vs.90\).aspx)物件從[!INCLUDE[TLA2#tla_tpclssdk](../../../../includes/tla2sharptla-tpclssdk-md.md)]及較早版本。  
  
 使用<xref:System.Windows.Controls.InkCanvas>來接收和顯示筆墨輸入的項目。 您通常是使用手寫筆，其與數位板互動來產生筆跡筆劃以輸入筆跡。 此外，滑鼠也可以代替手寫筆。 建立的筆觸會表示為<xref:System.Windows.Ink.Stroke>物件，而且它們可以操作以程式設計方式和由使用者輸入。 <xref:System.Windows.Controls.InkCanvas>可讓使用者選取、 修改或刪除現有<xref:System.Windows.Ink.Stroke>。  
  
 使用 XAML 可以設定筆跡收集，如將 `InkCanvas` 項目新增至樹狀結構一樣容易。 下列範例會將<xref:System.Windows.Controls.InkCanvas>預設[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中建立專案[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]。  
  
 [!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]  
  
 `InkCanvas` 項目也可以包含子項目，以將筆跡註釋功能新增至幾乎任何類型的 XAML 項目。 比方說，將筆跡的功能加入至文字項目，只會保持它的子系<xref:System.Windows.Controls.InkCanvas>。  
  
 [!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]  
  
 新增以筆跡標記映像的支援就是這麼簡單。  
  
 [!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]  
  
### <a name="inkcollection-modes"></a>InkCollection 模式  
 <xref:System.Windows.Controls.InkCanvas>支援的各種輸入模式透過其<xref:System.Windows.Controls.InkCanvas.EditingMode%2A>屬性。  
  
### <a name="manipulating-ink"></a>操作筆跡  
 <xref:System.Windows.Controls.InkCanvas>許多筆墨編輯作業提供支援。 例如，<xref:System.Windows.Controls.InkCanvas>支援畫筆後清除任何額外的程式碼，才能將功能加入至項目。  
  
#### <a name="selection"></a>選取  
 設定選取範圍模式很簡單，只設定<xref:System.Windows.Controls.InkCanvasEditingMode>屬性**選取**。 下列程式碼中設定的值為基礎的編輯模式<xref:System.Windows.Forms.CheckBox>:  
  
 [!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
 [!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]  
  
#### <a name="drawingattributes"></a>DrawingAttributes  
 使用<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A>来變更的筆墨筆劃外觀屬性。 比方說，<xref:System.Windows.Ink.DrawingAttributes.Color%2A>隸屬<xref:System.Windows.Ink.DrawingAttributes>設定轉譯的色彩<xref:System.Windows.Ink.Stroke>。 下例會將所選筆劃的色彩變更為紅色。  
  
 [!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
 [!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]  
  
### <a name="defaultdrawingattributes"></a>DefaultDrawingAttributes  
 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>屬性可存取屬性，例如高度、 寬度和色彩中建立的筆劃<xref:System.Windows.Controls.InkCanvas>。 一旦變更<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>，輸入的所有未來筆劃<xref:System.Windows.Controls.InkCanvas>會轉譯與新的屬性值。  
  
 除了修改<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>在程式碼後置檔案中，您可以使用 XAML 語法來指定<xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>屬性。 下列 XAML 程式碼示範如何設定<xref:System.Windows.Ink.DrawingAttributes.Color%2A>屬性。 若要使用此程式碼，請建立新的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 專案，在 Visual Studio 2005 中稱為 "HelloInkCanvas"。 以下列程式碼取代 Window1.xaml 檔案中的程式碼。  
  
 [!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]  
  
 接下來，將以下按鈕事件處理常式新增至 Window1 類別內的程式碼後置檔案。  
  
 [!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]  
  
 複製此程式碼之後，請在 Microsoft Visual Studio 2005 中按 **F5** 執行偵錯工具中的程式。  
  
 請注意如何<xref:System.Windows.Controls.StackPanel>將上方的按鈕<xref:System.Windows.Controls.InkCanvas>。 如果您嘗試透過頂端的按鈕時，筆墨<xref:System.Windows.Controls.InkCanvas>收集並呈現按鈕之後的筆墨。 這是因為按鈕的同層級<xref:System.Windows.Controls.InkCanvas>而不是子系。 而且按鈕的級別高於疊置順序，所以筆跡轉譯在其後。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Ink.DrawingAttributes>  
 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>  
 <xref:System.Windows.Ink>
