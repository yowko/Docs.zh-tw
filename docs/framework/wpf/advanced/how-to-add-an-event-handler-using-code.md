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
ms.openlocfilehash: 457b8cf5c68096b20df7fe39f1cc3f40358f34d0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460435"
---
# <a name="how-to-add-an-event-handler-using-code"></a>如何：使用程式碼加入事件處理常式
這個範例示範如何使用程式碼，將事件處理常式新增至專案。  
  
 如果您想要將事件處理常式加入至 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 專案，而且已經載入包含該專案的標記頁面，則必須使用程式碼加入處理常式。 或者，如果您要完全使用程式碼來建立應用程式的專案樹狀結構，而不使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]宣告任何專案，您可以呼叫特定方法，將事件處理常式加入至結構化專案樹狀結構。  
  
## <a name="example"></a>範例  
 下列範例會將新的 <xref:System.Windows.Controls.Button> 新增至 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中一開始定義的現有頁面。 程式碼後置檔案會執行事件處理常式方法，然後在 <xref:System.Windows.Controls.Button>上加入該方法做為新的事件處理常式。  
  
 此C#範例會使用 `+=` 運算子來指派事件的處理常式。 這是用來在 common language runtime （CLR）事件處理模型中指派處理常式的相同運算子。 Microsoft Visual Basic 不支援此運算子做為新增事件處理常式的方法。 而是需要下列其中一種技術：  
  
- 搭配使用 <xref:System.Windows.UIElement.AddHandler%2A> 方法與 `AddressOf` 運算子，以參考事件處理常式的執行。  
  
- 請使用 `Handles` 關鍵字做為事件處理常式定義的一部分。 這裡不會顯示這項技術;請參閱[Visual Basic 和 WPF 事件處理](visual-basic-and-wpf-event-handling.md)。  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
> 在初始剖析的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面中新增事件處理常式會簡單許多。 在您要加入事件處理常式的物件專案中，加入與您要處理的事件名稱相符的屬性。 然後指定該屬性的值，做為您在 [[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]] 頁面的程式碼後置檔案中定義的事件處理常式方法的名稱。 如需詳細資訊，請參閱[XAML 總覽（WPF）](../../../desktop-wpf/fundamentals/xaml.md)或[路由事件總覽](routed-events-overview.md)。  
  
## <a name="see-also"></a>請參閱

- [路由事件概觀](routed-events-overview.md)
- [「如何」主題](events-how-to-topics.md)
