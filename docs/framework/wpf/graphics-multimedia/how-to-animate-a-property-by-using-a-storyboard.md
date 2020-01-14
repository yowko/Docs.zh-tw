---
title: 操作說明：使用分鏡腳本建立屬性的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], Storyboards
- Storyboards [WPF], animation
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
ms.openlocfilehash: 6cfce9a5b070a23ed9ac03473888bf572b61393b
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559634"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>操作說明：使用分鏡腳本建立屬性的動畫
這個範例示範如何使用 <xref:System.Windows.Media.Animation.Storyboard> 來以動畫顯示內容。 若要使用 <xref:System.Windows.Media.Animation.Storyboard>建立屬性的動畫，請為您想要製作動畫的每個屬性建立動畫，同時建立 <xref:System.Windows.Media.Animation.Storyboard> 以包含動畫。  
  
 屬性類型會決定要使用的動畫類型。 例如，若要以動畫顯示採用 <xref:System.Double> 值的屬性，請使用 <xref:System.Windows.Media.Animation.DoubleAnimation>。 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 和 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> 附加屬性會指定要套用動畫的物件和屬性。  
  
 若要在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中啟動分鏡腳本，請使用 <xref:System.Windows.Media.Animation.BeginStoryboard> 動作和 <xref:System.Windows.EventTrigger>。 <xref:System.Windows.EventTrigger> 會在其 <xref:System.Windows.EventTrigger.RoutedEvent%2A> 屬性所指定的事件發生時，開始 <xref:System.Windows.Media.Animation.BeginStoryboard> 動作。 <xref:System.Windows.Media.Animation.BeginStoryboard> 動作會啟動 <xref:System.Windows.Media.Animation.Storyboard>。  
  
 下列範例會使用 <xref:System.Windows.Media.Animation.Storyboard> 物件來建立兩個 <xref:System.Windows.Controls.Button> 控制項的動畫。 若要讓第一個按鈕的大小變更，其 <xref:System.Windows.FrameworkElement.Width%2A> 會以動畫顯示。 若要讓第二個按鈕變更色彩，<xref:System.Windows.Media.SolidColorBrush> 的 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 屬性會用來設定動畫的按鈕 <xref:System.Windows.Controls.Control.Background%2A>。  
  
## <a name="example"></a>範例  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
> 雖然動畫可以同時以 <xref:System.Windows.FrameworkElement> 物件（例如 <xref:System.Windows.Controls.Control> 或 <xref:System.Windows.Controls.Panel>）和 <xref:System.Windows.Freezable> 物件（例如 <xref:System.Windows.Media.Brush> 或 <xref:System.Windows.Media.Transform>）為目標，但只有 framework 元素具有 <xref:System.Windows.FrameworkElement.Name%2A> 屬性。 若要將名稱指派給 Freezable，讓它可以成為動畫目標，請使用 [X:name 指示詞](../../../desktop-wpf/xaml-services/xname-directive.md)，如先前範例所示。  
  
 如果您使用程式碼，則必須建立 <xref:System.Windows.FrameworkElement> 的 <xref:System.Windows.NameScope>，並註冊物件的名稱，以建立該 <xref:System.Windows.FrameworkElement>的動畫。 若要在程式碼中啟動動畫，請搭配 <xref:System.Windows.EventTrigger>使用 <xref:System.Windows.Media.Animation.BeginStoryboard> 動作。 （選擇性）您可以使用事件處理常式和 <xref:System.Windows.Media.Animation.Storyboard>的 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法。 下列範例會示範如何使用 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法。  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 如需動畫和分鏡腳本的詳細資訊，請參閱[動畫概觀](animation-overview.md)。  
  
 如果您使用程式碼，則不限於使用 <xref:System.Windows.Media.Animation.Storyboard> 物件來建立屬性的動畫。 如需詳細資訊和範例，請參閱[不使用分鏡腳本而建立屬性的動畫](how-to-animate-a-property-without-using-a-storyboard.md)和[使用 AnimationClock 建立屬性的動畫](how-to-animate-a-property-by-using-an-animationclock.md)。
