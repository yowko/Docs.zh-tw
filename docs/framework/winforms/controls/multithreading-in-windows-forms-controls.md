---
title: 在 Windows Form 控制項中的多執行緒
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cf6790172b7445ad154eead5d17f8efddd78ffee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952676"
---
# <a name="multithreading-in-windows-forms-controls"></a>在 Windows Form 控制項中的多執行緒
在許多應用程式中, 您可以藉由在另一個執行緒上執行耗時的作業, 讓您的使用者介面 (UI) 更具回應能力。 有一些工具可供多執行緒處理您的 Windows Forms 控制項, 包括<xref:System.Threading>命名空間<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> 、方法和`BackgroundWorker`元件。  
  
> [!NOTE]
> 元件會取代並將功能新增<xref:System.Threading>至命名空間和<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>方法; 不過, 如果您選擇, 則會保留以供回溯相容性及未來使用。 `BackgroundWorker` 如需詳細資訊, 請參閱[BackgroundWorker 元件總覽](backgroundworker-component-overview.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：對 Windows Forms 控制項進行安全線程呼叫](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 顯示如何對 Windows Forms 控制項進行安全線程呼叫。  
  
 [如何：使用背景執行緒來搜尋檔案](how-to-use-a-background-thread-to-search-for-files.md)  
 示範如何使用<xref:System.Threading>命名空間<xref:System.Windows.Forms.Control.BeginInvoke%2A>和方法, 以非同步方式搜尋檔案。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ComponentModel.BackgroundWorker>  
 記載封裝背景工作執行緒以進行非同步作業的元件。  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 檔如何以非同步方式載入音效。  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 檔如何以非同步方式載入影像。  
  
## <a name="related-sections"></a>相關章節  
 [如何：在背景執行作業](how-to-run-an-operation-in-the-background.md)  
 示範如何使用<xref:System.ComponentModel.BackgroundWorker>元件執行耗時的作業。  
  
 [BackgroundWorker 元件概觀](backgroundworker-component-overview.md)  
 提供描述如何使用<xref:System.ComponentModel.BackgroundWorker>元件進行非同步作業的主題。
