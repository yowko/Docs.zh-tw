---
title: 如何：使用程式碼加入事件處理常式
description: 使用此範例來瞭解如何使用程式碼，將事件處理常式新增至 Windows Presentation Foundation 中的專案，而不是使用 XAML 來宣告。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: b36969f7a65ccbf6c9d03b22767d9eacdc177ad1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166370"
---
# <a name="how-to-add-an-event-handler-using-code"></a>如何：使用程式碼加入事件處理常式
這個範例示範如何使用程式碼，將事件處理常式新增至專案。  
  
 如果您想要將事件處理常式加入至專案 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，而且已經載入包含該專案的標記頁面，則必須使用程式碼加入處理常式。 或者，如果您要完全使用程式碼來建立應用程式的專案樹狀結構，而不使用宣告任何專案 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，您可以呼叫特定方法，將事件處理常式加入至結構化專案樹狀結構。  
  
## <a name="example"></a>範例  
 下列範例會將新的加入 <xref:System.Windows.Controls.Button> 至一開始在中定義的現有頁面 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。 程式碼後置檔案會執行事件處理常式方法，然後在上加入該方法做為新的事件處理常式 <xref:System.Windows.Controls.Button> 。  
  
 C # 範例會使用 `+=` 運算子來指派事件的處理常式。 這是用來在 common language runtime （CLR）事件處理模型中指派處理常式的相同運算子。 Microsoft Visual Basic 不支援此運算子做為新增事件處理常式的方法。 而是需要下列其中一種技術：  
  
- 搭配使用 <xref:System.Windows.UIElement.AddHandler%2A> 方法與 `AddressOf` 運算子，以參考事件處理常式的執行。  
  
- 使用 `Handles` 關鍵字做為事件處理常式定義的一部分。 這裡不會顯示這項技術;請參閱[Visual Basic 和 WPF 事件處理](visual-basic-and-wpf-event-handling.md)。  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
> 在初始剖析的頁面中新增事件處理常式 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 會簡單許多。 在您要加入事件處理常式的物件專案中，加入與您要處理的事件名稱相符的屬性。 然後指定該屬性的值，做為您在頁面的程式碼後置檔案中定義的事件處理常式方法的名稱 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。 如需詳細資訊，請參閱[XAML 總覽（WPF）](../../../desktop-wpf/fundamentals/xaml.md)或[路由事件總覽](routed-events-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [路由事件概觀](routed-events-overview.md)
- [操作說明主題](events-how-to-topics.md)
