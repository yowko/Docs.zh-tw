---
title: 操作說明：使用分鏡腳本建立屬性的動畫
description: 使用 Windows Presentation Foundation （WPF）中屬性的動畫和分鏡腳本，Enliven 您的使用者介面。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], Storyboards
- Storyboards [WPF], animation
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
ms.openlocfilehash: f21b606751b845905a7bde6d3a7658b214369cc6
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853748"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>操作說明：使用分鏡腳本建立屬性的動畫
這個範例示範如何使用來建立 <xref:System.Windows.Media.Animation.Storyboard> 屬性的動畫。 若要使用建立屬性的動畫 <xref:System.Windows.Media.Animation.Storyboard> ，請為您想要建立動畫的每個屬性建立動畫，同時建立 <xref:System.Windows.Media.Animation.Storyboard> 以包含動畫。  
  
 屬性類型會決定要使用的動畫類型。 例如，若要以動畫顯示接受值的屬性 <xref:System.Double> ，請使用 <xref:System.Windows.Media.Animation.DoubleAnimation> 。 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>和 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> 附加屬性會指定要套用動畫的物件和屬性。  
  
 若要在中啟動分鏡腳本 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ，請使用 <xref:System.Windows.Media.Animation.BeginStoryboard> 動作和 <xref:System.Windows.EventTrigger> 。 <xref:System.Windows.EventTrigger> <xref:System.Windows.Media.Animation.BeginStoryboard> 會在其屬性所指定的事件發生時開始動作 <xref:System.Windows.EventTrigger.RoutedEvent%2A> 。 <xref:System.Windows.Media.Animation.BeginStoryboard>動作會啟動 <xref:System.Windows.Media.Animation.Storyboard> 。  
  
 下列範例會使用 <xref:System.Windows.Media.Animation.Storyboard> 物件來建立兩個 <xref:System.Windows.Controls.Button> 控制項的動畫。 若要讓第一個按鈕的大小變更，其 <xref:System.Windows.FrameworkElement.Width%2A> 會以動畫顯示。 若要讓第二個按鈕變更色彩，的 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 屬性 <xref:System.Windows.Media.SolidColorBrush> 會用來設定 <xref:System.Windows.Controls.Control.Background%2A> 動畫按鈕的。  
  
## <a name="example"></a>範例  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
> 雖然動畫可以同時以 <xref:System.Windows.FrameworkElement> 物件（例如 <xref:System.Windows.Controls.Control> 或 <xref:System.Windows.Controls.Panel> ）和物件（例如 <xref:System.Windows.Freezable> 或）為目標，但 <xref:System.Windows.Media.Brush> <xref:System.Windows.Media.Transform> 只有 framework 元素具有 <xref:System.Windows.FrameworkElement.Name%2A> 屬性。 若要將名稱指派給 Freezable，讓它可以成為動畫目標，請使用 [X:name 指示詞](../../../desktop-wpf/xaml-services/xname-directive.md)，如先前範例所示。  
  
 如果您使用程式碼，您必須 <xref:System.Windows.NameScope> 為建立， <xref:System.Windows.FrameworkElement> 並註冊要以動畫顯示的物件名稱 <xref:System.Windows.FrameworkElement> 。 若要在程式碼中啟動動畫，請使用 <xref:System.Windows.Media.Animation.BeginStoryboard> 動作搭配 <xref:System.Windows.EventTrigger> 。 （選擇性）您可以使用事件處理常式和的 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法 <xref:System.Windows.Media.Animation.Storyboard> 。 下列範例會示範如何使用 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法。  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 如需動畫和分鏡腳本的詳細資訊，請參閱[動畫概觀](animation-overview.md)。  
  
 如果您使用程式碼，則不限於使用 <xref:System.Windows.Media.Animation.Storyboard> 物件來建立屬性的動畫。 如需詳細資訊和範例，請參閱[不使用分鏡腳本而建立屬性的動畫](how-to-animate-a-property-without-using-a-storyboard.md)和[使用 AnimationClock 建立屬性的動畫](how-to-animate-a-property-by-using-an-animationclock.md)。
