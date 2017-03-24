---
title: "原生互通性"
description: "原生互通性"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: ronpet
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3c357112-35fb-44ba-a07b-6a1c140370ac
translationtype: Human Translation
ms.sourcegitcommit: d18b21b67c154c4a8cf8211aa5d1473066c53656
ms.openlocfilehash: 13a4e4e7a588d55e82c5c4cde8f825c3b4502bb4
ms.lasthandoff: 03/02/2017

---

# <a name="native-interoperability"></a>原生互通性

在本文件中，我們將深入介紹可在 .NET 平台上執行「原生互通性」的三種方式。

下列為您要呼叫原生程式碼的幾個原因︰

*   作業系統隨附大量 Managed 類別庫中所沒有的 API。 此項目的基本範例將會存取硬體或作業系統管理功能。
*   與其他具有或是有可能會產生 C-style ABI (原生 ABI) 的元件進行通訊。 比方說，這涵蓋透過 [Java Native Interface (JNI)](http://docs.oracle.com/javase/8/docs/technotes/guides/jni/) 公開的 Java 程式碼，或任何其他可能會產生原生元件的 Managed 語言。
*   在 Windows 上，大部分的已安裝軟體 (例如 Microsoft Office 套件) 會註冊 COM 元件，這些元件代表它們的程式，而且可讓開發人員將其自動化或使用它們。 而這也需要原生互通性。

當然，上述清單並未涵蓋所有開發人員會想要或需要與原生元件互動的可能情況和情節。 舉例來說，.NET 類別庫會使用原生互通性支援來實作其一部分的 API，例如主控台支援和操作、檔案系統存取權及其他項目。 不過請務必注意，如果情況需要的話，您還有另外的選項。

> [!NOTE]
> 本文件中的大部分範例會針對 .NET Core 的所有三種支援平台 (Windows、Linux 和 macOS) 呈現。 不過，對於一些簡短和說明性的範例，只會顯示一個使用 Windows 檔名和副檔名 (也就是「dll」程式庫) 的範例。 這不表示無法在 Linux 或 macOS 上使用這些功能，如此呈現只是為了方便起見。

## <a name="platform-invoke-pinvoke"></a>平台叫用 (P/Invoke)

P/Invoke 是一種技術，可讓您從 Managed 程式碼存取結構、回撥和 Unmanaged 程式庫中的函式。 大部分的 P/Invoke API 都包含在兩個命名空間中︰`System` 和 `System.Runtime.InteropServices`。 使用這兩個命名空間可讓您存取特定屬性，這些屬性描述您要與原生元件進行通訊的方式。

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

上述範例是很簡單，但它並未示範從 Managed 程式碼叫用 Unmanaged 函式所需的項目。 現在逐步查看範例︰

*   行 #1 顯示出使用 `System.Runtime.InteropServices` 的陳述式，這是保存所有我們需要項目的命名空間。
*   行 #5 介紹 `DllImport` 屬性。 此屬性十分重要，因為它會告訴執行階段應載入 Unmanaged DLL。 這就是我們要叫用的 DLL。
*   行 #6 是 P/Invoke 工作的關鍵。 它會定義與 Unmanaged 方法具有**同樣簽章**的 Managed 方法。 您可以注意到宣告具有新的關鍵字 `extern`，它會告訴執行階段這就是外部方法，而且當您叫用它時，執行階段應該能在 `DllImport` 屬性指定的 DLL 中找到此關鍵字。

此範例的其餘部分僅示範如何叫用方法，就如同叫用任何其他 Managed 方法一樣。

此範例和 macOS 上的方法類似。 當然，其中有一個項目有所不同，此項目為 `DllImport` 屬性中程式庫的名稱，因為 macOS 命名動態程式庫有不同的配置。 下列範例使用 `getpid(2)` 函式，以取得應用程式的處理序識別碼，並將其列印至主控台。

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc and define the method corresponding to the native function.
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

當然，這和在 Linux 上的處理方式類似。 函式名稱相同，是因為 `getpid(2)` 為 [POSIX](https://en.wikipedia.org/wiki/POSIX) 系統呼叫。

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc and define the method corresponding to the native function.
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

### <a name="invoking-managed-code-from-unmanaged-code"></a>從 Unmanaged 程式碼叫用 Managed 程式碼

當然，執行階段允許互相進行通訊，這讓您可使用函式指標，從原生函式呼叫 Managed 成品。 與 Managed 程式碼中的函式指標最相似的是**委派**，因此委派被用來允許從原生程式碼回撥至 Managed 程式碼。

使用這項功能的方式和上述將 Managed 轉換至原生程序類似。 針對指定的回撥，您可定義符合簽章的委派，並將它傳遞至外部方法。 執行階段會處理其他項目。

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
        static extern int EnumWindows(EnumWC hWnd, IntPtr lParam);

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

在我們逐步解說範例之前，先了解我們要使用的 Unmanaged 函式簽章將有所助益。 我們想要呼叫以列舉所有視窗的函式具有下列簽章︰`BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

第一個參數是回撥。 該回撥具有下列簽章：`BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

記住這一點後，讓我們逐步解說範例︰

*   範例中的行 #8 定義與 Unmanaged 程式碼之回呼簽章相符的委派。 請注意，在 Managed 程式碼中使用 `IntPtr` 時，LPARAM 和 HWND 類型的呈現方式。
*   行 #10 及 #11 介紹 user32.dll 程式庫的 `EnumWindows` 函式。
*   行 #13-16 實作委派。 在這個簡單的範例中，我們只想要將控制代碼輸出至主控台。
*   最後，在行 #19 中我們叫用外部方法並傳入委派。

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

以上兩個範例依參數而定，在這兩種情況下，參數會被指定為 Managed 類型。 執行階段會執行「正確的動作」，並將這些項目處理成對等於另一端的項目。 此程序對原生 Interop 程式碼的撰寫品質十分重要，讓我們看看執行階段_封送處理_類型時會發生什麼事。

## <a name="type-marshalling"></a>封送處理類型

當類型要跨 Managed 界限進入原生類型時，**封送處理**為轉換類型的程序，反之亦然。

因為 Managed 和 Unmanaged 程式碼中的類型不同，所以需要封送處理。 比方說，在 Managed 程式碼中會有 `String`，而在 Unmanaged 程式碼中，字串可以是 Unicode (「寬」)、非 Unicode、以 null 終止的、ASCII 等等。依預設，P/Invoke 子系統會嘗試執行以預設行為為基礎的正確動作，您可以在 [MSDN](https://msdn.microsoft.com/library/zah6xy75.aspx) 查看這些動作。 不過，在您需要進行額外控制的情況下，您可以運用 `MarshalAs` 屬性來指定 Unmanaged 這一端的預期類型。 比方說，如果我們想要用以 null 終止的 ANSI 字串形式來傳送字串，我們可以下列方式執行它︰

```csharp
[DllImport("somenativelibrary.dll"]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);

```

### <a name="marshalling-classes-and-structs"></a>封送處理類別和結構

封送處理類型的另一個層面是如何將結構傳遞給 Unmanaged 方法。 比方說，有些 Unmanaged 方法需要結構以作為參數。 在這些情況下，我們需要建立對應的結構或類別，以將它作為 Managed 項目中的參數。 不過，只定義類別是不夠的，我們也必須指示封送處理器如何將類別中的欄位對應至 Unmanaged 結構。 這正是 `StructLayout` 屬性派上用場的時候。

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

上述範例顯示了一個呼叫至 `GetSystemTime()` 函式的簡單範例。 有趣的地方在於第 4 行的 \.。此屬性會指定類別的欄位應該循序對應至 Unmanaged 這一端上的結構。 這表示欄位的命名並不重要，只有它們的順序很重要，因為順序需要對應至 Unmanaged 結構，如下所示︰

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

我們已經在上述範例中看到了此步驟的 Linux 和 macOS 範例。 下方會再示範一次。

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

`StatClass` 類別代表 UNIX 系統上 `stat` 系統呼叫所傳回的結構。 它代表指定檔案的相關資訊。 上述類別在 Managed 程式碼中為 stat 結構表示法。 同樣地，類別中的欄位一定要和原生結構有相同的順序 (您可以在您喜愛的 UNIX 實作手冊頁上找到這些資訊)，它們擁有相同的基礎類型。

## <a name="more-resources"></a>更多資源

*   [PInvoke.net wiki](http://www.pinvoke.net) 是一個絕佳的 Wiki 網頁，具有通用的 Win32 API，以及如何呼叫它們的相關資訊。
*   [P/Invoke on MSDN](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [P/Invoke 上的 Mono 文件](http://www.mono-project.com/docs/advanced/pinvoke/)

