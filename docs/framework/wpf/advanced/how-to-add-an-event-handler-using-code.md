---
title: HOW TO：使用程式碼新增事件處理常式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: 32e3926bb4c519b7be14a26484603d6d4ea88b6a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665801"
---
# <a name="how-to-add-an-event-handler-using-code"></a>HOW TO：使用程式碼新增事件處理常式
此範例示範如何使用程式碼，將事件處理常式新增至項目。  
  
 如果您想要新增事件處理常式[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]項目和包含的項目 [標記] 頁面已載入，您必須新增處理常式，使用程式碼。 或者，如果您正在建置應用程式完全使用程式碼和未宣告任何項目使用的項目樹狀結構中向上[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您可以呼叫特定方法，將事件處理常式新增至建構的項目樹狀結構。  
  
## <a name="example"></a>範例  
 下列範例會將新<xref:System.Windows.Controls.Button>至現有的頁面，一開始會定義在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 程式碼後置檔案會實作事件處理常式方法和上，然後將該方法新增為新的事件處理常式<xref:System.Windows.Controls.Button>。  
  
 C#範例會使用`+=`運算子來指派到的事件處理常式。 這是用來指派中的處理常式的相同運算子[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]事件處理模型。 Microsoft Visual Basic 不支援這個運算子，來加入事件處理常式。 它需要使用兩種技術之一：  
  
- 使用<xref:System.Windows.UIElement.AddHandler%2A>方法，連同`AddressOf`運算子，以便參考事件處理常式實作。  
  
- 使用`Handles`關鍵字做為事件處理常式定義的一部分。 這項技術不討論;請參閱[Visual Basic 和 WPF 事件處理](visual-basic-and-wpf-event-handling.md)。  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  加入事件處理常式中一開始剖析[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面是更簡單。 在您要加入事件處理常式的物件項目，新增符合您想要處理的事件名稱的屬性。 然後指定該屬性的值，做為您的程式碼後置檔案中定義的事件處理常式方法名稱[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面。 如需詳細資訊，請參閱 < [XAML 概觀 (WPF)](xaml-overview-wpf.md)或是[路由事件概觀](routed-events-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [路由事件概觀](routed-events-overview.md)
- [HOW-TO 主題](events-how-to-topics.md)
