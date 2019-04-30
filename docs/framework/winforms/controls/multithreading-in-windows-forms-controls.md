---
title: 在 Windows Form 控制項中的多執行緒
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cc7f358a62c8057abb77e1f5a28544bb6c858d98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012720"
---
# <a name="multithreading-in-windows-forms-controls"></a>在 Windows Form 控制項中的多執行緒
在許多應用程式，您可以讓您的使用者介面 (UI) 回應速度更快執行耗時的作業，另一個執行緒上。 數種工具可供進行多執行緒處理您的 Windows Form 控制項，包括<xref:System.Threading>命名空間<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>方法，和`BackgroundWorker`元件。  
  
> [!NOTE]
>  `BackgroundWorker`元件會取代並且將功能加入<xref:System.Threading>命名空間和<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>方法; 不過，這些會保留回溯相容性和未來使用，如果您選擇。 如需詳細資訊，請參閱 < [BackgroundWorker 元件概觀](backgroundworker-component-overview.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：Windows Form 控制項的安全執行緒呼叫](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 示範如何進行對 Windows Form 控制項的安全執行緒呼叫。  
  
 [如何：使用背景執行緒搜尋檔案](how-to-use-a-background-thread-to-search-for-files.md)  
 示範如何使用<xref:System.Threading>命名空間和<xref:System.Windows.Forms.Control.BeginInvoke%2A>方法以非同步方式搜尋檔案。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ComponentModel.BackgroundWorker>  
 文件元件，可封裝背景工作執行緒的非同步作業。  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 說明如何以非同步方式載入音效。  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 說明如何以非同步方式載入映像。  
  
## <a name="related-sections"></a>相關章節  
 [如何：在背景執行作業](how-to-run-an-operation-in-the-background.md)  
 示範如何執行耗時的作業與<xref:System.ComponentModel.BackgroundWorker>元件。  
  
 [BackgroundWorker 元件概觀](backgroundworker-component-overview.md)  
 提供主題描述如何使用<xref:System.ComponentModel.BackgroundWorker>元件的非同步作業。
