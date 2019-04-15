---
title: 傳遞結構
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c8e35a09bd3348d5f53c662cf6e0ee9fec733d88
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142814"
---
# <a name="passing-structures"></a>傳遞結構
許多 Unmanaged 函式都需要您將其傳遞為函式的參數、結構成員 (Visual Basic 中的使用者定義型別) 或使用 Managed 程式碼所定義類別的成員。 使用平台叫用將結構或類別傳遞至 Unmanaged 程式碼時，您必須提供其他資訊來保留原始配置和對齊方式。 本主題介紹用來定義格式化類型的 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性。 針對 Managed 結構和類別，您可以從 **LayoutKind** 列舉所提供的數個可預測配置行為中進行選取。  
  
 本主題中所呈現概念的中心是結構與類別類型之間的重要差異。 結構是實值型別，而類別是參考型別 - 類別一律會提供至少一層記憶體間接取值 (實值的指標)。 這項差異十分重要，因為 Unmanaged 函式通常要求間接取值，如下表第一個資料行中的簽章所示。 其餘資料行中的 Managed 結構和類別宣告會顯示您可調整宣告中間接取值層級的目標程度。所提供的宣告同時適用於 Visual Basic 和 Visual C#。  
  
|Unmanaged 簽章|Managed 宣告： <br />無間接取值<br />`Structure MyType`<br />`struct MyType;`|Managed 宣告： <br />一層間接取值<br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> 要求零層間接取值。|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> 兩層間接取值。|無法進行，因為已有一層間接取值。|  
|`DoWork(MyType* x);`<br /><br /> 要求一層間接取值。|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> 新增一層間接取值。|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> 兩層間接取值。|  
|`DoWork(MyType** x);`<br /><br /> 要求兩層間接取值。|不可行，因為無法使用 **ByRef** **ByRef** 或 `ref` `ref`。|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> 新增一層間接取值。|  
  
 此表格描述下列平台叫用宣告方針：  
  
-   Unmanaged 函式未要求間接取值時，請使用以傳值方式傳遞的結構。  
  
-   Unmanaged 函式要求一層間接取值時，請使用以傳址方式傳遞的結構或以傳值方式傳遞的類別。  
  
-   Unmanaged 函式要求兩層間接取值時，請使用以傳址方式傳遞的類別。  
  
## <a name="declaring-and-passing-structures"></a>宣告和傳遞結構  
 下列範例示範如何使用 Managed 程式碼定義 `Point` 和 `Rect` 結構，並將類型當成參數傳遞至 User32.dll 檔案中的 **PtInRect** 函式。 **PtInRect** 具有下列 Unmanaged 簽章：  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 請注意，您必須以傳址方式傳遞 Rect 結構，因為此函式需要有 RECT 類型的指標。  
  
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
  
Friend Class WindowsAPI      
    Friend Shared Declare Auto Function PtInRect Lib "user32.dll" (
        ByRef r As Rect, p As Point) As Boolean  
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
  
internal static class WindowsAPI
{  
    [DllImport("User32.dll")]  
    internal static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a>宣告和傳遞類別  
 只要類別具有固定成員配置，您就可以將類別的成員傳遞至 Unmanaged DLL 函式。 下列範例示範如何以定義的循序順序將 `MySystemTime` 類別成員傳遞至 User32.dll 檔案中的 **GetSystemTime**。 **GetSystemTime** 具有下列 Unmanaged 簽章：  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 與實值型別不同，類別一律會有至少一層間接取值。  
  
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
  
Friend Class WindowsAPI  
    Friend Shared Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        sysTime As MySystemTime)  
    Friend Shared Declare Auto Function MessageBox Lib "User32.dll" (
        hWnd As IntPtr, lpText As String, lpCaption As String, uType As UInteger) As Integer  
End Class  
  
Public Class TestPlatformInvoke      
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        WindowsAPI.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        WindowsAPI.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)        
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
internal static class WindowsAPI
{  
    [DllImport("Kernel32.dll")]  
    internal static extern void GetSystemTime(MySystemTime st);  
  
    [DllImport("user32.dll", CharSet = CharSet.Auto)]  
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);  
}  
  
public class TestPlatformInvoke  
{  
    public static void Main()  
    {  
        MySystemTime sysTime = new MySystemTime();  
        WindowsAPI.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        WindowsAPI.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱

- [呼叫 DLL 函式](../../../docs/framework/interop/calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
