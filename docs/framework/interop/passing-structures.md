---
title: "傳遞結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a30905fdcf7063f6ecdae0346c9c5ee39b450be9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="passing-structures"></a><span data-ttu-id="b4373-102">傳遞結構</span><span class="sxs-lookup"><span data-stu-id="b4373-102">Passing Structures</span></span>
<span data-ttu-id="b4373-103">許多 Unmanaged 函式都需要您將其傳遞為函式的參數、結構成員 (Visual Basic 中的使用者定義型別) 或使用 Managed 程式碼所定義類別的成員。</span><span class="sxs-lookup"><span data-stu-id="b4373-103">Many unmanaged functions expect you to pass, as a parameter to the function, members of structures (user-defined types in Visual Basic) or members of classes that are defined in managed code.</span></span> <span data-ttu-id="b4373-104">使用平台叫用將結構或類別傳遞至 Unmanaged 程式碼時，您必須提供其他資訊來保留原始配置和對齊方式。</span><span class="sxs-lookup"><span data-stu-id="b4373-104">When passing structures or classes to unmanaged code using platform invoke, you must provide additional information to preserve the original layout and alignment.</span></span> <span data-ttu-id="b4373-105">本主題介紹用來定義格式化類型的 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="b4373-105">This topic introduces the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute, which you use to define formatted types.</span></span> <span data-ttu-id="b4373-106">針對 Managed 結構和類別，您可以從 **LayoutKind** 列舉所提供的數個可預測配置行為中進行選取。</span><span class="sxs-lookup"><span data-stu-id="b4373-106">For managed structures and classes, you can select from several predictable layout behaviors supplied by the **LayoutKind** enumeration.</span></span>  
  
 <span data-ttu-id="b4373-107">本主題中所呈現概念的中心是結構與類別類型之間的重要差異。</span><span class="sxs-lookup"><span data-stu-id="b4373-107">Central to the concepts presented in this topic is an important difference between structure and class types.</span></span> <span data-ttu-id="b4373-108">結構是實值型別，而類別是參考型別 - 類別一律會提供至少一層記憶體間接取值 (實值的指標)。</span><span class="sxs-lookup"><span data-stu-id="b4373-108">Structures are value types and classes are reference types — classes always provide at least one level of memory indirection (a pointer to a value).</span></span> <span data-ttu-id="b4373-109">這項差異十分重要，因為 Unmanaged 函式通常要求間接取值，如下表第一個資料行中的簽章所示。</span><span class="sxs-lookup"><span data-stu-id="b4373-109">This difference is important because unmanaged functions often demand indirection, as shown by the signatures in the first column of the following table.</span></span> <span data-ttu-id="b4373-110">其餘資料行中的 Managed 結構和類別宣告會顯示您可調整宣告中間接取值層級的目標程度。所提供的宣告同時適用於 Visual Basic 和 Visual C#。</span><span class="sxs-lookup"><span data-stu-id="b4373-110">The managed structure and class declarations in the remaining columns show the degree to which you can adjust the level of indirection in your declaration.Declarations are provided for both Visual Basic and Visual C#.</span></span>  
  
|<span data-ttu-id="b4373-111">Unmanaged 簽章</span><span class="sxs-lookup"><span data-stu-id="b4373-111">Unmanaged signature</span></span>|<span data-ttu-id="b4373-112">Managed 宣告：</span><span class="sxs-lookup"><span data-stu-id="b4373-112">Managed declaration:</span></span> <br /><span data-ttu-id="b4373-113">無間接取值</span><span class="sxs-lookup"><span data-stu-id="b4373-113">no indirection</span></span><br />`Structure MyType`<br />`struct MyType;`|<span data-ttu-id="b4373-114">Managed 宣告：</span><span class="sxs-lookup"><span data-stu-id="b4373-114">Managed declaration:</span></span> <br /><span data-ttu-id="b4373-115">一層間接取值</span><span class="sxs-lookup"><span data-stu-id="b4373-115">one level of indirection</span></span><br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> <span data-ttu-id="b4373-116">要求零層間接取值。</span><span class="sxs-lookup"><span data-stu-id="b4373-116">Demands zero levels of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="b4373-117">兩層間接取值。</span><span class="sxs-lookup"><span data-stu-id="b4373-117">Adds zero levels of indirection.</span></span>|<span data-ttu-id="b4373-118">無法進行，因為已有一層間接取值。</span><span class="sxs-lookup"><span data-stu-id="b4373-118">Not possible because there is already one level of indirection.</span></span>|  
|`DoWork(MyType* x);`<br /><br /> <span data-ttu-id="b4373-119">要求一層間接取值。</span><span class="sxs-lookup"><span data-stu-id="b4373-119">Demands one level of indirection.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="b4373-120">新增一層間接取值。</span><span class="sxs-lookup"><span data-stu-id="b4373-120">Adds one level of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="b4373-121">兩層間接取值。</span><span class="sxs-lookup"><span data-stu-id="b4373-121">Adds zero levels of indirection.</span></span>|  
|`DoWork(MyType** x);`<br /><br /> <span data-ttu-id="b4373-122">要求兩層間接取值。</span><span class="sxs-lookup"><span data-stu-id="b4373-122">Demands two levels of indirection.</span></span>|<span data-ttu-id="b4373-123">不可行，因為無法使用 **ByRef** **ByRef** 或 `ref` `ref`。</span><span class="sxs-lookup"><span data-stu-id="b4373-123">Not possible because **ByRef** **ByRef** or `ref` `ref` cannot be used.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="b4373-124">新增一層間接取值。</span><span class="sxs-lookup"><span data-stu-id="b4373-124">Adds one level of indirection.</span></span>|  
  
 <span data-ttu-id="b4373-125">此表格描述下列平台叫用宣告方針：</span><span class="sxs-lookup"><span data-stu-id="b4373-125">The table describes the following guidelines for platform invoke declarations:</span></span>  
  
-   <span data-ttu-id="b4373-126">Unmanaged 函式未要求間接取值時，請使用以傳值方式傳遞的結構。</span><span class="sxs-lookup"><span data-stu-id="b4373-126">Use a structure passed by value when the unmanaged function demands no indirection.</span></span>  
  
-   <span data-ttu-id="b4373-127">Unmanaged 函式要求一層間接取值時，請使用以傳址方式傳遞的結構或以傳值方式傳遞的類別。</span><span class="sxs-lookup"><span data-stu-id="b4373-127">Use either a structure passed by reference or a class passed by value when the unmanaged function demands one level of indirection.</span></span>  
  
-   <span data-ttu-id="b4373-128">Unmanaged 函式要求兩層間接取值時，請使用以傳址方式傳遞的類別。</span><span class="sxs-lookup"><span data-stu-id="b4373-128">Use a class passed by reference when the unmanaged function demands two levels of indirection.</span></span>  
  
## <a name="declaring-and-passing-structures"></a><span data-ttu-id="b4373-129">宣告和傳遞結構</span><span class="sxs-lookup"><span data-stu-id="b4373-129">Declaring and Passing Structures</span></span>  
 <span data-ttu-id="b4373-130">下列範例示範如何使用 Managed 程式碼定義 `Point` 和 `Rect` 結構，並將類型當成參數傳遞至 User32.dll 檔案中的 **PtInRect** 函式。</span><span class="sxs-lookup"><span data-stu-id="b4373-130">The following example shows how to define the `Point` and `Rect` structures in managed code, and pass the types as parameter to the **PtInRect** function in the User32.dll file.</span></span> <span data-ttu-id="b4373-131">**PtInRect** 具有下列 Unmanaged 簽章：</span><span class="sxs-lookup"><span data-stu-id="b4373-131">**PtInRect** has the following unmanaged signature:</span></span>  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="b4373-132">請注意，您必須以傳址方式傳遞 Rect 結構，因為此函式需要有 RECT 類型的指標。</span><span class="sxs-lookup"><span data-stu-id="b4373-132">Notice that you must pass the Rect structure by reference, since the function expects a pointer to a RECT type.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
    Public x As Integer  
    Public y As Integer  
End Structure  
  
Public Structure <StructLayout(LayoutKind.Explicit)> Rect  
    <FieldOffset(0)> Public left As Integer  
    <FieldOffset(4)> Public top As Integer  
    <FieldOffset(8)> Public right As Integer  
    <FieldOffset(12)> Public bottom As Integer  
End Structure  
  
Class Win32API      
    Declare Auto Function PtInRect Lib "user32.dll" _  
    (ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
    public int x;  
    public int y;  
}     
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
    [FieldOffset(0)] public int left;  
    [FieldOffset(4)] public int top;  
    [FieldOffset(8)] public int right;  
    [FieldOffset(12)] public int bottom;  
}     
  
class Win32API {  
    [DllImport("User32.dll")]  
    public static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a><span data-ttu-id="b4373-133">宣告和傳遞類別</span><span class="sxs-lookup"><span data-stu-id="b4373-133">Declaring and Passing Classes</span></span>  
 <span data-ttu-id="b4373-134">只要類別具有固定成員配置，您就可以將類別的成員傳遞至 Unmanaged DLL 函式。</span><span class="sxs-lookup"><span data-stu-id="b4373-134">You can pass members of a class to an unmanaged DLL function, as long as the class has a fixed member layout.</span></span> <span data-ttu-id="b4373-135">下列範例示範如何以定義的循序順序將 `MySystemTime` 類別成員傳遞至 User32.dll 檔案中的 **GetSystemTime**。</span><span class="sxs-lookup"><span data-stu-id="b4373-135">The following example demonstrates how to pass members of the `MySystemTime` class, which are defined in sequential order, to the **GetSystemTime** in the User32.dll file.</span></span> <span data-ttu-id="b4373-136">**GetSystemTime** 具有下列 Unmanaged 簽章：</span><span class="sxs-lookup"><span data-stu-id="b4373-136">**GetSystemTime** has the following unmanaged signature:</span></span>  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="b4373-137">與實值型別不同，類別一律會有至少一層間接取值。</span><span class="sxs-lookup"><span data-stu-id="b4373-137">Unlike value types, classes always have at least one level of indirection.</span></span>  
  
```vb  
Imports System  
Imports System.Runtime.InteropServices  
Imports Microsoft.VisualBasic  
  
<StructLayout(LayoutKind.Sequential)> Public Class MySystemTime  
    Public wYear As Short  
    Public wMonth As Short  
    Public wDayOfWeek As Short   
    Public wDay As Short  
    Public wHour As Short  
    Public wMinute As Short  
    Public wSecond As Short  
    Public wMiliseconds As Short  
End Class  
  
Public Class Win32  
    Declare Auto Sub GetSystemTime Lib "Kernel32.dll"(sysTime _  
        As MySystemTime)  
    Declare Auto Function MessageBox Lib "User32.dll"(hWnd As IntPtr, _  
        txt As String, caption As String, Typ As Integer) As Integer  
End Class  
  
Public Class TestPlatformInvoke      
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        Win32.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        Win32.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)        
    End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class MySystemTime {  
    public ushort wYear;   
    public ushort wMonth;  
    public ushort wDayOfWeek;   
    public ushort wDay;   
    public ushort wHour;   
    public ushort wMinute;   
    public ushort wSecond;   
    public ushort wMilliseconds;   
}  
class Win32API {  
    [DllImport("Kernel32.dll")]  
    public static extern void GetSystemTime(MySystemTime st);  
  
    [DllImport("user32.dll", CharSet=CharSet.Auto)]  
     public static extern int MessageBox(IntPtr hWnd,  
         string text, string caption, int options);  
}  
  
public class TestPlatformInvoke  
{  
    public static void Main()  
    {  
        MySystemTime sysTime = new MySystemTime();  
        Win32API.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        Win32API.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4373-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="b4373-138">See Also</span></span>  
 [<span data-ttu-id="b4373-139">呼叫 DLL 函式</span><span class="sxs-lookup"><span data-stu-id="b4373-139">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
