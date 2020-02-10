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
ms.openlocfilehash: 7629843730a82584e94448ceac1ea574906876c9
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095134"
---
# <a name="intercepting-input-from-the-stylus"></a>攔截手寫筆的輸入
<xref:System.Windows.Input.StylusPlugIns> 架構提供一種機制，可對 <xref:System.Windows.Input.Stylus> 輸入和建立數位筆跡 <xref:System.Windows.Ink.Stroke> 物件進行低層級的控制。 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 類別提供一種機制，可讓您執行自訂行為，並將其套用至來自手寫筆裝置的資料流程，以獲得最佳效能。  
  
 本主題包含下列各小節：  
  
- [架構](#Architecture)  
  
- [執行手寫筆外掛程式](#ImplementingStylusPlugins)  
  
- [將外掛程式新增至 InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
- [結論](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>架構  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 是[StylusInput](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms574861(v=vs.90)) api 的演進，如[存取和操作手寫筆輸入](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))中所述。  
  
 每個 <xref:System.Windows.UIElement> 都有一個 <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>的 <xref:System.Windows.UIElement.StylusPlugIns%2A> 屬性。 您可以將 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 新增至專案的 <xref:System.Windows.UIElement.StylusPlugIns%2A> 屬性，以操作產生的 <xref:System.Windows.Input.StylusPoint> 資料。 <xref:System.Windows.Input.StylusPoint> 資料是由系統數位板支援的所有屬性所組成，包括 <xref:System.Windows.Input.StylusPoint.X%2A> 和 <xref:System.Windows.Input.StylusPoint.Y%2A> 點資料，以及 <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> 資料。  
  
 當您將 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 新增至 <xref:System.Windows.UIElement.StylusPlugIns%2A> 屬性時，會將您的 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 物件直接插入至來自 <xref:System.Windows.Input.Stylus> 裝置的資料串流。 外掛程式新增至 <xref:System.Windows.UIElement.StylusPlugIns%2A> 集合的順序，會決定它們接收 <xref:System.Windows.Input.StylusPoint> 資料的順序。 例如，如果您加入的篩選外掛程式會將輸入限制在特定區域，然後新增外掛程式來辨識寫入的筆勢，則可辨識手勢的外掛程式將會接收篩選的 <xref:System.Windows.Input.StylusPoint> 資料。  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>執行手寫筆外掛程式  
 若要執行外掛程式，請從 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>衍生一個類別。 此類別會套用至從 <xref:System.Windows.Input.Stylus>傳入的資料流程。 在此類別中，您可以修改 <xref:System.Windows.Input.StylusPoint> 資料的值。  
  
> [!CAUTION]
> 如果 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 擲回或造成例外狀況，應用程式將會關閉。 您應該徹底測試使用 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 的控制項，而且只有在您確定 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 不會擲回例外狀況時，才使用控制項。  
  
 下列範例示範的外掛程式會藉由修改來自 <xref:System.Windows.Input.Stylus> 裝置的 <xref:System.Windows.Input.StylusPoint> 資料中的 <xref:System.Windows.Input.StylusPoint.X%2A> 和 <xref:System.Windows.Input.StylusPoint.Y%2A> 值，來限制手寫筆輸入。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>將外掛程式新增至 InkCanvas  
 使用您的自訂外掛程式最簡單的方式，就是執行衍生自 InkCanvas 的類別，並將它新增至 <xref:System.Windows.UIElement.StylusPlugIns%2A> 屬性。  
  
 下列範例示範用來篩選筆墨的自訂 <xref:System.Windows.Controls.InkCanvas>。  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 如果您將 `FilterInkCanvas` 新增至應用程式並加以執行，您會注意到，在使用者完成筆劃之前，筆跡不會限制為區域。 這是因為 <xref:System.Windows.Controls.InkCanvas> 具有 <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> 屬性，這是 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>，而且已經是 <xref:System.Windows.UIElement.StylusPlugIns%2A> 集合的成員。 您在 <xref:System.Windows.UIElement.StylusPlugIns%2A> 集合中新增的自訂 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 會在 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 接收資料之後收到 <xref:System.Windows.Input.StylusPoint> 的資料。 因此，在使用者提起畫筆以結束筆劃之前，不會篩選 <xref:System.Windows.Input.StylusPoint> 的資料。 若要在使用者繪製時篩選筆墨，您必須在 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>之前插入 `FilterPlugin`。  
  
 下列C#程式碼示範的自訂 <xref:System.Windows.Controls.InkCanvas> 會在繪製時篩選筆墨。  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>結論  
 藉由衍生您自己的 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 類別，並將它們插入 <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> 集合中，您可以大幅增強數位筆跡的行為。 您可以存取所產生的 <xref:System.Windows.Input.StylusPoint> 資料，讓您有機會自訂 <xref:System.Windows.Input.Stylus> 輸入。 因為您有 <xref:System.Windows.Input.StylusPoint> 資料的低層級存取權，所以您可以使用應用程式的最佳效能來執行筆墨集合和轉譯。  
  
## <a name="see-also"></a>另請參閱

- [筆跡進階處理](advanced-ink-handling.md)
- [存取和操作手寫筆輸入](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))
