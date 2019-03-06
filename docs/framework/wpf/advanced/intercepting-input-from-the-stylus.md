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
ms.openlocfilehash: 0568e72e6d686ce08e6bd802f273e45dd623524b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374306"
---
# <a name="intercepting-input-from-the-stylus"></a>攔截手寫筆的輸入
<xref:System.Windows.Input.StylusPlugIns>架構提供一個機制，透過實作的低階控制<xref:System.Windows.Input.Stylus>輸入和建立數位筆墨<xref:System.Windows.Ink.Stroke>物件。 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>類別會提供您實作自訂行為，並將它套用到來自手寫筆裝置，以獲得最佳的效能資料的資料流的機制。  
  
 本主題包含下列子章節：  
  
-   [架構](#Architecture)  
  
-   [實作的手寫筆外掛程式](#ImplementingStylusPlugins)  
  
-   [將外掛程式新增至 InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
-   [結論](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>架構  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>是的進化[StylusInput](https://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409)所述的 Api[存取和操作手寫筆輸入](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)中[Microsoft Windows XP Tablet PC Edition 軟體Development Kit 1.7](https://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409)。  
  
 每個<xref:System.Windows.UIElement>已經<xref:System.Windows.UIElement.StylusPlugIns%2A>屬於屬性<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>。 您可以加入<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>的項目<xref:System.Windows.UIElement.StylusPlugIns%2A>屬性來操作<xref:System.Windows.Input.StylusPoint>資料，因為它會產生。 <xref:System.Windows.Input.StylusPoint> 資料包含所有所支援的屬性系統潀糔蠮，包括<xref:System.Windows.Input.StylusPoint.X%2A>並<xref:System.Windows.Input.StylusPoint.Y%2A>點的資料，以及<xref:System.Windows.Input.StylusPoint.PressureFactor%2A>資料。  
  
 您<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>物件會直接插入到資料來源的資料流<xref:System.Windows.Input.Stylus>當您新增的裝置<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>到<xref:System.Windows.UIElement.StylusPlugIns%2A>屬性。 在其中加入外掛程式的順序<xref:System.Windows.UIElement.StylusPlugIns%2A>集合會指定將接收的順序<xref:System.Windows.Input.StylusPoint>資料。 比方說，如果您加入篩選外掛程式，將限制為特定區域中，輸入，然後新增 會辨識手勢，正在寫入的外掛程式，可辨識的筆勢的外掛程式將會收到篩選<xref:System.Windows.Input.StylusPoint>資料。  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>實作的手寫筆外掛程式  
 若要實作的外掛程式，衍生的類別<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>。 這個類別是套用的 i/o 資料流，因為它是來自<xref:System.Windows.Input.Stylus>。 在這個類別中，您可以修改的值<xref:System.Windows.Input.StylusPoint>資料。  
  
> [!CAUTION]
>  如果<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>會擲回，或造成例外狀況時，應用程式即將關閉。 您應該徹底測試使用的控制項<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>而且只能使用控制項，如果您確定<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>不會擲回例外狀況。  
  
 下列範例示範外掛程式，將手寫筆輸入限制藉由修改<xref:System.Windows.Input.StylusPoint.X%2A>並<xref:System.Windows.Input.StylusPoint.Y%2A>中的值<xref:System.Windows.Input.StylusPoint>資料，因為它是來自<xref:System.Windows.Input.Stylus>裝置。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>將外掛程式新增至 InkCanvas  
 若要使用您的自訂外掛程式的最簡單方式是實作衍生自 InkCanvas 類別，並將它加入<xref:System.Windows.UIElement.StylusPlugIns%2A>屬性。  
  
 下列範例示範自訂<xref:System.Windows.Controls.InkCanvas>篩選筆墨。  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 如果您新增`FilterInkCanvas`到您的應用程式並執行它，您會注意到使用者完成以筆劃後筆墨，不限於之前的區域。 這是因為<xref:System.Windows.Controls.InkCanvas>已<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>屬性，亦即<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>且已經隸屬<xref:System.Windows.UIElement.StylusPlugIns%2A>集合。 自訂<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>新增至您<xref:System.Windows.UIElement.StylusPlugIns%2A>集合接收<xref:System.Windows.Input.StylusPoint>後的資料<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>接收資料。 如此一來，<xref:System.Windows.Input.StylusPoint>資料將不會篩選直到使用者拿起畫筆筆觸的結束之後。 若要篩選使用者將它繪製筆墨，您必須插入`FilterPlugin`之前<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>。  
  
 下列 C# 程式碼示範了自訂<xref:System.Windows.Controls.InkCanvas>，篩選它是繪製的筆墨。  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>結論  
 藉由衍生您自己<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>類別和插入到<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>集合，即可大幅提高您的數位筆跡的行為。 您可以存取<xref:System.Windows.Input.StylusPoint>做為它產生的資料，讓您有機會自訂<xref:System.Windows.Input.Stylus>輸入。 因為您有這類低層級的存取權<xref:System.Windows.Input.StylusPoint>資料，您可以為您的應用程式實作筆跡收集和呈現以獲得最佳效能。  
  
## <a name="see-also"></a>另請參閱
- [筆跡進階處理](advanced-ink-handling.md)
- [存取和管理手寫筆輸入](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
