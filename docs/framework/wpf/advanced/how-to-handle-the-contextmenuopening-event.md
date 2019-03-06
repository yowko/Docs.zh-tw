---
title: HOW TO：處理 ContextMenuOpening 事件
ms.date: 03/30/2017
helpviewer_keywords:
- ContextMenuOpening properties [WPF]
ms.assetid: 789652fb-1951-4217-934a-7843e355adf4
ms.openlocfilehash: 077a28f345b886fd9ec183b5828c0535ce688cb4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364836"
---
# <a name="how-to-handle-the-contextmenuopening-event"></a>HOW TO：處理 ContextMenuOpening 事件
<xref:System.Windows.FrameworkElement.ContextMenuOpening>可以調整現有內容功能表之前以顯示或隱藏的功能表，否則會顯示藉由設定應用程式中處理事件<xref:System.Windows.RoutedEventArgs.Handled%2A>屬性設`true`事件資料中。 設定的一般原因<xref:System.Windows.RoutedEventArgs.Handled%2A>要`true`在事件資料就是把完全與新的功能表<xref:System.Windows.Controls.ContextMenu>物件時，有時需要取消作業，並啟動新的開放。 如果您撰寫處理常式<xref:System.Windows.FrameworkElement.ContextMenuOpening>事件，您應該留意之間的計時問題<xref:System.Windows.Controls.ContextMenu>控制項和負責開啟並定位操作功能表控制項的一般服務。 本主題說明一些不同的內容功能表開啟案例的程式碼技術，並說明其中計時問題派上用場的情況。  
  
 有數種案例處理<xref:System.Windows.FrameworkElement.ContextMenuOpening>事件：  
  
-   調整之前顯示的功能表項目。  
  
-   取代整個功能表之前顯示。  
  
-   完全隱藏任何現有的內容功能表，並不顯示任何內容功能表。  
  
## <a name="example"></a>範例  
  
## <a name="adjusting-the-menu-items-before-display"></a>調整之前顯示的功能表項目  
 調整現有的功能表項目相當簡單，可能是最常見的案例。 您可能會這麼做以增加或減少以回應您的應用程式中的目前狀態資訊或可從要求的操作功能表的其中的物件上的屬性的特定狀態資訊的快顯功能表選項。  
  
 常用的技巧是要取得事件的來源，也就是以滑鼠右鍵按一下特定控制項，並取得<xref:System.Windows.FrameworkElement.ContextMenu%2A>從它的屬性。 您通常想要檢查<xref:System.Windows.Controls.ItemsControl.Items%2A>若要查看哪些內容功能表項目已經存在的功能表中，然後新增或移除適當的新集合<xref:System.Windows.Controls.MenuItem>或從集合項目。  
  
 [!code-csharp[ContextMenuOpeningHandlers#AddItemNoHandle](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#additemnohandle)]  
  
## <a name="replacing-the-entire-menu-before-display"></a>取代之前顯示的整個功能表  
 替代的情況是如果您想要取代整個快顯功能表。 然後，您也可以不用說使用一種變化的上述程式碼中，移除現有的內容功能表中的每個項目，並加入新項目零開始。 取代操作功能表中的所有項目更具直覺性的方法是建立新的但是<xref:System.Windows.Controls.ContextMenu>，填入項目，然後設定<xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>是新的控制項屬性<xref:System.Windows.Controls.ContextMenu>。  
  
 以下是簡單的處理常式程式碼取代<xref:System.Windows.Controls.ContextMenu>。 程式碼參考自訂`BuildMenu`方法，它都會以分隔出因為它會呼叫一個以上的範例處理常式。  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceNoReopen](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacenoreopen)]  
  
 [!code-csharp[ContextMenuOpeningHandlers#BuildMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#buildmenu)]  
  
 不過，如果您使用這種處理常式<xref:System.Windows.FrameworkElement.ContextMenuOpening>，您可能可以公開計時問題，如果您要在此對話方塊設定物件<xref:System.Windows.Controls.ContextMenu>並沒有預先存在的內容功能表。 當使用者以滑鼠右鍵按一下控制項時，<xref:System.Windows.FrameworkElement.ContextMenuOpening>就會引發即使現有<xref:System.Windows.Controls.ContextMenu>為空白或 null。 但在此情況下，任何新<xref:System.Windows.Controls.ContextMenu>您在來源上設定項目太晚抵達時顯示。 此外，如果使用者以滑鼠右鍵按一下第二次，這次您的新<xref:System.Windows.Controls.ContextMenu>出現時，值為非 null，而且您的處理常式會適當地取代時的處理常式會執行第二次顯示功能表。 這可能表示兩個可能的因應措施：  
  
1.  確保<xref:System.Windows.FrameworkElement.ContextMenuOpening>永遠有至少一個預留位置控制項針對執行的處理常式<xref:System.Windows.Controls.ContextMenu>可用，您想要的處理常式程式碼取代它。 在此案例中，您仍然可以使用先前的範例所示的處理常式，但您通常想要指派預留位置<xref:System.Windows.Controls.ContextMenu>在初始標記：  
  
     [!code-xaml[ContextMenuOpeningHandlers#XAMLWithInitCM](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml#xamlwithinitcm)]  
  
2.  假設初始<xref:System.Windows.Controls.ContextMenu>值可能為 null，根據一些初步的邏輯。 您可以核取<xref:System.Windows.Controls.ContextMenu>null，或使用您的程式碼，以檢查是否已經過您的處理常式中的旗標執行至少一次。 因為您假設<xref:System.Windows.Controls.ContextMenu>即將要顯示，您的處理常式，則會將<xref:System.Windows.RoutedEventArgs.Handled%2A>到`true`事件資料中。 若要<xref:System.Windows.Controls.ContextMenuService>負責內容功能表顯示時，`true`值<xref:System.Windows.RoutedEventArgs.Handled%2A>資料在事件代表要求取消的顯示內容功能表 / 控制引發事件的組合。  
  
 現在您已隱藏的潛在可疑的操作功能表，下一個步驟是提供新的連線，然後顯示它。 設定新的其中一個基本上是前一個處理常式一樣： 您建立新<xref:System.Windows.Controls.ContextMenu>並設定控制項資料來源的<xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>與其屬性。 額外的步驟是，您現在必須強制的操作功能表中，顯示因為抑制第一次嘗試。 若要強制顯示，您將<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A?displayProperty=nameWithType>屬性設`true`處理常式內。 請小心時這樣做，因為開啟內容功能表處理常式中引發<xref:System.Windows.FrameworkElement.ContextMenuOpening>事件一次。 如果您重新輸入您的處理常式，它就會變成無限遞迴。 這就是為什麼您一定要檢查是否有`null`或使用旗標，如果您開啟內容功能表內<xref:System.Windows.FrameworkElement.ContextMenuOpening>事件處理常式。  
  
## <a name="suppressing-any-existing-context-menu-and-displaying-no-context-menu"></a>隱藏任何現有的內容功能表，並不顯示任何內容功能表  
 最後一個案例中，撰寫完全，隱藏功能表處理常式不常見。 如果指定的控制項不應該顯示操作功能表，有可能會更適當的方法，以確保這比藉由只在使用者要求時，隱藏功能表。 但如果您想要使用的處理常式，以隱藏內容功能表，並顯示任何內容，則應該只會設定您的處理常式<xref:System.Windows.RoutedEventArgs.Handled%2A>至`true`事件資料中。 <xref:System.Windows.Controls.ContextMenuService> ，負責顯示內容功能表將會檢查其在控制項引發的事件的事件資料。 如果事件已標示為<xref:System.Windows.RoutedEventArgs.Handled%2A>隨處在路由中，然後內容功能表開啟動作，起始事件隱藏。  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceReopen](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacereopen)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>
- [基底項目概觀](base-elements-overview.md)
- [ContextMenu 概觀](../controls/contextmenu-overview.md)
