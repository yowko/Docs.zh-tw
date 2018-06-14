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
ms.openlocfilehash: 7e67fb07a05d474999515a678fd72ac6b96953c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561068"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>操作說明：使用分鏡腳本建立屬性的動畫
這個範例示範如何使用<xref:System.Windows.Media.Animation.Storyboard>以動畫方式顯示屬性。 若要建立屬性的動畫使用<xref:System.Windows.Media.Animation.Storyboard>，建立您想要建立動畫，並建立每一個屬性的動畫<xref:System.Windows.Media.Animation.Storyboard>包含動畫。  
  
 屬性類型會決定要使用的動畫類型。 例如，若要建立採用屬性的動畫<xref:System.Double>值，會使用<xref:System.Windows.Media.Animation.DoubleAnimation>。 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>和<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>附加的屬性指定的物件和動畫已套用的屬性。  
  
 若要以啟動分鏡腳本[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，使用<xref:System.Windows.Media.Animation.BeginStoryboard>動作和<xref:System.Windows.EventTrigger>。 <xref:System.Windows.EventTrigger>開始<xref:System.Windows.Media.Animation.BeginStoryboard>動作時，事件是由其<xref:System.Windows.EventTrigger.RoutedEvent%2A>屬性，就會發生。 <xref:System.Windows.Media.Animation.BeginStoryboard>動作啟動<xref:System.Windows.Media.Animation.Storyboard>。  
  
 下列範例會使用<xref:System.Windows.Media.Animation.Storyboard>以動畫方式顯示兩個物件<xref:System.Windows.Controls.Button>控制項。 若要讓第一個按鈕大小，變更其<xref:System.Windows.FrameworkElement.Width%2A>的動畫。 若要讓變更色彩，第二個按鈕<xref:System.Windows.Media.SolidColorBrush.Color%2A>屬性<xref:System.Windows.Media.SolidColorBrush>用來設定<xref:System.Windows.Controls.Control.Background%2A>展示動畫的按鈕。  
  
## <a name="example"></a>範例  
 [!code-xaml[AnimatePropertyStoryboards#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
>  雖然動畫可鎖定目標兩者<xref:System.Windows.FrameworkElement>物件，例如<xref:System.Windows.Controls.Control>或<xref:System.Windows.Controls.Panel>，和<xref:System.Windows.Freezable>物件，例如<xref:System.Windows.Media.Brush>或<xref:System.Windows.Media.Transform>，只有架構項目的<xref:System.Windows.FrameworkElement.Name%2A>屬性。 若要將名稱指派給 Freezable，讓它可以成為動畫目標，請使用 [X:name 指示詞](../../../../docs/framework/xaml-services/x-name-directive.md)，如先前範例所示。  
  
 如果您使用程式碼，您必須建立<xref:System.Windows.NameScope>如<xref:System.Windows.FrameworkElement>並註冊以動畫方式顯示與該物件的名稱<xref:System.Windows.FrameworkElement>。 若要在程式碼中啟動動畫，請使用<xref:System.Windows.Media.Animation.BeginStoryboard>動作<xref:System.Windows.EventTrigger>。 （選擇性） 您可以使用事件處理常式和<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法<xref:System.Windows.Media.Animation.Storyboard>。 下列範例會示範如何使用 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法。  
  
 [!code-csharp[AnimatePropertyStoryboards#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 如需動畫和分鏡腳本的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
 如果您使用程式碼，您不一定要使用<xref:System.Windows.Media.Animation.Storyboard>以動畫顯示屬性的物件。 如需詳細資訊和範例，請參閱[不使用分鏡腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)和[使用 AnimationClock 建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-an-animationclock.md)。
