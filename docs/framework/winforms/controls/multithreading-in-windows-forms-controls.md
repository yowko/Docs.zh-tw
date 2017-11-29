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
ms.openlocfilehash: c4651ca9707dcf0fac2edea0f004275cfcf18cf2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="b3609-102">在 Windows Form 控制項中的多執行緒</span><span class="sxs-lookup"><span data-stu-id="b3609-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="b3609-103">在許多應用程式，您可以讓您的使用者介面 (UI) 更能有效回應執行耗時的作業，另一個執行緒上。</span><span class="sxs-lookup"><span data-stu-id="b3609-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="b3609-104">數個工具可供多執行緒 Windows Form 控制項，包括<xref:System.Threading>命名空間，<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>方法，而`BackgroundWorker`元件。</span><span class="sxs-lookup"><span data-stu-id="b3609-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3609-105">`BackgroundWorker`元件取代，並將功能加入<xref:System.Threading>命名空間和<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>方法; 不過，這些會保留回溯相容性及未來使用，如果您選擇。</span><span class="sxs-lookup"><span data-stu-id="b3609-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="b3609-106">如需詳細資訊，請參閱[BackgroundWorker 元件概觀](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b3609-106">For more information, see [BackgroundWorker Component Overview](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3609-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="b3609-107">In This Section</span></span>  
 [<span data-ttu-id="b3609-108">操作說明：進行對 Windows Forms 控制項的安全執行緒呼叫</span><span class="sxs-lookup"><span data-stu-id="b3609-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="b3609-109">示範如何進行安全執行緒呼叫 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="b3609-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="b3609-110">操作說明：使用背景執行緒搜尋檔案</span><span class="sxs-lookup"><span data-stu-id="b3609-110">How to: Use a Background Thread to Search for Files</span></span>](../../../../docs/framework/winforms/controls/how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="b3609-111">示範如何使用<xref:System.Threading>命名空間和<xref:System.Windows.Forms.Control.BeginInvoke%2A>方法來以非同步方式搜尋的檔案。</span><span class="sxs-lookup"><span data-stu-id="b3609-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b3609-112">參考資料</span><span class="sxs-lookup"><span data-stu-id="b3609-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="b3609-113">文件元件，可封裝工作者執行緒的非同步作業。</span><span class="sxs-lookup"><span data-stu-id="b3609-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="b3609-114">如何以非同步方式載入音效文件。</span><span class="sxs-lookup"><span data-stu-id="b3609-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="b3609-115">如何以非同步方式載入影像的文件。</span><span class="sxs-lookup"><span data-stu-id="b3609-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b3609-116">相關章節</span><span class="sxs-lookup"><span data-stu-id="b3609-116">Related Sections</span></span>  
 [<span data-ttu-id="b3609-117">操作說明：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="b3609-117">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="b3609-118">示範如何執行耗時的作業與<xref:System.ComponentModel.BackgroundWorker>元件。</span><span class="sxs-lookup"><span data-stu-id="b3609-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="b3609-119">BackgroundWorker 元件概觀</span><span class="sxs-lookup"><span data-stu-id="b3609-119">BackgroundWorker Component Overview</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 <span data-ttu-id="b3609-120">提供主題描述如何使用<xref:System.ComponentModel.BackgroundWorker>元件的非同步作業。</span><span class="sxs-lookup"><span data-stu-id="b3609-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>
