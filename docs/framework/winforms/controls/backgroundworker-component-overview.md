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
ms.openlocfilehash: 1f7da963db34434ee2631e9e2c0367abbd628656
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43539232"
---
# <a name="backgroundworker-component-overview"></a>BackgroundWorker 元件概觀
有許多經常執行的作業都需要長時間執行。 例如：  
  
-   映像下載  
  
-   Web 服務叫用  
  
-   檔案下載及上傳 (包括對等應用程式)  
  
-   複雜的本機運算  
  
-   資料庫交易  
  
-   本機磁碟存取 (假設因為存取記憶體導致速度變慢)  
  
 當這類作業執行時，可能會導致您的使用者介面無回應。 當您需要 UI 即時回應，但 UI 卻受到這些作業拖累，導致回應時間拉長時，<xref:System.ComponentModel.BackgroundWorker> 元件可以提供合宜的解決方法。  
  
 <xref:System.ComponentModel.BackgroundWorker> 元件可以非同步 (在背景中) 的方式，透過不同於應用程式之主要 UI 執行緒的執行緒來執行這些耗時的作業。 若要使用 <xref:System.ComponentModel.BackgroundWorker>，只須告知此函式要在背景中執行哪一個工作者方法，然後再呼叫 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 方法就可以了。 您呼叫的執行緒會如常執行，而工作者方法也會以非同步的方式同時執行。 當方法結束時，<xref:System.ComponentModel.BackgroundWorker> 會引發 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件來提示您呼叫的執行緒，並視情況在事件中包含作業的結果。  
  
 <xref:System.ComponentModel.BackgroundWorker>元件是可從**工具箱**，在**元件** 索引標籤。若要將 <xref:System.ComponentModel.BackgroundWorker> 加入表單，可將 <xref:System.ComponentModel.BackgroundWorker> 元件拖曳至表單中。 它會出現在元件匣中，和其屬性會出現在**屬性**視窗。  
  
 若要啟動非同步作業，請使用 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 方法。 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 可接受選用的 `object` 參數將引數傳遞給您的工作者方法。 <xref:System.ComponentModel.BackgroundWorker> 類別會引發 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件，而您的工作者執行緒會經由 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式連結至此事件。  
  
 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式可接受具有 <xref:System.ComponentModel.DoWorkEventArgs> 屬性的 <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> 參數。 此屬性會從 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 接收參數，並可傳遞給 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式中所呼叫的工作者方法。 下列範例示範如何指派工作者方法 `ComputeFibonacci` 所產生的結果。 它是較大的範例，您可以在中找到的一部分[如何： 實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)。  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 如需有關如何使用事件處理常式的詳細資訊，請參閱 <<c0> [ 事件](../../../../docs/standard/events/index.md)。  
  
> [!CAUTION]
>  無論使用何種多執行緒作業，您都可能會面臨嚴重而複雜的錯誤。 請在實作使用多執行緒的任何解決方案之前參閱 [Managed 執行緒最佳做法](../../../../docs/standard/threading/managed-threading-best-practices.md)。  
  
 如需有關使用<xref:System.ComponentModel.BackgroundWorker>類別，請參閱[如何： 在背景執行作業](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)。  
  
## <a name="see-also"></a>另請參閱  
 [不在組建中：Visual Basic 中的多執行緒處理](https://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)  
 [操作說明：實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
