---
title: 如何：使用程式碼加入事件處理常式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: 782f668557c3cb081d30e7835006af63c9ca4df5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542619"
---
# <a name="how-to-add-an-event-handler-using-code"></a>如何：使用程式碼加入事件處理常式
這個範例示範如何使用程式碼，將事件處理常式加入至項目。  
  
 如果您想要加入事件處理常式[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]項目，並包含元素的標記頁面已載入，則必須新增使用程式碼的處理常式。 或者，如果您要建置應用程式完全使用程式碼和未宣告的任何項目使用的項目樹狀結構向上[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您可以呼叫至建構的項目樹狀結構中加入事件處理常式的特定方法。  
  
## <a name="example"></a>範例  
 下列範例會將新<xref:System.Windows.Controls.Button>到現有的頁面中一開始定義[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 實作事件處理常式方法的程式碼後置檔案，並再將該方法做為新的事件處理常式加入上<xref:System.Windows.Controls.Button>。  
  
 C# 範例會使用`+=`運算子來指派到的事件處理常式。 這是用來指派中的處理常式的相同運算子[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]事件處理模型。 Microsoft Visual Basic 不支援此運算子來加入事件處理常式。 它需要使用兩種技術的其中一個：  
  
-   使用<xref:System.Windows.UIElement.AddHandler%2A>方法搭配`AddressOf`運算子，以便參考的事件處理常式實作。  
  
-   使用`Handles`關鍵字做為事件處理常式定義的一部分。 這項技術不如下所示。請參閱[Visual Basic 和 WPF 的事件處理](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md)。  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  加入事件處理常式中一開始剖析[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面是更簡單。 在您要加入事件處理常式物件的項目，加入的屬性符合您想要處理之事件的名稱。 然後指定該屬性的值做為您的程式碼後置檔案中定義的事件處理常式方法名稱[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面。 如需詳細資訊，請參閱[XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)或[路由傳送事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
