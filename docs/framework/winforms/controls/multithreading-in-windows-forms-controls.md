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
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="70a72-102">在 Windows Form 控制項中的多執行緒</span><span class="sxs-lookup"><span data-stu-id="70a72-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="70a72-103">在許多應用程式，您可以讓您的使用者介面 (UI) 回應速度更快執行耗時的作業，另一個執行緒上。</span><span class="sxs-lookup"><span data-stu-id="70a72-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="70a72-104">數種工具可供進行多執行緒處理您的 Windows Form 控制項，包括<xref:System.Threading>命名空間<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>方法，和`BackgroundWorker`元件。</span><span class="sxs-lookup"><span data-stu-id="70a72-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70a72-105">`BackgroundWorker`元件會取代並且將功能加入<xref:System.Threading>命名空間和<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>方法; 不過，這些會保留回溯相容性和未來使用，如果您選擇。</span><span class="sxs-lookup"><span data-stu-id="70a72-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="70a72-106">如需詳細資訊，請參閱 < [BackgroundWorker 元件概觀](backgroundworker-component-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="70a72-106">For more information, see [BackgroundWorker Component Overview](backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70a72-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="70a72-107">In This Section</span></span>  
 [<span data-ttu-id="70a72-108">如何：Windows Form 控制項的安全執行緒呼叫</span><span class="sxs-lookup"><span data-stu-id="70a72-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="70a72-109">示範如何進行對 Windows Form 控制項的安全執行緒呼叫。</span><span class="sxs-lookup"><span data-stu-id="70a72-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="70a72-110">如何：使用背景執行緒搜尋檔案</span><span class="sxs-lookup"><span data-stu-id="70a72-110">How to: Use a Background Thread to Search for Files</span></span>](how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="70a72-111">示範如何使用<xref:System.Threading>命名空間和<xref:System.Windows.Forms.Control.BeginInvoke%2A>方法以非同步方式搜尋檔案。</span><span class="sxs-lookup"><span data-stu-id="70a72-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="70a72-112">參考資料</span><span class="sxs-lookup"><span data-stu-id="70a72-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="70a72-113">文件元件，可封裝背景工作執行緒的非同步作業。</span><span class="sxs-lookup"><span data-stu-id="70a72-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="70a72-114">說明如何以非同步方式載入音效。</span><span class="sxs-lookup"><span data-stu-id="70a72-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="70a72-115">說明如何以非同步方式載入映像。</span><span class="sxs-lookup"><span data-stu-id="70a72-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="70a72-116">相關章節</span><span class="sxs-lookup"><span data-stu-id="70a72-116">Related Sections</span></span>  
 [<span data-ttu-id="70a72-117">如何：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="70a72-117">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="70a72-118">示範如何執行耗時的作業與<xref:System.ComponentModel.BackgroundWorker>元件。</span><span class="sxs-lookup"><span data-stu-id="70a72-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="70a72-119">BackgroundWorker 元件概觀</span><span class="sxs-lookup"><span data-stu-id="70a72-119">BackgroundWorker Component Overview</span></span>](backgroundworker-component-overview.md)  
 <span data-ttu-id="70a72-120">提供主題描述如何使用<xref:System.ComponentModel.BackgroundWorker>元件的非同步作業。</span><span class="sxs-lookup"><span data-stu-id="70a72-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>
