---
title: 字串的預設封送處理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88604058bd460d80214be6051abef7dc561c7710
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="default-marshaling-for-strings"></a>字串的預設封送處理
<xref:System.String?displayProperty=nameWithType> 和 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 類別同時都有類似的封送處理行為。  
  
 會封送處理字串為 COM 樣式 `BSTR` 類型或 Null 終端字串 (以 null 字元結束的字元陣列)。 字串內的字元可以做為 Unicode (Windows 系統上的預設值) 或 ANSI 封送處理。  
  
 本主題提供封送處理字串類型的下列資訊：  
  
-   [在介面中使用的字串](#cpcondefaultmarshalingforstringsanchor1)  
  
-   [在平台叫用中使用的字串](#cpcondefaultmarshalingforstringsanchor5)  
  
-   [在結構中使用的字串](#cpcondefaultmarshalingforstringsanchor2)  
  
-   [固定長度的字串緩衝區](#cpcondefaultmarshalingforstringsanchor3)  
  
<a name="cpcondefaultmarshalingforstringsanchor1"></a>

## <a name="strings-used-in-interfaces"></a>在介面中使用的字串  
 下表顯示當字串資料類型做為方法引數封送處理至 Unmanaged 程式碼時，字串資料類型的封送處理選項。 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性提供幾種 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉值來封送處理字串到 COM 介面。  
  
|列舉類型|Unmanaged 格式的描述|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr` (預設值)|具有前置長度和 Unicode 字元的 COM 樣式 `BSTR`。|  
|`UnmanagedType.LPStr`|ANSI 字元之 Null 終端陣列的指標。|  
|`UnmanagedType.LPWStr`|Unicode 字元之 Null 終端陣列的指標。|  
  
 此表格適用於字串。 不過，為了 <xref:System.Text.StringBuilder>，唯一允許的選項為 `UnmanagedType.LPStr` 和 `UnmanagedType.LPWStr`。  
  
 下列範例會顯示在 `IStringWorker` 介面中所宣告的字串。  
  
```cpp  
public interface IStringWorker {  
void PassString1(String s);  
void PassString2([MarshalAs(UnmanagedType.BStr)]String s);  
void PassString3([MarshalAs(UnmanagedType.LPStr)]String s);  
void PassString4([MarshalAs(UnmanagedType.LPWStr)]String s);  
void PassStringRef1(ref String s);  
void PassStringRef2([MarshalAs(UnmanagedType.BStr)]ref String s);  
void PassStringRef3([MarshalAs(UnmanagedType.LPStr)]ref String s);  
void PassStringRef4([MarshalAs(UnmanagedType.LPWStr)]ref String s);  
);
```

下列範例會顯示在類型程式庫中所述的對應介面。

```
[…]  
interface IStringWorker : IDispatch {  
HRESULT PassString1([in] BSTR s);  
HRESULT PassString2([in] BSTR s);  
HRESULT PassString3([in] LPStr s);  
HRESULT PassString4([in] LPWStr s);  
HRESULT PassStringRef1([in, out] BSTR *s);  
HRESULT PassStringRef2([in, out] BSTR *s);  
HRESULT PassStringRef3([in, out] LPStr *s);  
HRESULT PassStringRef4([in, out] LPWStr *s);  
);
```

<a name="cpcondefaultmarshalingforstringsanchor5"></a>

## <a name="strings-used-in-platform-invoke"></a>在平台叫用中使用的字串  
 平台叫用會複製字串引數，從 .NET Framework 格式 (Unicode) 轉換為平台 Unmanaged 格式。 字串為不可變的，在呼叫傳回時並不會從 Unmanaged 記憶體複製回 Managed 記憶體。  
  
 下表列出當字串做為平台叫用呼叫的方法引數封送處理時的封送處理選項。 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性提供幾種 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉值來封送處理字串。  
  
|列舉類型|Unmanaged 格式的描述|  
|----------------------|-------------------------------------|  
|`UnmanagedType.AnsiBStr`|具有前置長度和 ANSI 字元的 COM 樣式 `BSTR`。|  
|`UnmanagedType.BStr`|具有前置長度和 Unicode 字元的 COM 樣式 `BSTR`。|  
|`UnmanagedType.LPStr`|ANSI 字元之 Null 終端陣列的指標。|  
|`UnmanagedType.LPTStr`|平台相依字元之 Null 終端陣列的指標。|  
|`UnmanagedType.LPWStr`|Unicode 字元之 Null 終端陣列的指標。|  
|`UnmanagedType.TBStr`|具有前置長度和平台相依字元的 COM 樣式 `BSTR`。|  
|`VBByRefStr`|這個值可讓 Visual Basic .NET 變更 Unmanaged 程式碼中的字串，並且讓結果反映在 Managed 程式碼中。 只有平台叫用支援這個值。 這是 `ByVal` 字串在 Visual Basic 中的預設值。|  
  
 此表格適用於字串。 不過，為了 <xref:System.Text.StringBuilder>，唯一允許的選項為 `LPStr`、`LPTStr` 和 `LPWStr`。  
  
 下列類型定義會顯示對於平台叫用呼叫要如何正確使用 `MarshalAsAttribute`。  
  
```vb  
Class StringLibAPI      
Public Declare Auto Sub PassLPStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPStr)> s As String)      
Public Declare Auto Sub PassLPWStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPWStr)> s As String)      
Public Declare Auto Sub PassLPTStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPTStr)> s As String)      
Public Declare Auto Sub PassBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.BStr)> s As String)      
Public Declare Auto Sub PassAnsiBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.AnsiBStr)> s As String)      
Public Declare Auto Sub PassTBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.TBStr)> s As String)  
End Class  
```

```csharp
class StringLibAPI {  
[DllImport("StringLib.Dll")]  
public static extern void PassLPStr([MarshalAs(UnmanagedType.LPStr)]  
String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassLPWStr([MarshalAs(UnmanagedType.LPWStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassLPTStr([MarshalAs(UnmanagedType.LPTStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void PassBStr([MarshalAs(UnmanagedType.BStr)]  
String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassAnsiBStr([MarshalAs(UnmanagedType.AnsiBStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void PassTBStr([MarshalAs(UnmanagedType.TBStr)]  
String s);  
}  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor2"></a>   
## <a name="strings-used-in-structures"></a>在結構中使用的字串  
 字串是結構的有效成員；不過，<xref:System.Text.StringBuilder> 緩衝區在結構中無效。 下表顯示當類型做為欄位封送處理時字串資料類型的封送處理選項。 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性提供幾種 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉值來封送處理字串至欄位。  
  
|列舉類型|Unmanaged 格式的描述|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`|具有前置長度和 Unicode 字元的 COM 樣式 `BSTR`。|  
|`UnmanagedType.LPStr`|ANSI 字元之 Null 終端陣列的指標。|  
|`UnmanagedType.LPTStr`|平台相依字元之 Null 終端陣列的指標。|  
|`UnmanagedType.LPWStr`|Unicode 字元之 Null 終端陣列的指標。|  
|`UnmanagedType.ByValTStr`|一個固定長度的字元陣列；該陣列的類型由包含結構的字元集決定。|  
  
 `ByValTStr` 類型使用於出現在結構中的內嵌固定長度字元陣列。 其他類型適用於包含在結構內的字串參考，其中包含字串的指標。  
  
 套用至包含結構之 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性的 `CharSet` 引數會決定在結構中字串的字元格式。 下列範例結構包含字串的參考和內嵌字串，以及 ANSI、Unicode 和平台相依字元。  
  
### <a name="type-library-representation"></a>類型程式庫表示法  
  
```
struct StringInfoA {  
   char *    f1;  
   char      f2[256];  
};  
struct StringInfoW {  
   WCHAR *   f1;  
   WCHAR     f2[256];  
   BSTR      f3;  
};  
struct StringInfoT {  
   TCHAR *   f1;  
   TCHAR     f2[256];  
};  
```  
  
 下列程式碼範例示範如何使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性在不同格式中定義相同的結構。  
  
```vb  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Ansi)> _  
Structure StringInfoA  
<MarshalAs(UnmanagedType.LPStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
End Structure  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Unicode)> _  
Structure StringInfoW  
<MarshalAs(UnmanagedType.LPWStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
<MarshalAs(UnmanagedType.BStr)> Public f3 As String  
End Structure  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Auto)> _  
Structure StringInfoT  
<MarshalAs(UnmanagedType.LPTStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
End Structure  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Ansi)]  
struct StringInfoA {  
   [MarshalAs(UnmanagedType.LPStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
}  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Unicode)]  
struct StringInfoW {  
   [MarshalAs(UnmanagedType.LPWStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
   [MarshalAs(UnmanagedType.BStr)] public String f3;  
}  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Auto)]  
struct StringInfoT {  
   [MarshalAs(UnmanagedType.LPTStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
}  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor3"></a>   
## <a name="fixed-length-string-buffers"></a>固定長度字串緩衝區  
 在某些情況下，固定長度的字元緩衝區必須傳遞至 Unmanaged 程式碼以進行操作。 在此情況下只傳遞字串無法運作，因為被呼叫端不能修改傳遞緩衝區的內容。 即使該字串以傳址方式傳遞，也沒有任何方式來初始化指定大小的緩衝區。  
  
 解決方式為傳遞 <xref:System.Text.StringBuilder> 緩衝區做為引數，而非字串。 `StringBuilder` 可以為已取值，而且由被呼叫端修改，前提是它不會超過 `StringBuilder` 的容量。 它也可以初始化為固定長度。 例如，如果您初始化 `StringBuilder` 緩衝區為 `N` 的容量，封送處理器會提供 (`N`+1) 個字元大小的緩衝區。 +1 代表 Unmanged 字串具有 null 結束字元，但 `StringBuilder` 沒有。  
  
 例如，Microsoft Win32 API `GetWindowText` 函式 (定義於 Windows.h) 是必須傳遞至 Unmanaged 程式碼操作的固定長度字元緩衝區。 `LpString` 指向大小為 `nMaxCount` 的呼叫端配置緩衝區。 呼叫端必須配置緩衝區，並設定 `nMaxCount` 引數為配置緩衝區的大小。 下列程式碼顯示在 Windows.h 中所定義的 `GetWindowText` 函式宣告。  
  
```  
int GetWindowText(  
HWND hWnd,        // Handle to window or control.  
LPTStr lpString,  // Text buffer.  
int nMaxCount     // Maximum number of characters to copy.  
);  
```  
  
 `StringBuilder` 可以為已取值，而且由被呼叫端修改，前提是它不會超過 `StringBuilder` 的容量。 下列程式碼範例示範可以 `StringBuilder` 如何初始化為固定長度。  
  
```vb  
Public Class Win32API  
Public Declare Auto Sub GetWindowText Lib "User32.Dll" _  
(h As Integer, s As StringBuilder, nMaxCount As Integer)  
End Class  
Public Class Window  
   Friend h As Integer ' Friend handle to Window.  
   Public Function GetText() As String  
      Dim sb As New StringBuilder(256)  
      Win32API.GetWindowText(h, sb, sb.Capacity + 1)  
   Return sb.ToString()  
   End Function  
End Class  
```  
  
```csharp  
public class Win32API {  
[DllImport("User32.Dll")]  
public static extern void GetWindowText(int h, StringBuilder s,   
int nMaxCount);  
}  
public class Window {  
   internal int h;        // Internal handle to Window.  
   public String GetText() {  
      StringBuilder sb = new StringBuilder(256);  
      Win32API.GetWindowText(h, sb, sb.Capacity + 1);  
   return sb.ToString();  
   }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [預設的封送處理行為](default-marshaling-behavior.md)  
 [Blittable 和非 Blittable 類型](blittable-and-non-blittable-types.md)  
 [方向屬性](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))  
 [複製和 Pin](copying-and-pinning.md)
