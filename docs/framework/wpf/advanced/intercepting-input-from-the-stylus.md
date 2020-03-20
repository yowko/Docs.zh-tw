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
ms.openlocfilehash: 17cf42a9d6d94d6ea12399561af5647df3b4d8c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181923"
---
# <a name="intercepting-input-from-the-stylus"></a>攔截手寫筆的輸入
該<xref:System.Windows.Input.StylusPlugIns>體系結構為實現對<xref:System.Windows.Input.Stylus>輸入的低級控制和創建數位筆跡<xref:System.Windows.Ink.Stroke>物件提供了一種機制。 該<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>類提供了一種機制，用於實現自訂行為並將其應用於來自手寫筆設備的資料流程，以實現最佳性能。  
  
 本主題包含下列子章節：  
  
- [建築](#Architecture)  
  
- [實現手寫外掛程式](#ImplementingStylusPlugins)  
  
- [將外掛程式添加到 InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
- [結論](#Conclusion)  
  
<a name="Architecture"></a>
## <a name="architecture"></a>架構  
 是<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>[手寫輸入](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms574861(v=vs.90))API 的演變，在[訪問和操作筆輸入](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))中描述。  
  
 每個<xref:System.Windows.UIElement>都有一<xref:System.Windows.UIElement.StylusPlugIns%2A>個屬性是<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>。 您可以將 添加到<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>元素的屬性<xref:System.Windows.UIElement.StylusPlugIns%2A>以在生成資料時操作<xref:System.Windows.Input.StylusPoint>資料。 <xref:System.Windows.Input.StylusPoint>資料由系統數位化器支援的所有屬性組成，包括<xref:System.Windows.Input.StylusPoint.X%2A>和<xref:System.Windows.Input.StylusPoint.Y%2A>點資料以及<xref:System.Windows.Input.StylusPoint.PressureFactor%2A>資料。  
  
 將<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>的物件直接插入到設備<xref:System.Windows.Input.Stylus>的資料流程中，當您將 添加到<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>屬性時。 <xref:System.Windows.UIElement.StylusPlugIns%2A> 外掛程式添加到<xref:System.Windows.UIElement.StylusPlugIns%2A>集合的順序決定了它們接收<xref:System.Windows.Input.StylusPoint>資料的順序。 例如，如果添加篩選器外掛程式，將輸入限制到特定區域，然後添加一個外掛程式，在編寫手勢時識別手勢，則識別手勢的外掛程式將收到篩選<xref:System.Windows.Input.StylusPoint>的資料。  
  
<a name="ImplementingStylusPlugins"></a>
## <a name="implementing-stylus-plug-ins"></a>實現手寫外掛程式  
 要實現外掛程式，請從<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>派生類。 類應用 o 資料流程，因為它來自 。 <xref:System.Windows.Input.Stylus> 在此類中，您可以修改<xref:System.Windows.Input.StylusPoint>資料的值。  
  
> [!CAUTION]
> 如果<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>引發或導致異常，應用程式將關閉。 應徹底測試使用 和<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>僅在您確定 不會引發異常時才使用控制項<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>的控制項。  
  
 下面的示例演示了一個外掛程式，該<xref:System.Windows.Input.StylusPoint.X%2A>外掛程式通過修改<xref:System.Windows.Input.StylusPoint.Y%2A><xref:System.Windows.Input.StylusPoint>資料中的 和 值來限制手寫筆輸入。<xref:System.Windows.Input.Stylus>因為資料來自設備。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>將外掛程式添加到 InkCanvas  
 使用自訂外掛程式的最簡單方法是實現從 InkCanvas 派生的類並將其添加到<xref:System.Windows.UIElement.StylusPlugIns%2A>屬性。  
  
 下面的示例演示了篩選墨<xref:System.Windows.Controls.InkCanvas>跡的自訂。  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 如果向應用程式添加`FilterInkCanvas`並運行它，您會注意到，在使用者完成筆劃之前，墨蹟不會局限于區域。 這是因為<xref:System.Windows.Controls.InkCanvas>具有 屬性<xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>，該屬性是<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>，並且已經是<xref:System.Windows.UIElement.StylusPlugIns%2A>集合的成員。 添加到集合<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>中的<xref:System.Windows.UIElement.StylusPlugIns%2A>自訂在接收資料後<xref:System.Windows.Input.StylusPoint><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>接收資料。 因此，<xref:System.Windows.Input.StylusPoint>在使用者抬起筆以結束筆劃之前，資料才會被篩選。 若要在使用者繪製墨蹟時篩選墨蹟，必須在 之前`FilterPlugin`<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>插入 。  
  
 以下 C# 代碼演示了<xref:System.Windows.Controls.InkCanvas>在繪製墨蹟時篩選墨蹟的自訂。  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>
## <a name="conclusion"></a>結論  
 通過派生自己的<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>類並將其插入到集合中<xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>，可以極大地增強數位筆跡的行為。 您可以在生成<xref:System.Windows.Input.StylusPoint>資料時訪問資料，從而有機會自訂<xref:System.Windows.Input.Stylus>輸入。 由於您對<xref:System.Windows.Input.StylusPoint>資料具有如此低級別的訪問，因此可以實現墨蹟收集和呈現，從而為您的應用程式提供最佳性能。  
  
## <a name="see-also"></a>另請參閱

- [筆墨進階處理](advanced-ink-handling.md)
- [訪問和操作筆輸入](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))
