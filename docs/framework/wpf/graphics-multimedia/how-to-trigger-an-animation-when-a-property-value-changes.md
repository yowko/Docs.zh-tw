---
title: "如何：當屬性值變更時觸發動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d722be0f0367f7e6e98ef1c8451ce58ee28fedd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a>如何：當屬性值變更時觸發動畫
這個範例示範如何使用<xref:System.Windows.Trigger>啟動<xref:System.Windows.Media.Animation.Storyboard>屬性值變更時。 您可以使用<xref:System.Windows.Trigger>內<xref:System.Windows.Style>， <xref:System.Windows.Controls.ControlTemplate>，或<xref:System.Windows.DataTemplate>。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Trigger>以動畫方式顯示<xref:System.Windows.UIElement.Opacity%2A>的<xref:System.Windows.Controls.Button>時其<xref:System.Windows.UIElement.IsMouseOver%2A>屬性變成`true`。  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 屬性所套用的動畫<xref:System.Windows.Trigger>物件的行為會以更複雜的方式比<xref:System.Windows.EventTrigger>動畫開始使用<xref:System.Windows.Media.Animation.Storyboard>方法。  這些 「 遞交"動畫定義其他<xref:System.Windows.Trigger>物件，但以此撰寫<xref:System.Windows.EventTrigger>和方法觸發動畫。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Trigger>  
 [屬性動畫技術概觀](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [分鏡腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
