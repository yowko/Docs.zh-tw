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
# <a name="multithreading-in-windows-forms-controls"></a><span data-ttu-id="b0bb5-102">在 Windows Form 控制項中的多執行緒</span><span class="sxs-lookup"><span data-stu-id="b0bb5-102">Multithreading in Windows Forms Controls</span></span>
<span data-ttu-id="b0bb5-103">在許多應用程式中, 您可以藉由在另一個執行緒上執行耗時的作業, 讓您的使用者介面 (UI) 更具回應能力。</span><span class="sxs-lookup"><span data-stu-id="b0bb5-103">In many applications, you can make your user interface (UI) more responsive by performing time-consuming operations on another thread.</span></span> <span data-ttu-id="b0bb5-104">有一些工具可供多執行緒處理您的 Windows Forms 控制項, 包括<xref:System.Threading>命名空間<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> 、方法和`BackgroundWorker`元件。</span><span class="sxs-lookup"><span data-stu-id="b0bb5-104">A number of tools are available for multithreading your Windows Forms controls, including the <xref:System.Threading> namespace, the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method, and the `BackgroundWorker` component.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b0bb5-105">元件會取代並將功能新增<xref:System.Threading>至命名空間和<xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>方法; 不過, 如果您選擇, 則會保留以供回溯相容性及未來使用。 `BackgroundWorker`</span><span class="sxs-lookup"><span data-stu-id="b0bb5-105">The `BackgroundWorker` component replaces and adds functionality to the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> method; however, these are retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="b0bb5-106">如需詳細資訊, 請參閱[BackgroundWorker 元件總覽](backgroundworker-component-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b0bb5-106">For more information, see [BackgroundWorker Component Overview](backgroundworker-component-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b0bb5-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="b0bb5-107">In This Section</span></span>  
 [<span data-ttu-id="b0bb5-108">如何：對 Windows Forms 控制項進行安全線程呼叫</span><span class="sxs-lookup"><span data-stu-id="b0bb5-108">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 <span data-ttu-id="b0bb5-109">顯示如何對 Windows Forms 控制項進行安全線程呼叫。</span><span class="sxs-lookup"><span data-stu-id="b0bb5-109">Shows how to make thread-safe calls to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="b0bb5-110">如何：使用背景執行緒來搜尋檔案</span><span class="sxs-lookup"><span data-stu-id="b0bb5-110">How to: Use a Background Thread to Search for Files</span></span>](how-to-use-a-background-thread-to-search-for-files.md)  
 <span data-ttu-id="b0bb5-111">示範如何使用<xref:System.Threading>命名空間<xref:System.Windows.Forms.Control.BeginInvoke%2A>和方法, 以非同步方式搜尋檔案。</span><span class="sxs-lookup"><span data-stu-id="b0bb5-111">Shows how to use the <xref:System.Threading> namespace and the <xref:System.Windows.Forms.Control.BeginInvoke%2A> method to search for files asynchronously.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b0bb5-112">參考資料</span><span class="sxs-lookup"><span data-stu-id="b0bb5-112">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="b0bb5-113">記載封裝背景工作執行緒以進行非同步作業的元件。</span><span class="sxs-lookup"><span data-stu-id="b0bb5-113">Documents a component that encapsulates a worker thread for asynchronous operations.</span></span>  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <span data-ttu-id="b0bb5-114">檔如何以非同步方式載入音效。</span><span class="sxs-lookup"><span data-stu-id="b0bb5-114">Documents how to load a sound asynchronously.</span></span>  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 <span data-ttu-id="b0bb5-115">檔如何以非同步方式載入影像。</span><span class="sxs-lookup"><span data-stu-id="b0bb5-115">Documents how to load an image asynchronously.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b0bb5-116">相關章節</span><span class="sxs-lookup"><span data-stu-id="b0bb5-116">Related Sections</span></span>  
 [<span data-ttu-id="b0bb5-117">如何：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="b0bb5-117">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="b0bb5-118">示範如何使用<xref:System.ComponentModel.BackgroundWorker>元件執行耗時的作業。</span><span class="sxs-lookup"><span data-stu-id="b0bb5-118">Shows how to perform a time-consuming operation with the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
 [<span data-ttu-id="b0bb5-119">BackgroundWorker 元件概觀</span><span class="sxs-lookup"><span data-stu-id="b0bb5-119">BackgroundWorker Component Overview</span></span>](backgroundworker-component-overview.md)  
 <span data-ttu-id="b0bb5-120">提供描述如何使用<xref:System.ComponentModel.BackgroundWorker>元件進行非同步作業的主題。</span><span class="sxs-lookup"><span data-stu-id="b0bb5-120">Provides topics that describe how to use the <xref:System.ComponentModel.BackgroundWorker> component for asynchronous operations.</span></span>
