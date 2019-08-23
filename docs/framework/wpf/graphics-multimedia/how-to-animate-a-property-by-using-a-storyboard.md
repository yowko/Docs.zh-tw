---
title: 作法：使用分鏡腳本建立屬性的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], Storyboards
- Storyboards [WPF], animation
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
ms.openlocfilehash: a7a2656d84d37d3e2726df009a07ccf29661df07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963035"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>HOW TO：使用分鏡腳本建立屬性的動畫
這個範例示範如何使用來建立<xref:System.Windows.Media.Animation.Storyboard>屬性的動畫。 若要使用<xref:System.Windows.Media.Animation.Storyboard>建立屬性的動畫, 請為您想要建立動畫的每個屬性建立動畫, 同時<xref:System.Windows.Media.Animation.Storyboard>建立以包含動畫。  
  
 屬性類型會決定要使用的動畫類型。 例如, 若要以動畫顯示接受<xref:System.Double>值的屬性, 請<xref:System.Windows.Media.Animation.DoubleAnimation>使用。 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 和<xref:System.Windows.Media.Animation.Storyboard.TargetProperty>附加屬性會指定要套用動畫的物件和屬性。  
  
 若要在中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]啟動分鏡腳本, 請<xref:System.Windows.Media.Animation.BeginStoryboard>使用<xref:System.Windows.EventTrigger>動作和。 會在其<xref:System.Windows.Media.Animation.BeginStoryboard> 屬性<xref:System.Windows.EventTrigger.RoutedEvent%2A>所指定的事件發生時開始動作。 <xref:System.Windows.EventTrigger> <xref:System.Windows.Media.Animation.BeginStoryboard>動作會<xref:System.Windows.Media.Animation.Storyboard>啟動。  
  
 下列範例會使用<xref:System.Windows.Media.Animation.Storyboard>物件來建立兩<xref:System.Windows.Controls.Button>個控制項的動畫。 若要讓第一個按鈕的大小變更, <xref:System.Windows.FrameworkElement.Width%2A>其會以動畫顯示。 若要讓第二個按鈕變更色彩<xref:System.Windows.Media.SolidColorBrush.Color%2A> , 的屬性<xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Controls.Control.Background%2A>會用來設定動畫按鈕的。  
  
## <a name="example"></a>範例  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
> <xref:System.Windows.FrameworkElement>雖然動畫可以同時以物件 (例如<xref:System.Windows.Controls.Control>或<xref:System.Windows.Media.Brush> <xref:System.Windows.Freezable> <xref:System.Windows.Controls.Panel>) 和物件 (例如或<xref:System.Windows.Media.Transform>) 為目標, 但只有 framework 元素具有<xref:System.Windows.FrameworkElement.Name%2A>屬性。 若要將名稱指派給 Freezable，讓它可以成為動畫目標，請使用 [X:name 指示詞](../../xaml-services/x-name-directive.md)，如先前範例所示。  
  
 如果您使用程式<xref:System.Windows.NameScope> <xref:System.Windows.FrameworkElement>代碼, 您必須<xref:System.Windows.FrameworkElement>為建立, 並註冊要以動畫顯示的物件名稱。 若要在程式<xref:System.Windows.Media.Animation.BeginStoryboard> <xref:System.Windows.EventTrigger>代碼中啟動動畫, 請使用動作搭配。 (選擇性) 您可以使用事件處理常式和<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>的<xref:System.Windows.Media.Animation.Storyboard>方法。 下列範例會示範如何使用 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法。  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 如需動畫和分鏡腳本的詳細資訊，請參閱[動畫概觀](animation-overview.md)。  
  
 如果您使用程式碼, 則不限於使用<xref:System.Windows.Media.Animation.Storyboard>物件來建立屬性的動畫。 如需詳細資訊和範例，請參閱[不使用分鏡腳本而建立屬性的動畫](how-to-animate-a-property-without-using-a-storyboard.md)和[使用 AnimationClock 建立屬性的動畫](how-to-animate-a-property-by-using-an-animationclock.md)。
