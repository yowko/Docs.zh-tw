---
title: 回呼函式
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4494eda29ca6065a157869ec2f93b4875391824
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397386"
---
# <a name="callback-functions"></a><span data-ttu-id="5b45f-102">回呼函式</span><span class="sxs-lookup"><span data-stu-id="5b45f-102">Callback Functions</span></span>
<span data-ttu-id="5b45f-103">回呼函式是 Managed 應用程式內的程式碼，協助未管理 DLL 函式完成工作。</span><span class="sxs-lookup"><span data-stu-id="5b45f-103">A callback function is code within a managed application that helps an unmanaged DLL function complete a task.</span></span> <span data-ttu-id="5b45f-104">回呼函式的呼叫會透過 DLL 函式從 Managed 應用程式間接傳遞，然後傳遞回 Managed 實作。</span><span class="sxs-lookup"><span data-stu-id="5b45f-104">Calls to a callback function pass indirectly from a managed application, through a DLL function, and back to the managed implementation.</span></span> <span data-ttu-id="5b45f-105">許多使用平台叫用所呼叫的 DLL 函式有一部分需要 Managed 程式碼中有回呼函式，才能正確執行。</span><span class="sxs-lookup"><span data-stu-id="5b45f-105">Some of the many DLL functions called with platform invoke require a callback function in managed code to run properly.</span></span>  
  
 <span data-ttu-id="5b45f-106">若要從 Managed 程式碼呼叫大部分的 DLL 函式，請建立函式的 Managed 定義，然後進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="5b45f-106">To call most DLL functions from managed code, you create a managed definition of the function and then call it.</span></span> <span data-ttu-id="5b45f-107">此程序相當直接明瞭。</span><span class="sxs-lookup"><span data-stu-id="5b45f-107">The process is straightforward.</span></span>  
  
 <span data-ttu-id="5b45f-108">使用需要回呼函式的 DLL 函式時有一些額外步驟。</span><span class="sxs-lookup"><span data-stu-id="5b45f-108">Using a DLL function that requires a callback function has some additional steps.</span></span> <span data-ttu-id="5b45f-109">首先，您必須查看函式的文件，以決定函式是否需要回呼。</span><span class="sxs-lookup"><span data-stu-id="5b45f-109">First, you must determine whether the function requires a callback by looking at the documentation for the function.</span></span> <span data-ttu-id="5b45f-110">接下來，您必須在 Managed 應用程式中建立回呼函式。</span><span class="sxs-lookup"><span data-stu-id="5b45f-110">Next, you have to create the callback function in your managed application.</span></span> <span data-ttu-id="5b45f-111">最後，您呼叫 DLL 函式，以將指標傳遞給回呼函式以作為引數。</span><span class="sxs-lookup"><span data-stu-id="5b45f-111">Finally, you call the DLL function, passing a pointer to the callback function as an argument.</span></span> <span data-ttu-id="5b45f-112">下圖摘要說明這些步驟。</span><span class="sxs-lookup"><span data-stu-id="5b45f-112">The following illustration summarizes these steps.</span></span>  
  
 <span data-ttu-id="5b45f-113">![平台叫用回呼](../../../docs/framework/interop/media/pinvokecallback.gif "pinvokecallback")</span><span class="sxs-lookup"><span data-stu-id="5b45f-113">![Platform invoke callback](../../../docs/framework/interop/media/pinvokecallback.gif "pinvokecallback")</span></span>  
<span data-ttu-id="5b45f-114">回呼函式和實作</span><span class="sxs-lookup"><span data-stu-id="5b45f-114">Callback function and implementation</span></span>  
  
 <span data-ttu-id="5b45f-115">回呼函式最適合用於重複執行工作的情況。</span><span class="sxs-lookup"><span data-stu-id="5b45f-115">Callback functions are ideal for use in situations in which a task is performed repeatedly.</span></span> <span data-ttu-id="5b45f-116">在 Win32 API 中，另一個常見用法是列舉函式，例如 **EnumFontFamilies**、**EnumPrinters** 和 **EnumWindows**。</span><span class="sxs-lookup"><span data-stu-id="5b45f-116">Another common usage is with enumeration functions, such as **EnumFontFamilies**, **EnumPrinters**, and **EnumWindows** in the Win32 API.</span></span> <span data-ttu-id="5b45f-117">**EnumWindows** 函式會逐一列舉電腦上的所有現有視窗，以呼叫回呼函式來對每個視窗執行工作。</span><span class="sxs-lookup"><span data-stu-id="5b45f-117">The **EnumWindows** function enumerates through all existing windows on your computer, calling the callback function to perform a task on each window.</span></span> <span data-ttu-id="5b45f-118">如需指示和範例，請參閱[如何：實作回呼函式](../../../docs/framework/interop/how-to-implement-callback-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="5b45f-118">For instructions and an example, see [How to: Implement Callback Functions](../../../docs/framework/interop/how-to-implement-callback-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b45f-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="5b45f-119">See Also</span></span>  
 [<span data-ttu-id="5b45f-120">如何：實作回呼函式</span><span class="sxs-lookup"><span data-stu-id="5b45f-120">How to: Implement Callback Functions</span></span>](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 [<span data-ttu-id="5b45f-121">呼叫 DLL 函式</span><span class="sxs-lookup"><span data-stu-id="5b45f-121">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
