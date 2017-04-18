---
title: "傳遞結構 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "平台叫用, 呼叫 Unmanaged 函式"
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# 傳遞結構
許多 Unmanaged 的函式會要您將參數傳遞給函式、在 Managed 程式碼中所定義的結構 \(也就是 Visual Basic 中的使用者定義型別\) 成員或類別成員。  當使用平台叫用傳遞結構或類別至 Unmanaged 程式碼時，您必須提供額外的資訊以保留原始配置與對齊。  本主題將介紹定義格式化型別所使用的 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性。  針對 Managed 結構與類別而言，您可以從多個 **LayoutKind** 列舉所提供之可預測配置行為中予以選取。  
  
 本主題中所要呈現的中心概念在於結構與類別型別之間的一些主要差異。  結構為實值型別，而類別為參考型別，類別永遠會提供至少一個層級的記憶體間接取值 \(Indirection\) \(數值指標\)。  這項差異是很重要的，因為 Unmanaged 函式通常會要求間接取值，如同下表第一個欄位中的簽章所顯示的。  在其餘欄位中的 Managed 結構與類別宣告顯示您可以在宣告中調整之間接取值層級範圍。  Visual Basic 和 Visual C\# 均可使用宣告。  
  
|Unmanaged 簽章|Managed 宣告：               <br /> 無間接取值 \(Indirection\)               <br />  `Structure MyType`  <br />  `struct MyType;`|Managed 宣告：               <br /> 層級一間接取值               <br />  `Class MyType`  <br />  `class MyType;`|  
|------------------|-------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> 要求層級零的間接取值。|`DoWork(ByVal x As MyType)`  <br />  `DoWork(MyType x)`<br /><br /> 加入層級零的間接取值。|不可能，因為已經有層級一的間接取值。|  
|`DoWork(MyType* x);`<br /><br /> 要求層級一的間接取值。|`DoWork(ByRef x As MyType)`  <br />  `DoWork(ref MyType x)`<br /><br /> 加入層級一的間接取值。|`DoWork(ByVal x As MyType)`  <br />  `DoWork(MyType x)`<br /><br /> 加入層級零的間接取值。|  
|`DoWork(MyType** x);`<br /><br /> 要求層級二的間接取值。|不可能，因為無法使用 **ByRef** **ByRef**或是`ref` `ref`。|`DoWork(ByRef x As MyType)`  <br />  `DoWork(ref MyType x)`<br /><br /> 加入層級一的間接取值。|  
  
 該表格說明下列平台叫用宣告的方針：  
  
-   當 Unmanaged 函式不要求任何間接取值時，請使用傳值方式的結構。  
  
-   當 Unmanaged 函式要求層級一的間接取值時，請使用傳址方式結構或傳值方式類別。  
  
-   當 Unmanaged 函式要求層級二的間接取值時，請使用傳址方式類別。  
  
## 宣告與傳遞結構  
 以下範例示範如何在 Managed 程式碼中定義 `Point` 和 `Rect` 結構，並且將型別做為參數傳遞給 User32.dll 檔案中的 **PtInRect** 函式。  **PtInRect** 具有下列 Unmanaged 簽章：  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 請注意，您必須以傳址 \(By Reference\) 方式傳遞 Rect 結構，因為這個函式需要一個指向 RECT 型別的指標。  
  
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
  
## 宣告與傳遞類別  
 只要類別具有固定的成員配置，您就可以將類別的成員傳遞給 Unmanaged DLL 函式。  以下範例示範如何將以循序順序定義的 `MySystemTime` 類別的成員傳遞給 User32.dll 檔案中的 **GetSystemTime**。  **GetSystemTime** 具有以下 Unmanaged 簽章：  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 與實值型別不同的是，類別永遠會有至少一個層級的間接取值。  
  
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
  
## 請參閱  
 [呼叫 DLL 函式](../../../docs/framework/interop/calling-a-dll-function.md)   
 [StructLayoutAttribute 類別](frlrfSystemRuntimeInteropServicesStructLayoutAttributeClassTopic)   
 [StructLayoutAttribute 類別](frlrfSystemRuntimeInteropServicesStructLayoutAttributeClassTopic)   
 [FieldOffsetAttribute 類別](frlrfSystemRuntimeInteropServicesFieldOffsetAttributeClassTopic)