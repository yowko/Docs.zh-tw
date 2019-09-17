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
ms.openlocfilehash: 2547c0aa2f3a14080868c2760fa8999eb99d3d16
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046321"
---
# <a name="intercepting-input-from-the-stylus"></a>攔截手寫筆的輸入
此<xref:System.Windows.Input.StylusPlugIns>架構提供一種機制，可讓您對<xref:System.Windows.Input.Stylus>輸入和數位筆跡<xref:System.Windows.Ink.Stroke>物件的建立執行低層級的控制。 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>類別提供一種機制，可讓您執行自訂行為，並將其套用至來自手寫筆裝置的資料流程，以獲得最佳效能。  
  
 本主題包含下列子章節：  
  
- [架構](#Architecture)  
  
- [執行手寫筆外掛程式](#ImplementingStylusPlugins)  
  
- [將外掛程式新增至 InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
- [結論](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>架構  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 是 [StylusInput](https://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) api 的演進，在[Microsoft Windows XP Tablet PC Edition 軟體發展工具組 1.7](https://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409)中[是存取和操作手寫筆輸入](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)中所述。  
  
 每<xref:System.Windows.UIElement>個都<xref:System.Windows.UIElement.StylusPlugIns%2A>有一個<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>屬性，其為。 您可以將加入<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>至專案的<xref:System.Windows.UIElement.StylusPlugIns%2A>屬性，以在<xref:System.Windows.Input.StylusPoint>產生資料時操作它。 <xref:System.Windows.Input.StylusPoint>資料是由系統數位板支援的所有屬性所組成，包括<xref:System.Windows.Input.StylusPoint.X%2A>和<xref:System.Windows.Input.StylusPoint.Y%2A>點<xref:System.Windows.Input.StylusPoint.PressureFactor%2A>資料，以及資料。  
  
 當<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> <xref:System.Windows.Input.Stylus> 您將<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>加入至屬性時，會將您的物件直接插入至來自裝置的資料串流。<xref:System.Windows.UIElement.StylusPlugIns%2A> 外掛程式新增至<xref:System.Windows.UIElement.StylusPlugIns%2A>集合的順序會決定它們接收<xref:System.Windows.Input.StylusPoint>資料的順序。 例如，如果您加入的篩選外掛程式會將輸入限制在特定區域，然後加入可辨識書寫筆勢的外掛程式，則可辨識手勢的外掛程式將會接收篩選<xref:System.Windows.Input.StylusPoint>的資料。  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>執行手寫筆外掛程式  
 若要執行外掛程式，請從<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>衍生類別。 此類別會套用至從<xref:System.Windows.Input.Stylus>傳入的資料流程。 在此類別中，您可以修改<xref:System.Windows.Input.StylusPoint>資料的值。  
  
> [!CAUTION]
> <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>如果擲回或造成例外狀況，應用程式將會關閉。 您應該徹底測試使用的<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>控制項，而且只有在您<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>確定不會擲回例外狀況時，才會使用控制項。  
  
 下列範例示範外掛程式，它會<xref:System.Windows.Input.StylusPoint.X%2A>在從<xref:System.Windows.Input.Stylus>裝置傳入的<xref:System.Windows.Input.StylusPoint>資料中修改和<xref:System.Windows.Input.StylusPoint.Y%2A>值，以限制手寫筆輸入。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>將外掛程式新增至 InkCanvas  
 使用自訂外掛程式最簡單的方式，就是執行衍生自 InkCanvas 的類別，並將它加入至<xref:System.Windows.UIElement.StylusPlugIns%2A>屬性。  
  
 下列範例示範篩選筆墨的<xref:System.Windows.Controls.InkCanvas>自訂。  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 如果您將新增`FilterInkCanvas`至您的應用程式並加以執行，您會注意到，在使用者完成筆劃之前，筆跡不會限制為區域。 這<xref:System.Windows.Controls.InkCanvas>是因為<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>具有<xref:System.Windows.UIElement.StylusPlugIns%2A>屬性，這是，而且已經是集合的成員。<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 您新增<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> <xref:System.Windows.Input.StylusPoint>至集合的自訂會在收到資料<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>之後接收資料。 <xref:System.Windows.UIElement.StylusPlugIns%2A> 因此，在使用者提起<xref:System.Windows.Input.StylusPoint>畫筆以結束筆劃之前，將不會篩選資料。 若要在使用者繪製時篩選筆墨，您必須在`FilterPlugin` <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>之前插入。  
  
 下列C#程式碼示範的自<xref:System.Windows.Controls.InkCanvas>定義會篩選繪製的筆墨。  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>結論  
 藉由衍生您<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>自己的類別，並<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>將其插入集合中，您可以大幅增強數位筆跡的行為。 您可以存取產生的<xref:System.Windows.Input.StylusPoint>資料，讓您有機會<xref:System.Windows.Input.Stylus>自訂輸入。 因為您有這類資料的<xref:System.Windows.Input.StylusPoint>低層級存取權，所以您可以使用應用程式的最佳效能來執行筆墨集合和呈現。  
  
## <a name="see-also"></a>另請參閱

- [筆跡進階處理](advanced-ink-handling.md)
- [存取和操作手寫筆輸入](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
