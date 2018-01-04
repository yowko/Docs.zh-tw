---
title: "如何：處理 ContextMenuOpening 事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ContextMenuOpening properties [WPF]
ms.assetid: 789652fb-1951-4217-934a-7843e355adf4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5eec8646a48f94fb9ffdcad14849416732618a06
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-the-contextmenuopening-event"></a>如何：處理 ContextMenuOpening 事件
<xref:System.Windows.FrameworkElement.ContextMenuOpening>可以處理事件，或是調整現有內容功能表之前，顯示或隱藏的功能表會顯示藉由設定應用程式中<xref:System.Windows.RoutedEventArgs.Handled%2A>屬性`true`事件資料。 設定的一般原因<xref:System.Windows.RoutedEventArgs.Handled%2A>至`true`在事件資料的取代完全與新的功能表<xref:System.Windows.Controls.ContextMenu>物件，有時需要取消作業並啟動新的開啟。 如果您撰寫處理常式<xref:System.Windows.FrameworkElement.ContextMenuOpening>事件，您應該留意之間的時間問題<xref:System.Windows.Controls.ContextMenu>控制項和服務負責開啟並定位操作功能表控制項的一般情況下。 本主題說明一些不同的內容功能表開啟案例的程式碼技術，並將說明其中時間問題派上用場的情況。  
  
 有幾種情況，處理<xref:System.Windows.FrameworkElement.ContextMenuOpening>事件：  
  
-   調整顯示器之前的功能表項目。  
  
-   取代整個功能表顯示之前。  
  
-   完全隱藏任何現有的內容功能表，並不顯示任何內容功能表。  
  
## <a name="example"></a>範例  
  
## <a name="adjusting-the-menu-items-before-display"></a>調整顯示器之前的功能表項目  
 調整現有的功能表項目相當簡單，可能是最常見的案例。 您可能會執行這項操作才能新增或刪減內容功能表選項，以回應您的應用程式中的目前狀態資訊或可為要求的操作功能表所在之物件的屬性特定的狀態資訊。  
  
 一般的技巧是取得事件的來源，也就是已右鍵特定控制項，以及取得<xref:System.Windows.FrameworkElement.ContextMenu%2A>從它的屬性。 您通常想要檢查<xref:System.Windows.Controls.ItemsControl.Items%2A>集合，查看哪些內容功能表項目已經存在於功能表，然後新增或移除適當新<xref:System.Windows.Controls.MenuItem>或集合的項目。  
  
 [!code-csharp[ContextMenuOpeningHandlers#AddItemNoHandle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#additemnohandle)]  
  
## <a name="replacing-the-entire-menu-before-display"></a>取代整個之前顯示功能表  
 替代的情況是如果您想要取代整個內容功能表。 然後，您也可以當然使用上述的程式碼的變化來移除現有的內容功能表中的每個項目並加入新的開頭為零的項目。 但更直覺的方法取代內容功能表中的所有項目是建立新<xref:System.Windows.Controls.ContextMenu>，填入項目，然後設定<xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>屬性的新控制項<xref:System.Windows.Controls.ContextMenu>。  
  
 以下是簡單的處理常式程式碼取代<xref:System.Windows.Controls.ContextMenu>。 程式碼參考自訂`BuildMenu`方法，會以區隔出因為它會呼叫一個以上的範例處理常式。  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceNoReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacenoreopen)]  
  
 [!code-csharp[ContextMenuOpeningHandlers#BuildMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#buildmenu)]  
  
 不過，如果您使用這種樣式的處理常式<xref:System.Windows.FrameworkElement.ContextMenuOpening>，您可能可以公開的時間問題，如果您要在此對話方塊設定物件<xref:System.Windows.Controls.ContextMenu>並沒有預先存在的內容功能表。 當使用者以滑鼠右鍵按一下控制項，<xref:System.Windows.FrameworkElement.ContextMenuOpening>引發即使現有<xref:System.Windows.Controls.ContextMenu>為空白或 null。 但在此情況下，任何新<xref:System.Windows.Controls.ContextMenu>您在來源上設定項目太晚抵達時顯示。 此外，如果使用者以滑鼠右鍵按一下第二次，這次您的新<xref:System.Windows.Controls.ContextMenu>出現時，值為非 null，而且您的處理常式會正確取代並時的處理常式會執行第二次顯示功能表。 這可能表示兩個可能的因應措施：  
  
1.  確保<xref:System.Windows.FrameworkElement.ContextMenuOpening>一律針對具有至少一個預留位置的控制項執行的處理常式<xref:System.Windows.Controls.ContextMenu>可用，其中您想要取代的處理常式程式碼。 在此情況下，您仍然可以使用前一個範例所示的處理常式，但您通常想要指派預留位置<xref:System.Windows.Controls.ContextMenu>在初始標記中：  
  
     [!code-xaml[ContextMenuOpeningHandlers#XAMLWithInitCM](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml#xamlwithinitcm)]  
  
2.  假設初始<xref:System.Windows.Controls.ContextMenu>值可能是 null，根據一些初步的邏輯。 您可以查看<xref:System.Windows.Controls.ContextMenu>null，或使用的旗標來檢查是否已被您的處理常式程式碼中至少執行一次。 因為您假設<xref:System.Windows.Controls.ContextMenu>即將要顯示，您的處理常式，然後設定<xref:System.Windows.RoutedEventArgs.Handled%2A>至`true`事件資料。 若要<xref:System.Windows.Controls.ContextMenuService>負責內容功能表上顯示，`true`值<xref:System.Windows.RoutedEventArgs.Handled%2A>事件中的資料代表的要求取消的顯示內容功能表 / 控制引發事件的組合。  
  
 現在您已隱藏的潛在問題的內容功能表，下一個步驟是提供一個新加以顯示。 設定新的是基本上與前一個處理常式相同： 建置新<xref:System.Windows.Controls.ContextMenu>和設定控制項來源<xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>與其屬性。 額外的步驟是，您現在必須強制顯示的內容功能表中，因為隱藏第一次嘗試。 若要強制顯示，您將<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A?displayProperty=nameWithType>屬性`true`在處理常式。 請小心時這樣做，因為開啟內容功能表處理常式中引發<xref:System.Windows.FrameworkElement.ContextMenuOpening>事件一次。 如果您重新輸入您的處理常式，它就會變成無限遞迴。 這就是為什麼您一定要先檢查`null`使用旗標，如果您從 內開啟內容功能表或<xref:System.Windows.FrameworkElement.ContextMenuOpening>事件處理常式。  
  
## <a name="suppressing-any-existing-context-menu-and-displaying-no-context-menu"></a>隱藏任何現有的內容功能表，並不顯示任何內容功能表  
 最後一個案例中，撰寫完全，隱藏功能表處理常式是常見的。 如果指定的控制項不應該顯示操作功能表中，有可能更適當的方法，以確保這比只在使用者要求時隱藏功能表。 但如果您想要隱藏的內容功能表，並顯示任何內容，使用處理常式，則您的處理常式應該只設定<xref:System.Windows.RoutedEventArgs.Handled%2A>至`true`事件資料。 <xref:System.Windows.Controls.ContextMenuService> ，負責顯示內容功能表會檢查它在控制項引發的事件的事件資料。 如果事件已標示為<xref:System.Windows.RoutedEventArgs.Handled%2A>任何位置路徑，然後內容功能表開啟動作起始事件已隱藏。  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacereopen)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>  
 [基底項目概觀](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [ContextMenu 概觀](../../../../docs/framework/wpf/controls/contextmenu-overview.md)
