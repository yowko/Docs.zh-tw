---
title: "在 Windows Form 控制項中的多執行緒"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2b9c0a7b19df62867a4148b60e24b7d3ba9bcce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="multithreading-in-windows-forms-controls"></a>在 Windows Form 控制項中的多執行緒
在許多應用程式，您可以讓您的使用者介面 (UI) 更能有效回應執行耗時的作業，另一個執行緒上。 數個工具可供多執行緒 Windows Form 控制項，包括<xref:System.Threading>命名空間，<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>方法，而`BackgroundWorker`元件。  
  
> [!NOTE]
>  `BackgroundWorker`元件取代，並將功能加入<xref:System.Threading>命名空間和<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>方法; 不過，這些會保留回溯相容性及未來使用，如果您選擇。 如需詳細資訊，請參閱[BackgroundWorker 元件概觀](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [操作說明：進行對 Windows Forms 控制項的安全執行緒呼叫](../../../../docs/framework/winforms/controls/how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 示範如何進行安全執行緒呼叫 Windows Form 控制項。  
  
 [操作說明：使用背景執行緒搜尋檔案](../../../../docs/framework/winforms/controls/how-to-use-a-background-thread-to-search-for-files.md)  
 示範如何使用<xref:System.Threading>命名空間和<xref:System.Windows.Forms.Control.BeginInvoke%2A>方法來以非同步方式搜尋的檔案。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ComponentModel.BackgroundWorker>  
 文件元件，可封裝工作者執行緒的非同步作業。  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 如何以非同步方式載入音效文件。  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 如何以非同步方式載入影像的文件。  
  
## <a name="related-sections"></a>相關章節  
 [操作說明：在背景執行作業](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 示範如何執行耗時的作業與<xref:System.ComponentModel.BackgroundWorker>元件。  
  
 [BackgroundWorker 元件概觀](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 提供主題描述如何使用<xref:System.ComponentModel.BackgroundWorker>元件的非同步作業。
