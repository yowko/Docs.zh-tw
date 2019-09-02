---
title: 平台叫用 (P/Invoke)
description: 了解如何在 .NET 中透過 P/Invoke 呼叫原生函式。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: cda738a173cbe61cf49f79ceef78c533a5a879d9
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106791"
---
# <a name="platform-invoke-pinvoke"></a><span data-ttu-id="ea277-103">平台叫用 (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="ea277-103">Platform Invoke (P/Invoke)</span></span>

<span data-ttu-id="ea277-104">P/Invoke 是一種技術，可讓您從受控碼存取結構、回呼和非受控程式庫中的函式。</span><span class="sxs-lookup"><span data-stu-id="ea277-104">P/Invoke is a technology that allows you to access structs, callbacks, and functions in unmanaged libraries from your managed code.</span></span> <span data-ttu-id="ea277-105">大部分的 P/Invoke API 都包含在兩個命名空間中︰`System` 和 `System.Runtime.InteropServices`。</span><span class="sxs-lookup"><span data-stu-id="ea277-105">Most of the P/Invoke API is contained in two namespaces: `System` and `System.Runtime.InteropServices`.</span></span> <span data-ttu-id="ea277-106">使用這兩個命名空間會提供您可描述您想要如何與原生元件互動的工具。</span><span class="sxs-lookup"><span data-stu-id="ea277-106">Using these two namespaces give you the tools to describe how you want to communicate with the native component.</span></span>

<span data-ttu-id="ea277-107">讓我們從最常見的範例中著手，像是在 Managed 程式碼中呼叫 Unmanaged 函式。</span><span class="sxs-lookup"><span data-stu-id="ea277-107">Let’s start from the most common example, and that is calling unmanaged functions in your managed code.</span></span> <span data-ttu-id="ea277-108">現在從命令列應用程式顯示訊息方塊︰</span><span class="sxs-lookup"><span data-stu-id="ea277-108">Let’s show a message box from a command-line application:</span></span>

[!code-csharp[MessageBox](~/samples/snippets/standard/interop/pinvoke/messagebox.cs)]

<span data-ttu-id="ea277-109">上述範例很簡單，但它顯示了從受控碼叫用非受控函式所需的項目。</span><span class="sxs-lookup"><span data-stu-id="ea277-109">The previous example is simple, but it does show off what's needed to invoke unmanaged functions from managed code.</span></span> <span data-ttu-id="ea277-110">現在逐步查看範例︰</span><span class="sxs-lookup"><span data-stu-id="ea277-110">Let’s step through the example:</span></span>

- <span data-ttu-id="ea277-111">行 #1 顯示 `System.Runtime.InteropServices` 命名空間的 using 陳述式，該命名空間持有需要的所有項目。</span><span class="sxs-lookup"><span data-stu-id="ea277-111">Line #1 shows the using statement for the `System.Runtime.InteropServices` namespace that holds all the items needed.</span></span>
- <span data-ttu-id="ea277-112">行 #7 引進 `DllImport` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ea277-112">Line #7 introduces the `DllImport` attribute.</span></span> <span data-ttu-id="ea277-113">此屬性十分重要，因為它會告訴執行階段應載入 Unmanaged DLL。</span><span class="sxs-lookup"><span data-stu-id="ea277-113">This attribute is crucial, as it tells the runtime that it should load the unmanaged DLL.</span></span> <span data-ttu-id="ea277-114">傳入的字串是我們的目標函式所在的 DLL。</span><span class="sxs-lookup"><span data-stu-id="ea277-114">The string passed in is the DLL our target function is in.</span></span> <span data-ttu-id="ea277-115">此外，它會指定要使用哪個[字元集](./charset.md)來對字串進行封送處理。</span><span class="sxs-lookup"><span data-stu-id="ea277-115">Additionally, it specifies which [character set](./charset.md) to use for marshalling the strings.</span></span> <span data-ttu-id="ea277-116">最後，它會指定此函式會呼叫 [SetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-setlasterror)，且執行階段應該擷取錯誤碼，讓使用者可以透過 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error?displayProperty=nameWithType> 擷取它。</span><span class="sxs-lookup"><span data-stu-id="ea277-116">Finally, it specifies that this function calls [SetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-setlasterror) and that the runtime should capture that error code so the user can retrieve it via <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="ea277-117">行 #8 是 P/Invoke 工作的關鍵。</span><span class="sxs-lookup"><span data-stu-id="ea277-117">Line #8 is the crux of the P/Invoke work.</span></span> <span data-ttu-id="ea277-118">它會定義與 Unmanaged 方法具有**同樣簽章**的 Managed 方法。</span><span class="sxs-lookup"><span data-stu-id="ea277-118">It defines a managed method that has the **exact same signature** as the unmanaged one.</span></span> <span data-ttu-id="ea277-119">您可以注意到宣告具有新的關鍵字 `extern`，它會告訴執行階段這就是外部方法，而且當您叫用它時，執行階段應該能在 `DllImport` 屬性指定的 DLL 中找到此關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ea277-119">The declaration has a new keyword that you can notice, `extern`, which tells the runtime this is an external method, and that when you invoke it, the runtime should find it in the DLL specified in `DllImport` attribute.</span></span>

<span data-ttu-id="ea277-120">此範例的其餘部分僅示範如何叫用方法，就如同叫用任何其他 Managed 方法一樣。</span><span class="sxs-lookup"><span data-stu-id="ea277-120">The rest of the example is just invoking the method as you would any other managed method.</span></span>

<span data-ttu-id="ea277-121">此範例和 macOS 上的方法類似。</span><span class="sxs-lookup"><span data-stu-id="ea277-121">The sample is similar for macOS.</span></span> <span data-ttu-id="ea277-122">需要變更 `DllImport` 屬性中的程式庫名稱，因為 macOS 對於命名動態程式庫有不同的配置。</span><span class="sxs-lookup"><span data-stu-id="ea277-122">The name of the library in the `DllImport` attribute needs to change since macOS has a different scheme of naming dynamic libraries.</span></span> <span data-ttu-id="ea277-123">下列範例使用 `getpid(2)` 函式，以取得應用程式的處理序識別碼，並將它列印至主控台：</span><span class="sxs-lookup"><span data-stu-id="ea277-123">The following sample uses the `getpid(2)` function to get the process ID of the application and print it out to the console:</span></span>

[!code-csharp[getpid macOS](~/samples/snippets/standard/interop/pinvoke/getpid-macos.cs)]

<span data-ttu-id="ea277-124">它在 Linux 上也是類似如此。</span><span class="sxs-lookup"><span data-stu-id="ea277-124">It is also similar on Linux.</span></span> <span data-ttu-id="ea277-125">函式名稱相同，是因為 `getpid(2)` 為標準 [POSIX](https://en.wikipedia.org/wiki/POSIX) 系統呼叫。</span><span class="sxs-lookup"><span data-stu-id="ea277-125">The function name is the same, since `getpid(2)` is a standard [POSIX](https://en.wikipedia.org/wiki/POSIX) system call.</span></span>

[!code-csharp[getpid Linux](~/samples/snippets/standard/interop/pinvoke/getpid-linux.cs)]

## <a name="invoking-managed-code-from-unmanaged-code"></a><span data-ttu-id="ea277-126">從 Unmanaged 程式碼叫用 Managed 程式碼</span><span class="sxs-lookup"><span data-stu-id="ea277-126">Invoking managed code from unmanaged code</span></span>

<span data-ttu-id="ea277-127">執行階段允通訊許對雙向流動，讓您可使用函式指標從原生函式回呼受控碼。</span><span class="sxs-lookup"><span data-stu-id="ea277-127">The runtime allows communication to flow in both directions, enabling you to call back into managed code from native functions by using function pointers.</span></span> <span data-ttu-id="ea277-128">與 Managed 程式碼中的函式指標最相似的是**委派**，因此委派被用來允許從原生程式碼回撥至 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ea277-128">The closest thing to a function pointer in managed code is a **delegate**, so this is what is used to allow callbacks from native code into managed code.</span></span>

<span data-ttu-id="ea277-129">使用此功能的方式與上述受控對原生的程序類似。</span><span class="sxs-lookup"><span data-stu-id="ea277-129">The way to use this feature is similar to the managed to native process previously described.</span></span> <span data-ttu-id="ea277-130">針對指定的回呼，您可定義符合特徵標記的委派，並將它傳遞至外部方法中。</span><span class="sxs-lookup"><span data-stu-id="ea277-130">For a given callback, you define a delegate that matches the signature and pass that into the external method.</span></span> <span data-ttu-id="ea277-131">執行階段會處理其他項目。</span><span class="sxs-lookup"><span data-stu-id="ea277-131">The runtime will take care of everything else.</span></span>

[!code-csharp[EnumWindows](~/samples/snippets/standard/interop/pinvoke/enumwindows.cs)]

<span data-ttu-id="ea277-132">開始逐步查看範例之前，建議您先檢閱要使用之非受控函式的特徵標記。</span><span class="sxs-lookup"><span data-stu-id="ea277-132">Before walking through the example, it's good to review the signatures of the unmanaged functions you need to work with.</span></span> <span data-ttu-id="ea277-133">要呼叫來列舉所有視窗的函式具有下列特徵標記：`BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="ea277-133">The function to be called to enumerate all of the windows has the following signature: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span></span>

<span data-ttu-id="ea277-134">第一個參數是回撥。</span><span class="sxs-lookup"><span data-stu-id="ea277-134">The first parameter is a callback.</span></span> <span data-ttu-id="ea277-135">該回撥具有下列簽章：`BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="ea277-135">The said callback has the following signature: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span></span>

<span data-ttu-id="ea277-136">現在，讓我們逐步解說範例：</span><span class="sxs-lookup"><span data-stu-id="ea277-136">Now, let’s walk through the example:</span></span>

- <span data-ttu-id="ea277-137">範例中的行 #9 定義與非受控碼之回呼特徵標記相符的委派。</span><span class="sxs-lookup"><span data-stu-id="ea277-137">Line #9 in the example defines a delegate that matches the signature of the callback from unmanaged code.</span></span> <span data-ttu-id="ea277-138">請注意，在 Managed 程式碼中使用 `IntPtr` 時，LPARAM 和 HWND 類型的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="ea277-138">Notice how the LPARAM and HWND types are represented using `IntPtr` in the managed code.</span></span>
- <span data-ttu-id="ea277-139">行 #13 及 #14 引進 user32.dll 程式庫的 `EnumWindows` 函式。</span><span class="sxs-lookup"><span data-stu-id="ea277-139">Lines #13 and #14 introduce the `EnumWindows` function from the user32.dll library.</span></span>
- <span data-ttu-id="ea277-140">行 #17 - 20 實作委派。</span><span class="sxs-lookup"><span data-stu-id="ea277-140">Lines #17 - 20 implement the delegate.</span></span> <span data-ttu-id="ea277-141">在這個簡單的範例中，我們只想要將控制代碼輸出至主控台。</span><span class="sxs-lookup"><span data-stu-id="ea277-141">For this simple example, we just want to output the handle to the console.</span></span>
- <span data-ttu-id="ea277-142">最後，在行 #24 中，呼叫外部方法並傳入委派。</span><span class="sxs-lookup"><span data-stu-id="ea277-142">Finally, in line #24, the external method is called and passed in the delegate.</span></span>

<span data-ttu-id="ea277-143">Linux 和 macOS 的範例如下所示。</span><span class="sxs-lookup"><span data-stu-id="ea277-143">The Linux and macOS examples are shown below.</span></span> <span data-ttu-id="ea277-144">針對這些作業系統，我們使用 `ftw` 函式，其可在 C 程式庫 `libc` 中找到。</span><span class="sxs-lookup"><span data-stu-id="ea277-144">For them, we use the `ftw` function that can be found in `libc`, the C library.</span></span> <span data-ttu-id="ea277-145">此函式用來周遊目錄階層，並會將函式指標作為其參數之一。</span><span class="sxs-lookup"><span data-stu-id="ea277-145">This function is used to traverse directory hierarchies and it takes a pointer to a function as one of its parameters.</span></span> <span data-ttu-id="ea277-146">此函式具有下列簽章：`int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`。</span><span class="sxs-lookup"><span data-stu-id="ea277-146">The said function has the following signature: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span></span>

[!code-csharp[ftw Linux](~/samples/snippets/standard/interop/pinvoke/ftw-linux.cs)]

<span data-ttu-id="ea277-147">macOS 範例使用相同的函式，而唯一的差別在於 `DllImport` 屬性的引數，macOS 將 `libc` 放置於不同位置。</span><span class="sxs-lookup"><span data-stu-id="ea277-147">macOS example uses the same function, and the only difference is the argument to the `DllImport` attribute, as macOS keeps `libc` in a different place.</span></span>

[!code-csharp[ftw macOS](~/samples/snippets/standard/interop/pinvoke/ftw-macos.cs)]

<span data-ttu-id="ea277-148">上述兩個範例依參數而定，在這兩種情況下，參數會被指定為 Managed 類型。</span><span class="sxs-lookup"><span data-stu-id="ea277-148">Both of the previous examples depend on parameters, and in both cases, the parameters are given as managed types.</span></span> <span data-ttu-id="ea277-149">執行階段會執行「正確的動作」，並將這些項目處理成對等於另一端的項目。</span><span class="sxs-lookup"><span data-stu-id="ea277-149">Runtime does the "right thing" and processes these into its equivalents on the other side.</span></span> <span data-ttu-id="ea277-150">在我們的[類型封送處理](type-marshaling.md)頁面上了解類型如何封送至機器碼。</span><span class="sxs-lookup"><span data-stu-id="ea277-150">Learn about how types are marshaled to native code in our page on [Type marshaling](type-marshaling.md).</span></span>

## <a name="more-resources"></a><span data-ttu-id="ea277-151">更多資源</span><span class="sxs-lookup"><span data-stu-id="ea277-151">More resources</span></span>

- <span data-ttu-id="ea277-152">[PInvoke.net wiki](https://www.pinvoke.net/) \(英文\) 是一個絕佳的 Wiki 網頁，具有通用的 Windows API，以及如何呼叫它們的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ea277-152">[PInvoke.net wiki](https://www.pinvoke.net/) an excellent Wiki with information on common Windows APIs and how to call them.</span></span>
- [<span data-ttu-id="ea277-153">C++/CLI 中的 P/Invoke</span><span class="sxs-lookup"><span data-stu-id="ea277-153">P/Invoke in C++/CLI</span></span>](/cpp/dotnet/native-and-dotnet-interoperability)
- [<span data-ttu-id="ea277-154">P/Invoke 上的 Mono 文件</span><span class="sxs-lookup"><span data-stu-id="ea277-154">Mono documentation on P/Invoke</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/)
