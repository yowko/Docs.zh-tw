---
title: HOW TO：在屬性值變更時觸發動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
ms.openlocfilehash: 7e3eecedf7d464eeb8e4f60f2f05fa06d2e23e09
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769300"
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a>HOW TO：在屬性值變更時觸發動畫
此範例示範如何使用<xref:System.Windows.Trigger>啟動<xref:System.Windows.Media.Animation.Storyboard>屬性值變更時。 您可以使用<xref:System.Windows.Trigger>內<xref:System.Windows.Style>， <xref:System.Windows.Controls.ControlTemplate>，或<xref:System.Windows.DataTemplate>。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Trigger>來建立動畫<xref:System.Windows.UIElement.Opacity%2A>的<xref:System.Windows.Controls.Button>當其<xref:System.Windows.UIElement.IsMouseOver%2A>屬性會變成`true`。  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 套用屬性的動畫<xref:System.Windows.Trigger>物件的行為更複雜的方式比<xref:System.Windows.EventTrigger>動畫開始使用<xref:System.Windows.Media.Animation.Storyboard>方法。  這些 「 傳遞 」 與動畫定義其他<xref:System.Windows.Trigger>物件，但以此撰寫<xref:System.Windows.EventTrigger>和方法觸發動畫。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Trigger>
- [屬性動畫技術概觀](property-animation-techniques-overview.md)
- [分鏡腳本概觀](storyboards-overview.md)
