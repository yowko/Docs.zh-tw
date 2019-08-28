---
title: BackgroundWorker 元件概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- BackgroundWorker
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 64e9b3ab-7443-4a77-ab17-b8b8c0cb3f62
ms.openlocfilehash: e91d74b7ca5515dd63ba17a9111cadf5090dae2a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046112"
---
# <a name="backgroundworker-component-overview"></a>BackgroundWorker 元件概觀
有許多經常執行的作業都需要長時間執行。 例如：  
  
- 映像下載  
  
- Web 服務叫用  
  
- 檔案下載及上傳 (包括對等應用程式)  
  
- 複雜的本機運算  
  
- 資料庫交易  
  
- 本機磁碟存取 (假設因為存取記憶體導致速度變慢)  
  
 這類作業可能會導致您的使用者介面在執行時封鎖。 當您需要 UI 即時回應，但 UI 卻受到這些作業拖累，導致回應時間拉長時，<xref:System.ComponentModel.BackgroundWorker> 元件可以提供合宜的解決方法。  
  
 <xref:System.ComponentModel.BackgroundWorker> 元件可以非同步 (在背景中) 的方式，透過不同於應用程式之主要 UI 執行緒的執行緒來執行這些耗時的作業。 若要使用 <xref:System.ComponentModel.BackgroundWorker>，只須告知此函式要在背景中執行哪一個工作者方法，然後再呼叫 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 方法就可以了。 您呼叫的執行緒會如常執行，而工作者方法也會以非同步的方式同時執行。 當方法結束時，<xref:System.ComponentModel.BackgroundWorker> 會引發 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件來提示您呼叫的執行緒，並視情況在事件中包含作業的結果。  
  
 元件可從 [**工具箱**] 的 [元件] 索引標籤中取得。 <xref:System.ComponentModel.BackgroundWorker>若要將 <xref:System.ComponentModel.BackgroundWorker> 加入表單，可將 <xref:System.ComponentModel.BackgroundWorker> 元件拖曳至表單中。 它會出現在元件匣中, 而其屬性會出現在 [**屬性**] 視窗中。  
  
 若要啟動非同步作業，請使用 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 方法。 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 可接受選用的 `object` 參數將引數傳遞給您的工作者方法。 <xref:System.ComponentModel.BackgroundWorker> 類別會引發 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件，而您的工作者執行緒會經由 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式連結至此事件。  
  
 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式可接受具有 <xref:System.ComponentModel.DoWorkEventArgs> 屬性的 <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> 參數。 此屬性會從 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 接收參數，並可傳遞給 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式中所呼叫的工作者方法。 下列範例示範如何指派工作者方法 `ComputeFibonacci` 所產生的結果。 它是較大範例的一部分, 您可以在下列位置[找到:執行使用背景](how-to-implement-a-form-that-uses-a-background-operation.md)作業的表單。  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 如需使用事件處理常式的詳細資訊, 請參閱[事件](../../../standard/events/index.md)。  
  
> [!CAUTION]
> 無論使用何種多執行緒作業，您都可能會面臨嚴重而複雜的錯誤。 請在實作使用多執行緒的任何解決方案之前參閱 [Managed 執行緒最佳做法](../../../standard/threading/managed-threading-best-practices.md)。  
  
 如需使用<xref:System.ComponentModel.BackgroundWorker>類別的詳細資訊, 請[參閱如何:在背景執行作業](how-to-run-an-operation-in-the-background.md)。  
  
## <a name="see-also"></a>另請參閱

- [受控執行緒處理](../../../standard/threading/index.md)
- [事件架構非同步模式概觀](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [如何：實作使用背景作業的表單](how-to-implement-a-form-that-uses-a-background-operation.md)
