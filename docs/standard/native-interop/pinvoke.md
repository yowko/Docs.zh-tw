---
title: 平台叫用 (P/Invoke)
description: 了解如何在 .NET 中透過 P/Invoke 呼叫原生函式。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: f243fee2b246afff36732d469c6295d7e4b2fd87
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "56411380"
---
# <a name="platform-invoke-pinvoke"></a>平台叫用 (P/Invoke)

P/Invoke 是一種技術，可讓您從受控碼存取結構、回呼和非受控程式庫中的函式。 大部分的 P/Invoke API 都包含在兩個命名空間中︰`System` 和 `System.Runtime.InteropServices`。 使用這兩個命名空間會提供您可描述您想要如何與原生元件互動的工具。

讓我們從最常見的範例中著手，像是在 Managed 程式碼中呼叫 Unmanaged 函式。 現在從命令列應用程式顯示訊息方塊︰

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

上述範例很簡單，但它顯示了從受控碼叫用非受控函式所需的項目。 現在逐步查看範例︰

*   行 #1 顯示 `System.Runtime.InteropServices` 命名空間的 using 陳述式，該命名空間持有需要的所有項目。
*   行 #7 引進 `DllImport` 屬性。 此屬性十分重要，因為它會告訴執行階段應載入 Unmanaged DLL。 傳入的字串是我們的目標函式所在的 DLL。
*   行 #8 是 P/Invoke 工作的關鍵。 它會定義與 Unmanaged 方法具有**同樣簽章**的 Managed 方法。 您可以注意到宣告具有新的關鍵字 `extern`，它會告訴執行階段這就是外部方法，而且當您叫用它時，執行階段應該能在 `DllImport` 屬性指定的 DLL 中找到此關鍵字。

此範例的其餘部分僅示範如何叫用方法，就如同叫用任何其他 Managed 方法一樣。

此範例和 macOS 上的方法類似。 需要變更 `DllImport` 屬性中的程式庫名稱，因為 macOS 對於命名動態程式庫有不同的配置。 下列範例使用 `getpid(2)` 函式，以取得應用程式的處理序識別碼，並將它列印至主控台：

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

它在 Linux 上也是類似如此。 函式名稱相同，是因為 `getpid(2)` 為標準 [POSIX](https://en.wikipedia.org/wiki/POSIX) 系統呼叫。

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

## <a name="invoking-managed-code-from-unmanaged-code"></a>從 Unmanaged 程式碼叫用 Managed 程式碼

執行階段允通訊許對雙向流動，讓您可使用函式指標從原生函式回呼受控碼。 與 Managed 程式碼中的函式指標最相似的是**委派**，因此委派被用來允許從原生程式碼回撥至 Managed 程式碼。

使用此功能的方式與上述受控對原生的程序類似。 針對指定的回呼，您可定義符合特徵標記的委派，並將它傳遞至外部方法中。 執行階段會處理其他項目。

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

開始逐步查看範例之前，建議您先檢閱要使用之非受控函式的特徵標記。 要呼叫來列舉所有視窗的函式具有下列特徵標記：`BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

第一個參數是回撥。 該回撥具有下列簽章：`BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

現在，讓我們逐步解說範例：

*   範例中的行 #9 定義與非受控碼之回呼特徵標記相符的委派。 請注意，在 Managed 程式碼中使用 `IntPtr` 時，LPARAM 和 HWND 類型的呈現方式。
*   行 #13 及 #14 引進 user32.dll 程式庫的 `EnumWindows` 函式。
*   行 #17 - 20 實作委派。 在這個簡單的範例中，我們只想要將控制代碼輸出至主控台。
*   最後，在行 #24 中，呼叫外部方法並傳入委派。

Linux 和 macOS 的範例如下所示。 針對這些作業系統，我們使用 `ftw` 函式，其可在 C 程式庫 `libc` 中找到。 此函式用來周遊目錄階層，並會將函式指標作為其參數之一。 此函式具有下列簽章：`int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`。

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

macOS 範例使用相同的函式，而唯一的差別在於 `DllImport` 屬性的引數，macOS 將 `libc` 放置於不同位置。

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
        // represents that struct in managed code.
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

上述兩個範例依參數而定，在這兩種情況下，參數會被指定為 Managed 類型。 執行階段會執行「正確的動作」，並將這些項目處理成對等於另一端的項目。 在我們的[類型封送處理](type-marshalling.md)頁面上了解類型如何封送至機器碼。


## <a name="more-resources"></a>更多資源

*   [PInvoke.net wiki](https://www.pinvoke.net/) 是一個絕佳的 Wiki 網頁，具有通用的 Win32 API，以及如何呼叫它們的相關資訊。
*   [P/Invoke on MSDN](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [P/Invoke 上的 Mono 文件](https://www.mono-project.com/docs/advanced/pinvoke/)
