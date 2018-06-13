---
title: 攔截手寫筆的輸入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'architecture [WPF], '
- ', '
- ', '
- ', '
ms.assetid: 791bb2f0-4e5c-4569-ac3c-211996808d44
ms.openlocfilehash: 813c5f6060b3a59358b286c93a9077debd41a746
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547612"
---
# <a name="intercepting-input-from-the-stylus"></a>攔截手寫筆的輸入
<xref:System.Windows.Input.StylusPlugIns>架構提供一個機制，透過實作的低階控制<xref:System.Windows.Input.Stylus>輸入和建立數位筆跡<xref:System.Windows.Ink.Stroke>物件。 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>類別提供您實作自訂行為，並將它套用到來自手寫筆裝置以獲得最佳的效能資料的資料流的機制。  
  
 本主題包含下列子章節：  
  
-   [架構](#Architecture)  
  
-   [實作手寫筆外掛程式](#ImplementingStylusPlugins)  
  
-   [InkCanvas 加入外掛程式](#AddingYourPluginToAnInkCanvas)  
  
-   [結論](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>架構  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>是的演進[StylusInput](http://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409)所述的 Api[存取和操作畫筆輸入](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)，請在[Microsoft Windows XP Tablet PC Edition 軟體開發套件 1.7](http://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409)。  
  
 每個<xref:System.Windows.UIElement>具有<xref:System.Windows.UIElement.StylusPlugIns%2A>屬性<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>。 您可以加入<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>的項目<xref:System.Windows.UIElement.StylusPlugIns%2A>屬性來操作<xref:System.Windows.Input.StylusPoint>產生做為它的資料。 <xref:System.Windows.Input.StylusPoint> 資料包含系統潀糔蠮，包括支援的所有屬性<xref:System.Windows.Input.StylusPoint.X%2A>和<xref:System.Windows.Input.StylusPoint.Y%2A>點的資料，以及<xref:System.Windows.Input.StylusPoint.PressureFactor%2A>資料。  
  
 您<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>物件直接插入的資料來自資料流<xref:System.Windows.Input.Stylus>裝置，當您將加入<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>至<xref:System.Windows.UIElement.StylusPlugIns%2A>屬性。 在其中加入外掛程式順序<xref:System.Windows.UIElement.StylusPlugIns%2A>集合會要求他們將收到的順序<xref:System.Windows.Input.StylusPoint>資料。 比方說，如果您加入篩選外掛程式，以限制到特定區域中，輸入，然後再新增 的寫法是可以辨識筆勢的外掛程式，外掛程式可辨識筆勢會收到篩選<xref:System.Windows.Input.StylusPoint>資料。  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>實作手寫筆外掛程式  
 若要實作的外掛程式，衍生自<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>。 這個類別是套用的 o 中的資料流，因為它來自<xref:System.Windows.Input.Stylus>。 此類別中，您可以修改的值<xref:System.Windows.Input.StylusPoint>資料。  
  
> [!CAUTION]
>  如果<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>擲回或造成例外狀況，應用程式即將關閉。 您應該徹底測試使用的控制項<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>，並只使用控制，如果您確定<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>不會擲回例外狀況。  
  
 下列範例會示範外掛程式，藉由修改限制手寫筆輸入<xref:System.Windows.Input.StylusPoint.X%2A>和<xref:System.Windows.Input.StylusPoint.Y%2A>中的值<xref:System.Windows.Input.StylusPoint>資料，因為它來自<xref:System.Windows.Input.Stylus>裝置。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>InkCanvas 加入外掛程式  
 若要使用您的自訂外掛程式的最簡單方式是實作一個衍生自 InkCanvas 的類別，並將它加入<xref:System.Windows.UIElement.StylusPlugIns%2A>屬性。  
  
 下列範例會示範自訂<xref:System.Windows.Controls.InkCanvas>篩選筆跡。  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 如果您將加入`FilterInkCanvas`應用程式和執行它，您會注意到筆墨筆劃使用者後不會限制為之前的區域。 這是因為<xref:System.Windows.Controls.InkCanvas>具有<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>屬性，這是<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>且已隸屬<xref:System.Windows.UIElement.StylusPlugIns%2A>集合。 自訂<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>您已加入至<xref:System.Windows.UIElement.StylusPlugIns%2A>集合接收<xref:System.Windows.Input.StylusPoint>後的資料<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>接收資料。 如此一來，<xref:System.Windows.Input.StylusPoint>資料將不會篩選直到之後使用者取消結束筆觸以畫筆。 若要篩選使用者將它繪製的筆墨，您必須插入`FilterPlugin`之前<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>。  
  
 下列 C# 程式碼會示範自訂<xref:System.Windows.Controls.InkCanvas>，篩選它是繪製的筆墨。  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>結論  
 由衍生您自己<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>類別，並將其插入<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>集合，您可以大幅強化您的數位筆跡的行為。 您可以存取<xref:System.Windows.Input.StylusPoint>產生做為它的資料，讓您有機會自訂<xref:System.Windows.Input.Stylus>輸入。 因為這類低層級存取<xref:System.Windows.Input.StylusPoint>資料，您可以為您的應用程式實作筆墨收集和呈現以獲得最佳效能。  
  
## <a name="see-also"></a>另請參閱  
 [筆跡進階處理](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)  
 [存取和管理畫筆輸入](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
