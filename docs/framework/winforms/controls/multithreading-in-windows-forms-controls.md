---
title: 控制項中的多執行緒
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: 79832e12a10f02c909d2a28270594bcb4ea68656
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742138"
---
# <a name="multithreading-in-windows-forms-controls"></a>在 Windows Form 控制項中的多執行緒
在許多應用程式中，您可以藉由在另一個執行緒上執行耗時的作業，讓您的使用者介面（UI）更具回應能力。 有一些工具可供多執行緒處理您的 Windows Forms 控制項，包括 <xref:System.Threading> 命名空間、<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> 方法和 `BackgroundWorker` 元件。  
  
> [!NOTE]
> `BackgroundWorker` 元件會取代 <xref:System.Threading> 命名空間和 <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> 方法，並將其加入功能;不過，如果您選擇，這些會保留給回溯相容性及未來使用。 如需詳細資訊，請參閱[BackgroundWorker 元件總覽](backgroundworker-component-overview.md)。  
  
## <a name="in-this-section"></a>本章節內容  
 [操作說明：進行對 Windows Forms 控制項的安全執行緒呼叫](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 顯示如何對 Windows Forms 控制項進行安全線程呼叫。  
  
 [操作說明：使用背景執行緒搜尋檔案](how-to-use-a-background-thread-to-search-for-files.md)  
 示範如何使用 <xref:System.Threading> 命名空間和 <xref:System.Windows.Forms.Control.BeginInvoke%2A> 方法，以非同步方式搜尋檔案。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ComponentModel.BackgroundWorker>  
 記載封裝背景工作執行緒以進行非同步作業的元件。  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 檔如何以非同步方式載入音效。  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 檔如何以非同步方式載入影像。  
  
## <a name="related-sections"></a>相關章節  
 [操作說明：在背景執行作業](how-to-run-an-operation-in-the-background.md)  
 示範如何使用 <xref:System.ComponentModel.BackgroundWorker> 元件執行耗時的作業。  
  
 [BackgroundWorker 元件概觀](backgroundworker-component-overview.md)  
 提供描述如何使用 <xref:System.ComponentModel.BackgroundWorker> 元件進行非同步作業的主題。
