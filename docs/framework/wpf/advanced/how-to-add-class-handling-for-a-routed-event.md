---
title: 如何：加入路由事件的類別處理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], class handlers
- task_core_add_class_handling_routed_properties [WPF]
- class handlers [WPF], routed events
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
ms.openlocfilehash: 85c3491c9035d807b4c654659a8641121bb5709f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545359"
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a>如何：加入路由事件的類別處理
依類別處理常式或路由中任何指定節點上的執行個體處理常式可以處理路由的事件。 首先，叫用與可用由類別實作來隱藏執行個體處理的事件，或引進其他事件的特定行為的基底類別所擁有的事件類別處理常式。 此範例說明兩種密切相關的技術，實作類別處理常式。  
  
## <a name="example"></a>範例  
 這個範例會使用為基礎的自訂類別<xref:System.Windows.Controls.Canvas>面板。 應用程式的基本前提是自訂類別引進了其子項目，包括攔截任何滑鼠左鍵按一下和標示為已處理，才能將叫用子系項目類別或在其上的任何執行個體處理常式上的行為。  
  
 <xref:System.Windows.UIElement>類別公開的虛擬方法，可讓類別處理<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>事件，只覆寫事件。 這是最簡單的方式來實作類別處理，如果您的類別階層中某處有虛擬方法。 下列程式碼會示範<xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A>"MyEditContainer"衍生自的類別中實作<xref:System.Windows.Controls.Canvas>。 實作會將事件標記為已處理的引數中，並將某些程式碼，讓來源項目的基本明顯的變更。  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 如果沒有虛擬基底類別或針對該特定的方法，可以直接使用的公用程式方法加入類別處理<xref:System.Windows.EventManager>類別<xref:System.Windows.EventManager.RegisterClassHandler%2A>。 這個方法只能呼叫內的靜態初始設定的類別加入類別處理。 這個範例會將另一個處理常式<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>，而在此情況下已註冊的類別是自訂的類別。 相反地，使用虛擬函式，已註冊的類別時，真正<xref:System.Windows.UIElement>基底類別。 在基底類別和子類別化每個註冊類別處理的情況下，子類別處理常式會先叫用。 應用程式中的行為會是這個處理常式會先顯示其訊息方塊，並接著會顯示虛擬方法的處理常式中的可見變更。  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.EventManager>  
 [將路由事件標記為已處理以及類別處理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [處理路由事件](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)  
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
