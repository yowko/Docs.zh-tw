---
title: 回呼函式
description: 瞭解回呼函式，這是具有受控應用程式的程式碼，可協助非受控 DLL 函式完成工作。
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
ms.openlocfilehash: e28756b5ed935aff83363b38d6f33982e87718b2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621713"
---
# <a name="callback-functions"></a><span data-ttu-id="55996-103">回呼函式</span><span class="sxs-lookup"><span data-stu-id="55996-103">Callback Functions</span></span>
<span data-ttu-id="55996-104">回呼函式是 Managed 應用程式內的程式碼，協助未管理 DLL 函式完成工作。</span><span class="sxs-lookup"><span data-stu-id="55996-104">A callback function is code within a managed application that helps an unmanaged DLL function complete a task.</span></span> <span data-ttu-id="55996-105">回呼函式的呼叫會透過 DLL 函式從 Managed 應用程式間接傳遞，然後傳遞回 Managed 實作。</span><span class="sxs-lookup"><span data-stu-id="55996-105">Calls to a callback function pass indirectly from a managed application, through a DLL function, and back to the managed implementation.</span></span> <span data-ttu-id="55996-106">許多使用平台叫用所呼叫的 DLL 函式有一部分需要 Managed 程式碼中有回呼函式，才能正確執行。</span><span class="sxs-lookup"><span data-stu-id="55996-106">Some of the many DLL functions called with platform invoke require a callback function in managed code to run properly.</span></span>  
  
 <span data-ttu-id="55996-107">若要從 Managed 程式碼呼叫大部分的 DLL 函式，請建立函式的 Managed 定義，然後進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="55996-107">To call most DLL functions from managed code, you create a managed definition of the function and then call it.</span></span> <span data-ttu-id="55996-108">此程序相當直接明瞭。</span><span class="sxs-lookup"><span data-stu-id="55996-108">The process is straightforward.</span></span>  
  
 <span data-ttu-id="55996-109">使用需要回呼函式的 DLL 函式時有一些額外步驟。</span><span class="sxs-lookup"><span data-stu-id="55996-109">Using a DLL function that requires a callback function has some additional steps.</span></span> <span data-ttu-id="55996-110">首先，您必須查看函式的文件，以決定函式是否需要回呼。</span><span class="sxs-lookup"><span data-stu-id="55996-110">First, you must determine whether the function requires a callback by looking at the documentation for the function.</span></span> <span data-ttu-id="55996-111">接下來，您必須在 Managed 應用程式中建立回呼函式。</span><span class="sxs-lookup"><span data-stu-id="55996-111">Next, you have to create the callback function in your managed application.</span></span> <span data-ttu-id="55996-112">最後，您呼叫 DLL 函式，以將指標傳遞給回呼函式以作為引數。</span><span class="sxs-lookup"><span data-stu-id="55996-112">Finally, you call the DLL function, passing a pointer to the callback function as an argument.</span></span>

 <span data-ttu-id="55996-113">下圖摘要說明的回呼函式和實作步驟：</span><span class="sxs-lookup"><span data-stu-id="55996-113">The following illustration summarizes the callback function and implementation steps:</span></span>  
  
 ![圖表顯示平台叫用回呼程序。](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 <span data-ttu-id="55996-115">回呼函式最適合用於重複執行工作的情況。</span><span class="sxs-lookup"><span data-stu-id="55996-115">Callback functions are ideal for use in situations in which a task is performed repeatedly.</span></span> <span data-ttu-id="55996-116">在 Windows API 中，另一個常見用法是列舉函式，例如 **EnumFontFamilies**、**EnumPrinters** 和 **EnumWindows**。</span><span class="sxs-lookup"><span data-stu-id="55996-116">Another common usage is with enumeration functions, such as **EnumFontFamilies**, **EnumPrinters**, and **EnumWindows** in the Windows API.</span></span> <span data-ttu-id="55996-117">**EnumWindows** 函式會逐一列舉電腦上的所有現有視窗，以呼叫回呼函式來對每個視窗執行工作。</span><span class="sxs-lookup"><span data-stu-id="55996-117">The **EnumWindows** function enumerates through all existing windows on your computer, calling the callback function to perform a task on each window.</span></span> <span data-ttu-id="55996-118">如需指示和範例，請參閱[如何：實作回呼函式](how-to-implement-callback-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="55996-118">For instructions and an example, see [How to: Implement Callback Functions](how-to-implement-callback-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55996-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55996-119">See also</span></span>

- [<span data-ttu-id="55996-120">作法：實作回呼函式</span><span class="sxs-lookup"><span data-stu-id="55996-120">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)
- [<span data-ttu-id="55996-121">呼叫 DLL 函式</span><span class="sxs-lookup"><span data-stu-id="55996-121">Calling a DLL Function</span></span>](calling-a-dll-function.md)
