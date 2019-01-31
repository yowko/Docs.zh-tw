---
title: HOW TO：實作回呼函式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- callback function, implementing
ms.assetid: e55b3712-b9ea-4453-bd9a-ad5cfa2f6bfa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bf972455aa54a7fe45ffd7858ac9e5da5eee6e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718672"
---
# <a name="how-to-implement-callback-functions"></a><span data-ttu-id="dd406-102">HOW TO：實作回呼函式</span><span class="sxs-lookup"><span data-stu-id="dd406-102">How to: Implement Callback Functions</span></span>
<span data-ttu-id="dd406-103">下列程序及範例示範 Managed 應用程式 (使用平台叫用) 如何將每個視窗的控制碼值列印到本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="dd406-103">The following procedure and example demonstrate how a managed application, using platform invoke, can print the handle value for each window on the local computer.</span></span> <span data-ttu-id="dd406-104">具體而言，程序和範例會使用 **EnumWindows** 函式以逐步執行視窗的清單，並使用 Managed 回呼函式 (具名回呼) 以列印視窗控制代碼的值。</span><span class="sxs-lookup"><span data-stu-id="dd406-104">Specifically, the procedure and example use the **EnumWindows** function to step through the list of windows and a managed callback function (named CallBack) to print the value of the window handle.</span></span>  
  
### <a name="to-implement-a-callback-function"></a><span data-ttu-id="dd406-105">若要實作回撥函式</span><span class="sxs-lookup"><span data-stu-id="dd406-105">To implement a callback function</span></span>  
  
1.  <span data-ttu-id="dd406-106">進一步進行實作前，請先查看 **EnumWindows** 函式的簽章。</span><span class="sxs-lookup"><span data-stu-id="dd406-106">Look at the signature for the **EnumWindows** function before going further with the implementation.</span></span> <span data-ttu-id="dd406-107">**EnumWindows** 具有下列簽章：</span><span class="sxs-lookup"><span data-stu-id="dd406-107">**EnumWindows** has the following signature:</span></span>  
  
    ```  
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)  
    ```  
  
     <span data-ttu-id="dd406-108">此函式需要進行回呼的一個線索在於 **lpEnumFunc** 引數。</span><span class="sxs-lookup"><span data-stu-id="dd406-108">One clue that this function requires a callback is the presence of the **lpEnumFunc** argument.</span></span> <span data-ttu-id="dd406-109">**lp** (長度指標) 前置詞與 **Func** 後置詞的結合出現在引數名稱中的情況相當普遍，其會將指標帶到回呼函式。</span><span class="sxs-lookup"><span data-stu-id="dd406-109">It is common to see the **lp** (long pointer) prefix combined with the **Func** suffix in the name of arguments that take a pointer to a callback function.</span></span> <span data-ttu-id="dd406-110">如需 Win32 函式的相關文件，請參閱 Microsoft Platform SDK。</span><span class="sxs-lookup"><span data-stu-id="dd406-110">For documentation about Win32 functions, see the Microsoft Platform SDK.</span></span>  
  
2.  <span data-ttu-id="dd406-111">建立 Managed 回撥函式。</span><span class="sxs-lookup"><span data-stu-id="dd406-111">Create the managed callback function.</span></span> <span data-ttu-id="dd406-112">此範例會宣告稱為 `CallBack` 的委派型別，其採用兩個引數 (**hwnd** 和 **lparam**)。</span><span class="sxs-lookup"><span data-stu-id="dd406-112">The example declares a delegate type, called `CallBack`, which takes two arguments (**hwnd** and **lparam**).</span></span> <span data-ttu-id="dd406-113">第一個引數是視窗的控制代碼；第二個引數則由應用程式定義。</span><span class="sxs-lookup"><span data-stu-id="dd406-113">The first argument is a handle to the window; the second argument is application-defined.</span></span> <span data-ttu-id="dd406-114">在此版本中，兩個引數都必須是整數。</span><span class="sxs-lookup"><span data-stu-id="dd406-114">In this release, both arguments must be integers.</span></span>  
  
     <span data-ttu-id="dd406-115">回撥函式通常傳回非零值即表示成功，傳回零則表示失敗。</span><span class="sxs-lookup"><span data-stu-id="dd406-115">Callback functions generally return nonzero values to indicate success and zero to indicate failure.</span></span> <span data-ttu-id="dd406-116">此範例將傳回的值明確設定為 **true** 以繼續列舉。</span><span class="sxs-lookup"><span data-stu-id="dd406-116">This example explicitly sets the return value to **true** to continue the enumeration.</span></span>  
  
3.  <span data-ttu-id="dd406-117">建立委派，並將其以引數方式傳遞至 **EnumWindows** 函式。</span><span class="sxs-lookup"><span data-stu-id="dd406-117">Create a delegate and pass it as an argument to the **EnumWindows** function.</span></span> <span data-ttu-id="dd406-118">平台叫用會自動將委派轉換成熟悉的回撥格式。</span><span class="sxs-lookup"><span data-stu-id="dd406-118">Platform invoke converts the delegate to a familiar callback format automatically.</span></span>  
  
4.  <span data-ttu-id="dd406-119">請確定記憶體回收行程不會在回撥函式完成其工作前，回收該委派。</span><span class="sxs-lookup"><span data-stu-id="dd406-119">Ensure that the garbage collector does not reclaim the delegate before the callback function completes its work.</span></span> <span data-ttu-id="dd406-120">當您將委派以參數 (或結構中的欄位) 方式傳遞時，其將在呼叫期間保持為未回收。</span><span class="sxs-lookup"><span data-stu-id="dd406-120">When you pass a delegate as a parameter, or pass a delegate contained as a field in a structure, it remains uncollected for the duration of the call.</span></span> <span data-ttu-id="dd406-121">因此，在以下列舉範例中，回撥函式在呼叫傳回前即會完成該工作，且不需要 Managed 呼叫端進行額外的動作。</span><span class="sxs-lookup"><span data-stu-id="dd406-121">So, as is the case in the following enumeration example, the callback function completes its work before the call returns and requires no additional action by the managed caller.</span></span>  
  
     <span data-ttu-id="dd406-122">但是，如果呼叫傳回後仍然可以叫用回撥函式，則 Managed 呼叫端必須採取步驟，以確保在回撥函式結束前，委派仍保持未回收。</span><span class="sxs-lookup"><span data-stu-id="dd406-122">If, however, the callback function can be invoked after the call returns, the managed caller must take steps to ensure that the delegate remains uncollected until the callback function finishes.</span></span> <span data-ttu-id="dd406-123">如需避免記憶體回收的詳細資訊，請參閱含有平台叫用的 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)。</span><span class="sxs-lookup"><span data-stu-id="dd406-123">For detailed information about preventing garbage collection, see [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md) with Platform Invoke.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd406-124">範例</span><span class="sxs-lookup"><span data-stu-id="dd406-124">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd406-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd406-125">See also</span></span>
- [<span data-ttu-id="dd406-126">回呼函式</span><span class="sxs-lookup"><span data-stu-id="dd406-126">Callback Functions</span></span>](../../../docs/framework/interop/callback-functions.md)
- [<span data-ttu-id="dd406-127">呼叫 DLL 函式</span><span class="sxs-lookup"><span data-stu-id="dd406-127">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
