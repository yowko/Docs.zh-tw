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
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="c55d1-102">在 Windows Form 控制項中的多執行緒</span><span class="sxs-lookup"><span data-stu-id="c55d1-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="c55d1-103">在許多應用程式中，您可以藉由在另一個執行緒上執行耗時的作業，讓您的使用者介面（UI）更具回應能力。</span><span class="sxs-lookup"><span data-stu-id="c55d1-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="c55d1-104">有一些工具可供多執行緒處理您的 Windows Forms 控制項，包括 <xref:System.Threading> 命名空間、<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> 方法和 `BackgroundWorker` 元件。</span><span class="sxs-lookup"><span data-stu-id="c55d1-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c55d1-105">`BackgroundWorker` 元件會取代 <xref:System.Threading> 命名空間和 <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> 方法，並將其加入功能;不過，如果您選擇，這些會保留給回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="c55d1-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="c55d1-106">如需詳細資訊，請參閱[BackgroundWorker 元件總覽](backgroundworker-component-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c55d1-106">For more information, see [BackgroundWorker Component Overview](backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c55d1-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="c55d1-107">In This Section</span></span>  
 [<span data-ttu-id="c55d1-108">操作說明：進行對 Windows Forms 控制項的安全執行緒呼叫</span><span class="sxs-lookup"><span data-stu-id="c55d1-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="c55d1-109">顯示如何對 Windows Forms 控制項進行安全線程呼叫。</span><span class="sxs-lookup"><span data-stu-id="c55d1-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="c55d1-110">操作說明：使用背景執行緒搜尋檔案</span><span class="sxs-lookup"><span data-stu-id="c55d1-110">How to: Use a Background Thread to Search for Files</span></span>](how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="c55d1-111">示範如何使用 <xref:System.Threading> 命名空間和 <xref:System.Windows.Forms.Control.BeginInvoke%2A> 方法，以非同步方式搜尋檔案。</span><span class="sxs-lookup"><span data-stu-id="c55d1-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c55d1-112">參考資料</span><span class="sxs-lookup"><span data-stu-id="c55d1-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="c55d1-113">記載封裝背景工作執行緒以進行非同步作業的元件。</span><span class="sxs-lookup"><span data-stu-id="c55d1-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="c55d1-114">檔如何以非同步方式載入音效。</span><span class="sxs-lookup"><span data-stu-id="c55d1-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="c55d1-115">檔如何以非同步方式載入影像。</span><span class="sxs-lookup"><span data-stu-id="c55d1-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c55d1-116">相關章節</span><span class="sxs-lookup"><span data-stu-id="c55d1-116">Related Sections</span></span>  
 [<span data-ttu-id="c55d1-117">操作說明：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="c55d1-117">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="c55d1-118">示範如何使用 <xref:System.ComponentModel.BackgroundWorker> 元件執行耗時的作業。</span><span class="sxs-lookup"><span data-stu-id="c55d1-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="c55d1-119">BackgroundWorker 元件概觀</span><span class="sxs-lookup"><span data-stu-id="c55d1-119">BackgroundWorker Component Overview</span></span>](backgroundworker-component-overview.md)  
 <span data-ttu-id="c55d1-120">提供描述如何使用 <xref:System.ComponentModel.BackgroundWorker> 元件進行非同步作業的主題。</span><span class="sxs-lookup"><span data-stu-id="c55d1-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>
