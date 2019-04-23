---
title: HOW TO：新增路由事件的類別處理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], class handlers
- task_core_add_class_handling_routed_properties [WPF]
- class handlers [WPF], routed events
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
ms.openlocfilehash: 7b897954cbdab461dc0305c6290e67c1af5282c3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224263"
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a>HOW TO：新增路由事件的類別處理
藉由類別處理常式或路由中任何指定節點上的執行個體處理常式可以處理路由的事件。 類別處理常式會先叫用，而且可以由類別實作來隱藏執行個體處理的事件，或引進其他事件的特定行為的基底類別所擁有的事件。 此範例說明兩種密切相關的技術，實作類別處理常式。  
  
## <a name="example"></a>範例  
 這個範例會使用自訂類別，根據<xref:System.Windows.Controls.Canvas>面板。 應用程式的基本前提是自訂類別導入了在其子項目，包括攔截任何滑鼠左的按鈕點選，以及標示為已處理，將會叫用子系項目類別或它的任何執行個體處理常式之前的行為。  
  
 <xref:System.Windows.UIElement>類別會公開虛擬方法，以允許的類別處理<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>事件，只覆寫事件。 這是最簡單的方式來實作類別處理，如果您的類別階層中某處的虛擬方法可用。 下列程式碼示範<xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A>"MyEditContainer"衍生自的類別中實作<xref:System.Windows.Controls.Canvas>。 實作會將事件標記為已處理的引數中，然後將 指定來源項目基本的可見變更一些程式碼。  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 如果沒有虛擬基底類別或該特定的方法，可以直接使用的公用程式方法加入類別處理<xref:System.Windows.EventManager>類別， <xref:System.Windows.EventManager.RegisterClassHandler%2A>。 中的加入類別處理的類別的靜態初始設定時，應該只呼叫這個方法。 這個範例會將另一個處理常式<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>，並在此情況下已註冊的類別是自訂類別。 相反地，當使用虛擬函式時，已註冊的類別其實不過是<xref:System.Windows.UIElement>基底類別。 在基底類別和子類別中每個註冊類別處理的情況下，子類別處理常式會最先叫用。 這個處理常式會先顯示它的訊息方塊，則會顯示虛擬方法的處理常式中的視覺化變更是在應用程式的行為。  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.EventManager>
- [將路由事件標記為已處理以及類別處理](marking-routed-events-as-handled-and-class-handling.md)
- [處理路由事件](how-to-handle-a-routed-event.md)
- [路由事件概觀](routed-events-overview.md)
