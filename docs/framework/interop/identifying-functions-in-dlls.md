---
title: "識別 DLL 中的函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- platform invoke, identifying functions
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- identifying DLL functions
- DLL functions
ms.assetid: 3e3f6780-6d90-4413-bad7-ba641220364d
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d182ec26d6d15ad3e4c93e9bfa8287ba028e424
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="identifying-functions-in-dlls"></a><span data-ttu-id="001be-102">識別 DLL 中的函式</span><span class="sxs-lookup"><span data-stu-id="001be-102">Identifying Functions in DLLs</span></span>
<span data-ttu-id="001be-103">DLL 函式的身分識別是由下列項目所組成：</span><span class="sxs-lookup"><span data-stu-id="001be-103">The identity of a DLL function consists of the following elements:</span></span>  
  
-   <span data-ttu-id="001be-104">函式名稱或序數</span><span class="sxs-lookup"><span data-stu-id="001be-104">Function name or ordinal</span></span>  
  
-   <span data-ttu-id="001be-105">可在其中找到實作之 DLL 檔案的名稱</span><span class="sxs-lookup"><span data-stu-id="001be-105">Name of the DLL file in which the implementation can be found</span></span>  
  
 <span data-ttu-id="001be-106">例如，在 User32.dll 中指定 **MessageBox** 函式可識別此函式 (**MessageBox**) 及其位置 (User32.dll、User32 或 user32)。</span><span class="sxs-lookup"><span data-stu-id="001be-106">For example, specifying the **MessageBox** function in the User32.dll identifies the function (**MessageBox**) and its location (User32.dll, User32, or user32).</span></span> <span data-ttu-id="001be-107">Microsoft Windows 應用程式開發介面 (Win32 API) 可針對處理字元和字串的每一個函式，各包含兩個版本：一個是單位元組字元的 ANSI 版本，另一個是雙位元組字元的 Unicode 版本。</span><span class="sxs-lookup"><span data-stu-id="001be-107">The Microsoft Windows application programming interface (Win32 API) can contain two versions of each function that handles characters and strings: a 1-byte character ANSI version and a 2-byte character Unicode version.</span></span> <span data-ttu-id="001be-108">未指定時，由 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> 欄位所代表的字元集預設為 ANSI。</span><span class="sxs-lookup"><span data-stu-id="001be-108">When unspecified, the character set, represented by the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field, defaults to ANSI.</span></span> <span data-ttu-id="001be-109">某些函式可以有兩個以上的版本。</span><span class="sxs-lookup"><span data-stu-id="001be-109">Some functions can have more than two versions.</span></span>  
  
 <span data-ttu-id="001be-110">**MessageBoxA** 是 **MessageBox** 函式的 ANSI 進入點；**MessageBoxW** 則是 Unicode 版本。</span><span class="sxs-lookup"><span data-stu-id="001be-110">**MessageBoxA** is the ANSI entry point for the **MessageBox** function; **MessageBoxW** is the Unicode version.</span></span> <span data-ttu-id="001be-111">您可以藉由執行各種不同的命令列工具，列出特定 DLL 的函式名稱，例如 user32.dll 。</span><span class="sxs-lookup"><span data-stu-id="001be-111">You can list function names for a specific DLL, such as user32.dll, by running a variety of command-line tools.</span></span> <span data-ttu-id="001be-112">例如，您可以使用 `dumpbin /exports user32.dll` 或 `link /dump /exports user32.dll` 來取得函式名稱。</span><span class="sxs-lookup"><span data-stu-id="001be-112">For example, you can use `dumpbin /exports user32.dll` or `link /dump /exports user32.dll` to obtain function names.</span></span>  
  
 <span data-ttu-id="001be-113">只要將新名稱對應至 DLL 中原始的進入點，您就可以在程式碼內將 Unmanaged 函式重新命名為您喜歡的任何名稱。</span><span class="sxs-lookup"><span data-stu-id="001be-113">You can rename an unmanaged function to whatever you like within your code as long as you map the new name to the original entry point in the DLL.</span></span> <span data-ttu-id="001be-114">如需在 Managed 原始程式碼中重新命名 Unmanaged DLL 函式中的指示，請參閱[指定進入點](../../../docs/framework/interop/specifying-an-entry-point.md)。</span><span class="sxs-lookup"><span data-stu-id="001be-114">For instructions on renaming an unmanaged DLL function in managed source code, see the [Specifying an Entry Point](../../../docs/framework/interop/specifying-an-entry-point.md).</span></span>  
  
 <span data-ttu-id="001be-115">平台叫用可讓您藉由呼叫 Win32 API 和其他 Dll 中的函式，控制作業系統的重要部分。</span><span class="sxs-lookup"><span data-stu-id="001be-115">Platform invoke enables you to control a significant portion of the operating system by calling functions in the Win32 API and other DLLs.</span></span> <span data-ttu-id="001be-116">除了 Win32 API 以外，還有許多其他 API 和 DLL 可透過平台叫用供您使用。</span><span class="sxs-lookup"><span data-stu-id="001be-116">In addition to the Win32 API, there are numerous other APIs and DLLs available to you through platform invoke.</span></span>  
  
 <span data-ttu-id="001be-117">下表描述 Win32 API 中常用的數個 Dll。</span><span class="sxs-lookup"><span data-stu-id="001be-117">The following table describes several commonly used DLLs in the Win32 API.</span></span>  
  
|<span data-ttu-id="001be-118">DLL</span><span class="sxs-lookup"><span data-stu-id="001be-118">DLL</span></span>|<span data-ttu-id="001be-119">內容的描述</span><span class="sxs-lookup"><span data-stu-id="001be-119">Description of Contents</span></span>|  
|---------|-----------------------------|  
|<span data-ttu-id="001be-120">GDI32.dll</span><span class="sxs-lookup"><span data-stu-id="001be-120">GDI32.dll</span></span>|<span data-ttu-id="001be-121">用於裝置輸出的圖形裝置介面 (GDI) 函式，例如用於繪圖和字型管理的函式。</span><span class="sxs-lookup"><span data-stu-id="001be-121">Graphics Device Interface (GDI) functions for device output, such as those for drawing and font management.</span></span>|  
|<span data-ttu-id="001be-122">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="001be-122">Kernel32.dll</span></span>|<span data-ttu-id="001be-123">用於記憶體管理和資源處理的低階作業系統函式。</span><span class="sxs-lookup"><span data-stu-id="001be-123">Low-level operating system functions for memory management and resource handling.</span></span>|  
|<span data-ttu-id="001be-124">User32.dll</span><span class="sxs-lookup"><span data-stu-id="001be-124">User32.dll</span></span>|<span data-ttu-id="001be-125">用於訊息處理、計時器、功能表和通訊的 Windows 管理函式。</span><span class="sxs-lookup"><span data-stu-id="001be-125">Windows management functions for message handling, timers, menus, and communications.</span></span>|  
  
 <span data-ttu-id="001be-126">如需 Win32 API 的完整文件，請參閱 Platform SDK。</span><span class="sxs-lookup"><span data-stu-id="001be-126">For complete documentation on the Win32 API, see the Platform SDK.</span></span> <span data-ttu-id="001be-127">如需示範如何建構要與平台叫用搭配使用之 .NET 型宣告的範例，請參閱[使用平台叫用封送處理資料](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)。</span><span class="sxs-lookup"><span data-stu-id="001be-127">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="001be-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="001be-128">See Also</span></span>  
 [<span data-ttu-id="001be-129">使用 Unmanaged DLL 函式</span><span class="sxs-lookup"><span data-stu-id="001be-129">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="001be-130">指定進入點</span><span class="sxs-lookup"><span data-stu-id="001be-130">Specifying an Entry Point</span></span>](../../../docs/framework/interop/specifying-an-entry-point.md)  
 [<span data-ttu-id="001be-131">建立類別以包裝 DLL 函式</span><span class="sxs-lookup"><span data-stu-id="001be-131">Creating a Class to Hold DLL Functions</span></span>](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)  
 [<span data-ttu-id="001be-132">在 Managed 程式碼中建立原型</span><span class="sxs-lookup"><span data-stu-id="001be-132">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="001be-133">呼叫 DLL 函式</span><span class="sxs-lookup"><span data-stu-id="001be-133">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
