---
ms.openlocfilehash: dab6b435a885d862d08f94dd31de79625f19bcc0
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67870512"
---
## <a name="installation-instructions---visual-studio-installer"></a><span data-ttu-id="1fc44-101">安裝指示 - Visual Studio 安裝程式</span><span class="sxs-lookup"><span data-stu-id="1fc44-101">Installation instructions - Visual Studio Installer</span></span>

<span data-ttu-id="1fc44-102">有兩種不同方式可以在 [Visual Studio 安裝程式]  中尋找 [.NET Compiler Platform SDK]  ：</span><span class="sxs-lookup"><span data-stu-id="1fc44-102">There are two different ways to find the **.NET Compiler Platform SDK** in the **Visual Studio Installer**:</span></span>

### <a name="install-using-the-visual-studio-installer---workloads-view"></a><span data-ttu-id="1fc44-103">使用 Visual Studio 安裝程式安裝 - 工作負載檢視</span><span class="sxs-lookup"><span data-stu-id="1fc44-103">Install using the Visual Studio Installer - Workloads view</span></span>

<span data-ttu-id="1fc44-104">不會自動選取 .NET Compiler Platform SDK 作為 Visual Studio 延伸模組開發工作負載的一部分。</span><span class="sxs-lookup"><span data-stu-id="1fc44-104">The .NET Compiler Platform SDK is not automatically selected as part of the Visual Studio extension development workload.</span></span> <span data-ttu-id="1fc44-105">您必須選取它作為為選用元件。</span><span class="sxs-lookup"><span data-stu-id="1fc44-105">You must select it as an optional component.</span></span>

1. <span data-ttu-id="1fc44-106">執行 [Visual Studio 安裝程式] </span><span class="sxs-lookup"><span data-stu-id="1fc44-106">Run **Visual Studio Installer**</span></span> 
1. <span data-ttu-id="1fc44-107">選取 [修改] </span><span class="sxs-lookup"><span data-stu-id="1fc44-107">Select **Modify**</span></span> 
1. <span data-ttu-id="1fc44-108">核取 [Visual Studio 延伸模組開發]  。</span><span class="sxs-lookup"><span data-stu-id="1fc44-108">Check the **Visual Studio extension development** workload.</span></span>
1. <span data-ttu-id="1fc44-109">在摘要樹狀結構中開啟 [Visual Studio 延伸模組開發]  節點。</span><span class="sxs-lookup"><span data-stu-id="1fc44-109">Open the **Visual Studio extension development** node in the summary tree.</span></span>
1. <span data-ttu-id="1fc44-110">核取 [.NET Compiler Platform SDK]  的方塊。</span><span class="sxs-lookup"><span data-stu-id="1fc44-110">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="1fc44-111">您將在選用元件下的最後處找到它。</span><span class="sxs-lookup"><span data-stu-id="1fc44-111">You'll find it last under the optional components.</span></span>

<span data-ttu-id="1fc44-112">(選擇性) 您可能也需要 [DGML 編輯器]  以在視覺化檢視中顯示圖形：</span><span class="sxs-lookup"><span data-stu-id="1fc44-112">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="1fc44-113">在摘要樹狀結構中開啟 [個別元件]  節點。</span><span class="sxs-lookup"><span data-stu-id="1fc44-113">Open the **Individual components** node in the summary tree.</span></span>
1. <span data-ttu-id="1fc44-114">核取 [DGML 編輯器]  的方塊</span><span class="sxs-lookup"><span data-stu-id="1fc44-114">Check the box for **DGML editor**</span></span>

### <a name="install-using-the-visual-studio-installer---individual-components-tab"></a><span data-ttu-id="1fc44-115">使用 Visual Studio 安裝程式安裝 - [個別元件] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="1fc44-115">Install using the Visual Studio Installer - Individual components tab</span></span>

1. <span data-ttu-id="1fc44-116">執行 [Visual Studio 安裝程式] </span><span class="sxs-lookup"><span data-stu-id="1fc44-116">Run **Visual Studio Installer**</span></span> 
1. <span data-ttu-id="1fc44-117">選取 [修改] </span><span class="sxs-lookup"><span data-stu-id="1fc44-117">Select **Modify**</span></span> 
1. <span data-ttu-id="1fc44-118">選取 [個別元件]  索引標籤</span><span class="sxs-lookup"><span data-stu-id="1fc44-118">Select the **Individual components** tab</span></span> 
1. <span data-ttu-id="1fc44-119">核取 [.NET Compiler Platform SDK]  的方塊。</span><span class="sxs-lookup"><span data-stu-id="1fc44-119">Check the box for **.NET Compiler Platform SDK**.</span></span> <span data-ttu-id="1fc44-120">您將在 [編譯器、建置工具與執行階段]  區段下的頂端找到它。</span><span class="sxs-lookup"><span data-stu-id="1fc44-120">You'll find it at the top under the **Compilers, build tools, and runtimes** section.</span></span>

<span data-ttu-id="1fc44-121">(選擇性) 您可能也需要 [DGML 編輯器]  以在視覺化檢視中顯示圖形：</span><span class="sxs-lookup"><span data-stu-id="1fc44-121">Optionally, you'll also want the **DGML editor** to display graphs in the visualizer:</span></span>

1. <span data-ttu-id="1fc44-122">核取 [DGML 編輯器]  的方塊。</span><span class="sxs-lookup"><span data-stu-id="1fc44-122">Check the box for **DGML editor**.</span></span> <span data-ttu-id="1fc44-123">您將在 [程式碼工具]  區段下找到它。</span><span class="sxs-lookup"><span data-stu-id="1fc44-123">You'll find it under the **Code tools** section.</span></span>
