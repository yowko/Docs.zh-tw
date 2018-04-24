---
title: 原生互通性
description: 了解如何連接到 .NET 中的原生元件。
keywords: .NET, .NET Core
author: blackdwarf
ms.author: ronpet
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3c357112-35fb-44ba-a07b-6a1c140370ac
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d9b0fa5ebe37e51c45a8a5d8a42ce9b9688cc7c1
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="native-interoperability"></a><span data-ttu-id="d2a3d-104">原生互通性</span><span class="sxs-lookup"><span data-stu-id="d2a3d-104">Native Interoperability</span></span>

<span data-ttu-id="d2a3d-105">在本文件中，我們將深入介紹透過 .NET 提供之執行「原生互通性」的三種方式。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-105">In this document, we will dive a little bit deeper into all three ways of doing "native interoperability" that are available using .NET.</span></span>

<span data-ttu-id="d2a3d-106">下列為您要呼叫原生程式碼的幾個原因︰</span><span class="sxs-lookup"><span data-stu-id="d2a3d-106">There are a few of reasons why you would want to call into native code:</span></span>

*   <span data-ttu-id="d2a3d-107">作業系統隨附大量 Managed 類別庫中所沒有的 API。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-107">Operating Systems come with a large volume of APIs that are not present in the managed class libraries.</span></span> <span data-ttu-id="d2a3d-108">此項目的基本範例將會存取硬體或作業系統管理功能。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-108">A prime example for this would be access to hardware or operating system management functions.</span></span>
*   <span data-ttu-id="d2a3d-109">與其他具有或是有可能會產生 C-style ABI (原生 ABI) 的元件進行通訊。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-109">Communicating with other components that have or can produce C-style ABIs (native ABIs).</span></span> <span data-ttu-id="d2a3d-110">比方說，這涵蓋透過 [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) 公開的 Java 程式碼，或任何其他可能會產生原生元件的 Managed 語言。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-110">This covers, for example, Java code that is exposed via [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
*   <span data-ttu-id="d2a3d-111">在 Windows 上，大部分的已安裝軟體 (例如 Microsoft Office 套件) 會註冊 COM 元件，這些元件代表它們的程式，而且可讓開發人員將其自動化或使用它們。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-111">On Windows, most of the software that gets installed, such as Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="d2a3d-112">而這也需要原生互通性。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-112">This also requires native interoperability.</span></span>

<span data-ttu-id="d2a3d-113">當然，上述清單並未涵蓋所有開發人員會想要或需要與原生元件互動的可能情況和情節。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-113">Of course, the list above does not cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="d2a3d-114">舉例來說，.NET 類別庫會使用原生互通性支援來實作其一部分的 API，例如主控台支援和操作、檔案系統存取權及其他項目。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-114">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="d2a3d-115">不過請務必注意，如果情況需要的話，您還有另外的選項。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-115">However, it is important to note that there is an option, should one need it.</span></span>

> [!NOTE]
> <span data-ttu-id="d2a3d-116">本文件中的大部分範例會針對 .NET Core 的所有三種支援平台 (Windows、Linux 和 macOS) 呈現。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-116">Most of the examples in this document will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="d2a3d-117">不過，對於一些簡短和說明性的範例，只會顯示一個使用 Windows 檔名和副檔名 (也就是代表程式庫的 "dll") 的範例。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-117">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="d2a3d-118">這不表示無法在 Linux 或 macOS 上使用這些功能，如此呈現只是為了方便起見。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-118">This does not mean that those features are not available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="platform-invoke-pinvoke"></a><span data-ttu-id="d2a3d-119">平台叫用 (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="d2a3d-119">Platform Invoke (P/Invoke)</span></span>

<span data-ttu-id="d2a3d-120">P/Invoke 是一種技術，可讓您從 Managed 程式碼存取結構、回撥和 Unmanaged 程式庫中的函式。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-120">P/Invoke is a technology that allows you to access structs, callbacks and functions in unmanaged libraries from your managed code.</span></span> <span data-ttu-id="d2a3d-121">大部分的 P/Invoke API 都包含在兩個命名空間中︰`System` 和 `System.Runtime.InteropServices`。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-121">Most of the P/Invoke API is contained in two namespaces: `System` and `System.Runtime.InteropServices`.</span></span> <span data-ttu-id="d2a3d-122">使用這兩個命名空間可讓您存取特定屬性，這些屬性描述您要與原生元件進行通訊的方式。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-122">Using these two namespaces will allow you access to the attributes that describe how you want to communicate with the native component.</span></span>

<span data-ttu-id="d2a3d-123">讓我們從最常見的範例中著手，像是在 Managed 程式碼中呼叫 Unmanaged 函式。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-123">Let’s start from the most common example, and that is calling unmanaged functions in your managed code.</span></span> <span data-ttu-id="d2a3d-124">現在從命令列應用程式顯示訊息方塊︰</span><span class="sxs-lookup"><span data-stu-id="d2a3d-124">Let’s show a message box from a command-line application:</span></span>

```csharp
using System.Runtime.InteropServices;

public class Program {

    // Import user32.dll (containing the function we need) and define
    // the method corresponding to the native function.
    [DllImport("user32.dll")]
    public static extern int MessageBox(IntPtr hWnd, String text, String caption, int options);

    public static void Main(string[] args) {
        // Invoke the function as a regular managed method.
        MessageBox(IntPtr.Zero, "Command-line message box", "Attention!", 0);
    }
}
```

<span data-ttu-id="d2a3d-125">上述範例是很簡單，但它並未示範從 Managed 程式碼叫用 Unmanaged 函式所需的項目。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-125">The example above is pretty simple, but it does show off what is needed to invoke unmanaged functions from managed code.</span></span> <span data-ttu-id="d2a3d-126">現在逐步查看範例︰</span><span class="sxs-lookup"><span data-stu-id="d2a3d-126">Let’s step through the example:</span></span>

*   <span data-ttu-id="d2a3d-127">行 #1 顯示出使用 `System.Runtime.InteropServices` 的陳述式，這是保存所有我們需要項目的命名空間。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-127">Line #1 shows the using statement for the `System.Runtime.InteropServices` which is the namespace that holds all of the items we need.</span></span>
*   <span data-ttu-id="d2a3d-128">行 #5 介紹 `DllImport` 屬性。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-128">Line #5 introduces the `DllImport` attribute.</span></span> <span data-ttu-id="d2a3d-129">此屬性十分重要，因為它會告訴執行階段應載入 Unmanaged DLL。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-129">This attribute is crucial, as it tells the runtime that it should load the unmanaged DLL.</span></span> <span data-ttu-id="d2a3d-130">這就是我們要叫用的 DLL。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-130">This is the DLL into which we wish to invoke.</span></span>
*   <span data-ttu-id="d2a3d-131">行 #6 是 P/Invoke 工作的關鍵。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-131">Line #6 is the crux of the P/Invoke work.</span></span> <span data-ttu-id="d2a3d-132">它會定義與 Unmanaged 方法具有**同樣簽章**的 Managed 方法。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-132">It defines a managed method that has the **exact same signature** as the unmanaged one.</span></span> <span data-ttu-id="d2a3d-133">您可以注意到宣告具有新的關鍵字 `extern`，它會告訴執行階段這就是外部方法，而且當您叫用它時，執行階段應該能在 `DllImport` 屬性指定的 DLL 中找到此關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-133">The declaration has a new keyword that you can notice, `extern`, which tells the runtime this is an external method, and that when you invoke it, the runtime should find it in the DLL specified in `DllImport` attribute.</span></span>

<span data-ttu-id="d2a3d-134">此範例的其餘部分僅示範如何叫用方法，就如同叫用任何其他 Managed 方法一樣。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-134">The rest of the example is just invoking the method as you would any other managed method.</span></span>

<span data-ttu-id="d2a3d-135">此範例和 macOS 上的方法類似。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-135">The sample is similar for macOS.</span></span> <span data-ttu-id="d2a3d-136">當然，其中有一個項目有所不同，此項目為 `DllImport` 屬性中程式庫的名稱，因為 macOS 命名動態程式庫有不同的配置。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-136">One thing that needs to change is, of course, the name of the library in the `DllImport` attribute, as macOS has a different scheme of naming dynamic libraries.</span></span> <span data-ttu-id="d2a3d-137">下列範例使用 `getpid(2)` 函式，以取得應用程式的處理序識別碼，並將其列印至主控台。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-137">The sample below uses the `getpid(2)` function to get the process ID of the application and print it out to the console.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libSystem shared library and define the method corresponding to the native function.
        [DllImport("libSystem.dylib")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

<span data-ttu-id="d2a3d-138">它在 Linux 上也是類似如此。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-138">It is also similar on Linux.</span></span> <span data-ttu-id="d2a3d-139">函式名稱相同，是因為 `getpid(2)` 為標準 [POSIX](https://en.wikipedia.org/wiki/POSIX) 系統呼叫。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-139">The function name is the same, since `getpid(2)` is a standard [POSIX](https://en.wikipedia.org/wiki/POSIX) system call.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc shared library and define the method corresponding to the native function.
        [DllImport("libc.so.6")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

### <a name="invoking-managed-code-from-unmanaged-code"></a><span data-ttu-id="d2a3d-140">從 Unmanaged 程式碼叫用 Managed 程式碼</span><span class="sxs-lookup"><span data-stu-id="d2a3d-140">Invoking managed code from unmanaged code</span></span>

<span data-ttu-id="d2a3d-141">當然，執行階段允許互相進行通訊，這讓您可使用函式指標，從原生函式呼叫 Managed 成品。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-141">Of course, the runtime allows communication to flow both ways which enables you to call into managed artifacts from native functions, using function pointers.</span></span> <span data-ttu-id="d2a3d-142">與 Managed 程式碼中的函式指標最相似的是**委派**，因此委派被用來允許從原生程式碼回撥至 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-142">The closest thing to a function pointer in managed code is a **delegate**, so this is what is used to allow callbacks from native code into managed code.</span></span>

<span data-ttu-id="d2a3d-143">使用這項功能的方式和上述將 Managed 轉換至原生程序類似。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-143">The way to use this feature is similar to managed to native process described above.</span></span> <span data-ttu-id="d2a3d-144">針對指定的回撥，您可定義符合簽章的委派，並將它傳遞至外部方法。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-144">For a given callback, you define a delegate that matches the signature, and pass that into the external method.</span></span> <span data-ttu-id="d2a3d-145">執行階段會處理其他項目。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-145">The runtime will take care of everything else.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace ConsoleApplication1 {

    class Program {

        // Define a delegate that corresponds to the unmanaged function.
        delegate bool EnumWC(IntPtr hwnd, IntPtr lParam);

        // Import user32.dll (containing the function we need) and define
        // the method corresponding to the native function.
        [DllImport("user32.dll")]
        static extern int EnumWindows(EnumWC lpEnumFunc, IntPtr lParam);

        // Define the implementation of the delegate; here, we simply output the window handle.
        static bool OutputWindow(IntPtr hwnd, IntPtr lParam) {
            Console.WriteLine(hwnd.ToInt64());
            return true;
        }

        static void Main(string[] args) {
            // Invoke the method; note the delegate as a first parameter.
            EnumWindows(OutputWindow, IntPtr.Zero);
        }
    }
}
```

<span data-ttu-id="d2a3d-146">在我們逐步解說範例之前，先了解我們要使用的 Unmanaged 函式簽章將有所助益。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-146">Before we walk through our example, it is good to go over the signatures of the unmanaged functions we need to work with.</span></span> <span data-ttu-id="d2a3d-147">我們想要呼叫以列舉所有視窗的函式具有下列簽章︰`BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="d2a3d-147">The function we want to call to enumerate all of the windows has the following signature: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span></span>

<span data-ttu-id="d2a3d-148">第一個參數是回撥。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-148">The first parameter is a callback.</span></span> <span data-ttu-id="d2a3d-149">該回撥具有下列簽章：`BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="d2a3d-149">The said callback has the following signature: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span></span>

<span data-ttu-id="d2a3d-150">記住這一點後，讓我們逐步解說範例︰</span><span class="sxs-lookup"><span data-stu-id="d2a3d-150">With this in mind, let’s walk through the example:</span></span>

*   <span data-ttu-id="d2a3d-151">範例中的行 #8 定義與 Unmanaged 程式碼之回呼簽章相符的委派。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-151">Line #8 in the example defines a delegate that matches the signature of the callback from unmanaged code.</span></span> <span data-ttu-id="d2a3d-152">請注意，在 Managed 程式碼中使用 `IntPtr` 時，LPARAM 和 HWND 類型的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-152">Notice how the LPARAM and HWND types are represented using `IntPtr` in the managed code.</span></span>
*   <span data-ttu-id="d2a3d-153">行 #10 及 #11 介紹 user32.dll 程式庫的 `EnumWindows` 函式。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-153">Lines #10 and #11 introduce the `EnumWindows` function from the user32.dll library.</span></span>
*   <span data-ttu-id="d2a3d-154">行 #13-16 實作委派。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-154">Lines #13 - 16 implement the delegate.</span></span> <span data-ttu-id="d2a3d-155">在這個簡單的範例中，我們只想要將控制代碼輸出至主控台。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-155">For this simple example, we just want to output the handle to the console.</span></span>
*   <span data-ttu-id="d2a3d-156">最後，在行 #19 中我們叫用外部方法並傳入委派。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-156">Finally, in line #19 we invoke the external method and pass in the delegate.</span></span>

<span data-ttu-id="d2a3d-157">Linux 和 macOS 的範例如下所示。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-157">The Linux and macOS examples are shown below.</span></span> <span data-ttu-id="d2a3d-158">針對這些作業系統，我們使用 `ftw` 函式，其可在 C 程式庫 `libc` 中找到。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-158">For them, we use the `ftw` function that can be found in `libc`, the C library.</span></span> <span data-ttu-id="d2a3d-159">此函式用來周遊目錄階層，並會將函式指標作為其參數之一。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-159">This function is used to traverse directory hierarchies and it takes a pointer to a function as one of its parameters.</span></span> <span data-ttu-id="d2a3d-160">此函式具有下列簽章：`int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-160">The said function has the following signature: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

            // Define a delegate that has the same signature as the native function.
            delegate int DirClbk(string fName, StatClass stat, int typeFlag);

            // Import the libc and define the method to represent the native function.
            [DllImport("libc.so.6")]
            static extern int ftw(string dirpath, DirClbk cl, int descriptors);

            // Implement the above DirClbk delegate;
            // this one just prints out the filename that is passed to it.
            static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                    Console.WriteLine(fName);
                    return 0;
            }

            public static void Main(string[] args){
                    // Call the native function.
                    // Note the second parameter which represents the delegate (callback).
                    ftw(".", DisplayEntry, 10);
            }
    }

    // The native callback takes a pointer to a struct. The below class
    // represents that struct in managed code. You can find more information
    // about this in the section on marshalling below.
    [StructLayout(LayoutKind.Sequential)]
    public class StatClass {
            public uint DeviceID;
            public uint InodeNumber;
            public uint Mode;
            public uint HardLinks;
            public uint UserID;
            public uint GroupID;
            public uint SpecialDeviceID;
            public ulong Size;
            public ulong BlockSize;
            public uint Blocks;
            public long TimeLastAccess;
            public long TimeLastModification;
            public long TimeLastStatusChange;
    }
}
```

<span data-ttu-id="d2a3d-161">macOS 範例使用相同的函式，而唯一的差別在於 `DllImport` 屬性的引數，macOS 將 `libc` 放置於不同位置。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-161">macOS example uses the same function, and the only difference is the argument to the `DllImport` attribute, as macOS keeps `libc` in a different place.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
        public static class Program {

                // Define a delegate that has the same signature as the native function.
                delegate int DirClbk(string fName, StatClass stat, int typeFlag);

                // Import the libc and define the method to represent the native function.
                [DllImport("libSystem.dylib")]
                static extern int ftw(string dirpath, DirClbk cl, int descriptors);

                // Implement the above DirClbk delegate;
                // this one just prints out the filename that is passed to it.
                static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                        Console.WriteLine(fName);
                        return 0;
                }

                public static void Main(string[] args){
                        // Call the native function.
                        // Note the second parameter which represents the delegate (callback).
                        ftw(".", DisplayEntry, 10);
                }
        }

        // The native callback takes a pointer to a struct. The below class
        // represents that struct in managed code. You can find more information
        // about this in the section on marshalling below.
        [StructLayout(LayoutKind.Sequential)]
        public class StatClass {
                public uint DeviceID;
                public uint InodeNumber;
                public uint Mode;
                public uint HardLinks;
                public uint UserID;
                public uint GroupID;
                public uint SpecialDeviceID;
                public ulong Size;
                public ulong BlockSize;
                public uint Blocks;
                public long TimeLastAccess;
                public long TimeLastModification;
                public long TimeLastStatusChange;
        }
}
```

<span data-ttu-id="d2a3d-162">以上兩個範例依參數而定，在這兩種情況下，參數會被指定為 Managed 類型。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-162">Both of the above examples depend on parameters, and in both cases, the parameters are given as managed types.</span></span> <span data-ttu-id="d2a3d-163">執行階段會執行「正確的動作」，並將這些項目處理成對等於另一端的項目。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-163">Runtime does the "right thing" and processes these into its equivalents on the other side.</span></span> <span data-ttu-id="d2a3d-164">此程序對原生 Interop 程式碼的撰寫品質十分重要，讓我們看看執行階段_封送處理_類型時會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-164">Since this process is really important to writing quality native interop code, let’s take a look at what happens when the runtime _marshals_ the types.</span></span>

## <a name="type-marshalling"></a><span data-ttu-id="d2a3d-165">封送處理類型</span><span class="sxs-lookup"><span data-stu-id="d2a3d-165">Type marshalling</span></span>

<span data-ttu-id="d2a3d-166">當類型要跨 Managed 界限進入原生類型時，**封送處理**為轉換類型的程序，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-166">**Marshalling** is the process of transforming types when they need to cross the managed boundary into native and vice versa.</span></span>

<span data-ttu-id="d2a3d-167">因為 Managed 和 Unmanaged 程式碼中的類型不同，所以需要封送處理。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-167">The reason marshalling is needed is because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="d2a3d-168">例如，在 Managed 程式碼中會有 `String`，而在 Unmanaged 程式碼中，字串可以是 Unicode (「寬」)、非 Unicode、以 null 終止的及 ASCII 等等。依預設，P/Invoke 子系統會嘗試執行以預設行為為基礎的正確動作，您可以在 [MSDN](../../docs/framework/interop/default-marshaling-behavior.md) 查看這些動作。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-168">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem will try to do the Right Thing based on the default behavior which you can see on [MSDN](../../docs/framework/interop/default-marshaling-behavior.md).</span></span> <span data-ttu-id="d2a3d-169">不過，在您需要進行額外控制的情況下，您可以運用 `MarshalAs` 屬性來指定 Unmanaged 這一端的預期類型。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-169">However, for those situations where you need extra control, you can employ the `MarshalAs` attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="d2a3d-170">比方說，如果我們想要用以 null 終止的 ANSI 字串形式來傳送字串，我們可以下列方式執行它︰</span><span class="sxs-lookup"><span data-stu-id="d2a3d-170">For instance, if we want the string to be sent as a null-terminated ANSI string, we could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

### <a name="marshalling-classes-and-structs"></a><span data-ttu-id="d2a3d-171">封送處理類別和結構</span><span class="sxs-lookup"><span data-stu-id="d2a3d-171">Marshalling classes and structs</span></span>

<span data-ttu-id="d2a3d-172">封送處理類型的另一個層面是如何將結構傳遞給 Unmanaged 方法。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-172">Another aspect of type marshalling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="d2a3d-173">比方說，有些 Unmanaged 方法需要結構以作為參數。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-173">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="d2a3d-174">在這些情況下，我們需要建立對應的結構或類別，以將它作為 Managed 項目中的參數。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-174">In these cases, we need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="d2a3d-175">不過，只定義類別是不夠的，我們也必須指示封送處理器如何將類別中的欄位對應至 Unmanaged 結構。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-175">However, just defining the class is not enough, we also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="d2a3d-176">這正是 `StructLayout` 屬性派上用場的時候。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-176">This is where the `StructLayout` attribute comes into play.</span></span>

```csharp
[DllImport("kernel32.dll")]
static extern void GetSystemTime(SystemTime systemTime);

[StructLayout(LayoutKind.Sequential)]
class SystemTime {
    public ushort Year;
    public ushort Month;
    public ushort DayOfWeek;
    public ushort Day;
    public ushort Hour;
    public ushort Minute;
    public ushort Second;
    public ushort Milsecond;
}

public static void Main(string[] args) {
    SystemTime st = new SystemTime();
    GetSystemTime(st);
    Console.WriteLine(st.Year);
}
```

<span data-ttu-id="d2a3d-177">上述範例顯示了一個呼叫至 `GetSystemTime()` 函式的簡單範例。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-177">The example above shows off a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="d2a3d-178">請注意第 4 行。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-178">The interesting bit is on line 4.</span></span> <span data-ttu-id="d2a3d-179">此屬性會指定類別的欄位應該循序對應至 Unmanaged 這一端上的結構。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-179">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="d2a3d-180">這表示欄位的命名並不重要，只有它們的順序很重要，因為順序需要對應至 Unmanaged 結構，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="d2a3d-180">This means that the naming of the fields is not important, only their order is important, as it needs to correspond to the unmanaged struct, shown below:</span></span>

```c
typedef struct _SYSTEMTIME {
  WORD wYear;
  WORD wMonth;
  WORD wDayOfWeek;
  WORD wDay;
  WORD wHour;
  WORD wMinute;
  WORD wSecond;
  WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME*;
```

<span data-ttu-id="d2a3d-181">我們已經在上述範例中看到了此步驟的 Linux 和 macOS 範例。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-181">We already saw the Linux and macOS example for this in the previous example.</span></span> <span data-ttu-id="d2a3d-182">下方會再示範一次。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-182">It is shown again below.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential)]
public class StatClass {
        public uint DeviceID;
        public uint InodeNumber;
        public uint Mode;
        public uint HardLinks;
        public uint UserID;
        public uint GroupID;
        public uint SpecialDeviceID;
        public ulong Size;
        public ulong BlockSize;
        public uint Blocks;
        public long TimeLastAccess;
        public long TimeLastModification;
        public long TimeLastStatusChange;
}
```

<span data-ttu-id="d2a3d-183">`StatClass` 類別代表 UNIX 系統上 `stat` 系統呼叫所傳回的結構。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-183">The `StatClass` class represents a structure that is returned by the `stat` system call on UNIX systems.</span></span> <span data-ttu-id="d2a3d-184">它代表指定檔案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-184">It represents information about a given file.</span></span> <span data-ttu-id="d2a3d-185">上述類別在 Managed 程式碼中為 stat 結構表示法。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-185">The class above is the stat struct representation in managed code.</span></span> <span data-ttu-id="d2a3d-186">同樣地，類別中的欄位一定要和原生結構有相同的順序 (您可以在您喜愛的 UNIX 實作手冊頁上找到這些資訊)，它們擁有相同的基礎類型。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-186">Again, the fields in the class have to be in the same order as the native struct (you can find these by perusing man pages on your favorite UNIX implementation) and they have to be of the same underlying type.</span></span>

## <a name="more-resources"></a><span data-ttu-id="d2a3d-187">更多資源</span><span class="sxs-lookup"><span data-stu-id="d2a3d-187">More resources</span></span>

*   <span data-ttu-id="d2a3d-188">[PInvoke.net wiki](https://www.pinvoke.net/) 是一個絕佳的 Wiki 網頁，具有通用的 Win32 API，以及如何呼叫它們的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d2a3d-188">[PInvoke.net wiki](https://www.pinvoke.net/) an excellent Wiki with information on common Win32 APIs and how to call them.</span></span>
*   [<span data-ttu-id="d2a3d-189">P/Invoke on MSDN</span><span class="sxs-lookup"><span data-stu-id="d2a3d-189">P/Invoke on MSDN</span></span>](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [<span data-ttu-id="d2a3d-190">P/Invoke 上的 Mono 文件</span><span class="sxs-lookup"><span data-stu-id="d2a3d-190">Mono documentation on P/Invoke</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/)
