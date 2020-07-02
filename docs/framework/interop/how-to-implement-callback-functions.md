---
title: 作法：實作回呼函式
description: 請參閱如何執行回呼函式。 在此範例中，使用平台叫用的受控應用程式會列印電腦上每個視窗的控制碼值。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- callback function, implementing
ms.assetid: e55b3712-b9ea-4453-bd9a-ad5cfa2f6bfa
ms.openlocfilehash: 31c657372e760c8d57f9714b20178967ad85fcd3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619113"
---
# <a name="how-to-implement-callback-functions"></a><span data-ttu-id="c35b4-104">作法：實作回呼函式</span><span class="sxs-lookup"><span data-stu-id="c35b4-104">How to: Implement Callback Functions</span></span>
<span data-ttu-id="c35b4-105">下列程序及範例示範 Managed 應用程式 (使用平台叫用) 如何將每個視窗的控制碼值列印到本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="c35b4-105">The following procedure and example demonstrate how a managed application, using platform invoke, can print the handle value for each window on the local computer.</span></span> <span data-ttu-id="c35b4-106">具體而言，程序和範例會使用 **EnumWindows** 函式以逐步執行視窗的清單，並使用 Managed 回呼函式 (具名回呼) 以列印視窗控制代碼的值。</span><span class="sxs-lookup"><span data-stu-id="c35b4-106">Specifically, the procedure and example use the **EnumWindows** function to step through the list of windows and a managed callback function (named CallBack) to print the value of the window handle.</span></span>  
  
### <a name="to-implement-a-callback-function"></a><span data-ttu-id="c35b4-107">若要實作回撥函式</span><span class="sxs-lookup"><span data-stu-id="c35b4-107">To implement a callback function</span></span>  
  
1. <span data-ttu-id="c35b4-108">進一步進行實作前，請先查看 **EnumWindows** 函式的簽章。</span><span class="sxs-lookup"><span data-stu-id="c35b4-108">Look at the signature for the **EnumWindows** function before going further with the implementation.</span></span> <span data-ttu-id="c35b4-109">**EnumWindows** 具有下列簽章：</span><span class="sxs-lookup"><span data-stu-id="c35b4-109">**EnumWindows** has the following signature:</span></span>  
  
    ```cpp
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)
    ```
  
     <span data-ttu-id="c35b4-110">此函式需要進行回呼的一個線索在於 **lpEnumFunc** 引數。</span><span class="sxs-lookup"><span data-stu-id="c35b4-110">One clue that this function requires a callback is the presence of the **lpEnumFunc** argument.</span></span> <span data-ttu-id="c35b4-111">**lp** (長度指標) 前置詞與 **Func** 後置詞的結合出現在引數名稱中的情況相當普遍，其會將指標帶到回呼函式。</span><span class="sxs-lookup"><span data-stu-id="c35b4-111">It is common to see the **lp** (long pointer) prefix combined with the **Func** suffix in the name of arguments that take a pointer to a callback function.</span></span> <span data-ttu-id="c35b4-112">如需 Win32 函式的相關文件，請參閱 Microsoft Platform SDK。</span><span class="sxs-lookup"><span data-stu-id="c35b4-112">For documentation about Win32 functions, see the Microsoft Platform SDK.</span></span>  
  
2. <span data-ttu-id="c35b4-113">建立 Managed 回撥函式。</span><span class="sxs-lookup"><span data-stu-id="c35b4-113">Create the managed callback function.</span></span> <span data-ttu-id="c35b4-114">此範例會宣告稱為 `CallBack` 的委派型別，其採用兩個引數 (**hwnd** 和 **lparam**)。</span><span class="sxs-lookup"><span data-stu-id="c35b4-114">The example declares a delegate type, called `CallBack`, which takes two arguments (**hwnd** and **lparam**).</span></span> <span data-ttu-id="c35b4-115">第一個引數是視窗的控制代碼；第二個引數則由應用程式定義。</span><span class="sxs-lookup"><span data-stu-id="c35b4-115">The first argument is a handle to the window; the second argument is application-defined.</span></span> <span data-ttu-id="c35b4-116">在此版本中，兩個引數都必須是整數。</span><span class="sxs-lookup"><span data-stu-id="c35b4-116">In this release, both arguments must be integers.</span></span>  
  
     <span data-ttu-id="c35b4-117">回撥函式通常傳回非零值即表示成功，傳回零則表示失敗。</span><span class="sxs-lookup"><span data-stu-id="c35b4-117">Callback functions generally return nonzero values to indicate success and zero to indicate failure.</span></span> <span data-ttu-id="c35b4-118">此範例將傳回的值明確設定為 **true** 以繼續列舉。</span><span class="sxs-lookup"><span data-stu-id="c35b4-118">This example explicitly sets the return value to **true** to continue the enumeration.</span></span>  
  
3. <span data-ttu-id="c35b4-119">建立委派，並將其以引數方式傳遞至 **EnumWindows** 函式。</span><span class="sxs-lookup"><span data-stu-id="c35b4-119">Create a delegate and pass it as an argument to the **EnumWindows** function.</span></span> <span data-ttu-id="c35b4-120">平台叫用會自動將委派轉換成熟悉的回撥格式。</span><span class="sxs-lookup"><span data-stu-id="c35b4-120">Platform invoke converts the delegate to a familiar callback format automatically.</span></span>  
  
4. <span data-ttu-id="c35b4-121">請確定記憶體回收行程不會在回撥函式完成其工作前，回收該委派。</span><span class="sxs-lookup"><span data-stu-id="c35b4-121">Ensure that the garbage collector does not reclaim the delegate before the callback function completes its work.</span></span> <span data-ttu-id="c35b4-122">當您將委派以參數 (或結構中的欄位) 方式傳遞時，其將在呼叫期間保持為未回收。</span><span class="sxs-lookup"><span data-stu-id="c35b4-122">When you pass a delegate as a parameter, or pass a delegate contained as a field in a structure, it remains uncollected for the duration of the call.</span></span> <span data-ttu-id="c35b4-123">因此，在以下列舉範例中，回撥函式在呼叫傳回前即會完成該工作，且不需要 Managed 呼叫端進行額外的動作。</span><span class="sxs-lookup"><span data-stu-id="c35b4-123">So, as is the case in the following enumeration example, the callback function completes its work before the call returns and requires no additional action by the managed caller.</span></span>  
  
     <span data-ttu-id="c35b4-124">但是，如果呼叫傳回後仍然可以叫用回撥函式，則 Managed 呼叫端必須採取步驟，以確保在回撥函式結束前，委派仍保持未回收。</span><span class="sxs-lookup"><span data-stu-id="c35b4-124">If, however, the callback function can be invoked after the call returns, the managed caller must take steps to ensure that the delegate remains uncollected until the callback function finishes.</span></span> <span data-ttu-id="c35b4-125">如需避免記憶體回收的詳細資訊，請參閱含有平台叫用的 [Interop 封送處理](interop-marshaling.md)。</span><span class="sxs-lookup"><span data-stu-id="c35b4-125">For detailed information about preventing garbage collection, see [Interop Marshaling](interop-marshaling.md) with Platform Invoke.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c35b4-126">範例</span><span class="sxs-lookup"><span data-stu-id="c35b4-126">Example</span></span>  
  
```vb  
Imports System  
Imports System.Runtime.InteropServices  
  
Public Delegate Function CallBack( _  
hwnd As Integer, lParam As Integer) As Boolean  
  
Public Class EnumReportApp  
  
    Declare Function EnumWindows Lib "user32" ( _  
       x As CallBack, y As Integer) As Integer  
  
    Public Shared Sub Main()  
        EnumWindows(AddressOf EnumReportApp.Report, 0)  
    End Sub 'Main  
  
    Public Shared Function Report(hwnd As Integer, lParam As Integer) _  
    As Boolean  
        Console.Write("Window handle is ")  
        Console.WriteLine(hwnd)  
        Return True  
    End Function 'Report  
End Class 'EnumReportApp  
```  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public delegate bool CallBack(int hwnd, int lParam);  
  
public class EnumReportApp  
{  
    [DllImport("user32")]  
    public static extern int EnumWindows(CallBack x, int y);
  
    public static void Main()
    {  
        CallBack myCallBack = new CallBack(EnumReportApp.Report);  
        EnumWindows(myCallBack, 0);  
    }  
  
    public static bool Report(int hwnd, int lParam)  
    {
        Console.Write("Window handle is ");  
        Console.WriteLine(hwnd);  
        return true;  
    }  
}  
```  
  
```cpp  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
// A delegate type.  
delegate bool CallBack(int hwnd, int lParam);  
  
// Managed type with the method to call.  
ref class EnumReport  
{  
// Report the window handle.  
public:  
    [DllImport("user32")]  
    static int EnumWindows(CallBack^ x, int y);  
  
    static void Main()  
    {  
        EnumReport^ er = gcnew EnumReport;  
        CallBack^ myCallBack = gcnew CallBack(&EnumReport::Report);  
        EnumWindows(myCallBack, 0);  
    }  
  
    static bool Report(int hwnd, int lParam)  
    {  
       Console::Write(L"Window handle is ");  
       Console::WriteLine(hwnd);  
       return true;  
    }  
};  
  
int main()  
{  
    EnumReport::Main();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c35b4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c35b4-127">See also</span></span>

- [<span data-ttu-id="c35b4-128">回呼函式</span><span class="sxs-lookup"><span data-stu-id="c35b4-128">Callback Functions</span></span>](callback-functions.md)
- [<span data-ttu-id="c35b4-129">呼叫 DLL 函式</span><span class="sxs-lookup"><span data-stu-id="c35b4-129">Calling a DLL Function</span></span>](calling-a-dll-function.md)
