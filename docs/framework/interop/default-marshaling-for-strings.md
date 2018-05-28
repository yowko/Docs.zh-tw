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
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="493ed-102">字串的預設封送處理</span><span class="sxs-lookup"><span data-stu-id="493ed-102">Default Marshaling for Strings</span></span>
<span data-ttu-id="493ed-103"><xref:System.String?displayProperty=nameWithType> 和 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 類別同時都有類似的封送處理行為。</span><span class="sxs-lookup"><span data-stu-id="493ed-103">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>  
  
 <span data-ttu-id="493ed-104">會封送處理字串為 COM 樣式 `BSTR` 類型或 Null 終端字串 (以 null 字元結束的字元陣列)。</span><span class="sxs-lookup"><span data-stu-id="493ed-104">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="493ed-105">字串內的字元可以做為 Unicode (Windows 系統上的預設值) 或 ANSI 封送處理。</span><span class="sxs-lookup"><span data-stu-id="493ed-105">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>  
  
 <span data-ttu-id="493ed-106">本主題提供封送處理字串類型的下列資訊：</span><span class="sxs-lookup"><span data-stu-id="493ed-106">This topic provides the following information on marshaling string types:</span></span>  
  
-   [<span data-ttu-id="493ed-107">在介面中使用的字串</span><span class="sxs-lookup"><span data-stu-id="493ed-107">Strings Used in Interfaces</span></span>](#cpcondefaultmarshalingforstringsanchor1)  
  
-   [<span data-ttu-id="493ed-108">在平台叫用中使用的字串</span><span class="sxs-lookup"><span data-stu-id="493ed-108">Strings Used in Platform Invoke</span></span>](#cpcondefaultmarshalingforstringsanchor5)  
  
-   [<span data-ttu-id="493ed-109">在結構中使用的字串</span><span class="sxs-lookup"><span data-stu-id="493ed-109">Strings Used in Structures</span></span>](#cpcondefaultmarshalingforstringsanchor2)  
  
-   [<span data-ttu-id="493ed-110">固定長度的字串緩衝區</span><span class="sxs-lookup"><span data-stu-id="493ed-110">Fixed-Length String Buffers</span></span>](#cpcondefaultmarshalingforstringsanchor3)  
  
<a name="cpcondefaultmarshalingforstringsanchor1"></a>

## <a name="strings-used-in-interfaces"></a><span data-ttu-id="493ed-111">在介面中使用的字串</span><span class="sxs-lookup"><span data-stu-id="493ed-111">Strings Used in Interfaces</span></span>  
 <span data-ttu-id="493ed-112">下表顯示當字串資料類型做為方法引數封送處理至 Unmanaged 程式碼時，字串資料類型的封送處理選項。</span><span class="sxs-lookup"><span data-stu-id="493ed-112">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="493ed-113"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性提供幾種 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉值來封送處理字串到 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="493ed-113">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>  
  
|<span data-ttu-id="493ed-114">列舉類型</span><span class="sxs-lookup"><span data-stu-id="493ed-114">Enumeration type</span></span>|<span data-ttu-id="493ed-115">Unmanaged 格式的描述</span><span class="sxs-lookup"><span data-stu-id="493ed-115">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="493ed-116">`UnmanagedType.BStr` (預設值)</span><span class="sxs-lookup"><span data-stu-id="493ed-116">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="493ed-117">具有前置長度和 Unicode 字元的 COM 樣式 `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="493ed-117">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="493ed-118">ANSI 字元之 Null 終端陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="493ed-118">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="493ed-119">Unicode 字元之 Null 終端陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="493ed-119">A pointer to a null-terminated array of Unicode characters.</span></span>|  
  
 <span data-ttu-id="493ed-120">此表格適用於字串。</span><span class="sxs-lookup"><span data-stu-id="493ed-120">This table applies to strings.</span></span> <span data-ttu-id="493ed-121">不過，為了 <xref:System.Text.StringBuilder>，唯一允許的選項為 `UnmanagedType.LPStr` 和 `UnmanagedType.LPWStr`。</span><span class="sxs-lookup"><span data-stu-id="493ed-121">However, for <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>  
  
 <span data-ttu-id="493ed-122">下列範例會顯示在 `IStringWorker` 介面中所宣告的字串。</span><span class="sxs-lookup"><span data-stu-id="493ed-122">The following example shows strings declared in the `IStringWorker` interface.</span></span>  
  
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

<span data-ttu-id="493ed-123">下列範例會顯示在類型程式庫中所述的對應介面。</span><span class="sxs-lookup"><span data-stu-id="493ed-123">The following example shows the corresponding interface described in a type library.</span></span>

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

## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="493ed-124">在平台叫用中使用的字串</span><span class="sxs-lookup"><span data-stu-id="493ed-124">Strings Used in Platform Invoke</span></span>  
 <span data-ttu-id="493ed-125">平台叫用會複製字串引數，從 .NET Framework 格式 (Unicode) 轉換為平台 Unmanaged 格式。</span><span class="sxs-lookup"><span data-stu-id="493ed-125">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="493ed-126">字串為不可變的，在呼叫傳回時並不會從 Unmanaged 記憶體複製回 Managed 記憶體。</span><span class="sxs-lookup"><span data-stu-id="493ed-126">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>  
  
 <span data-ttu-id="493ed-127">下表列出當字串做為平台叫用呼叫的方法引數封送處理時的封送處理選項。</span><span class="sxs-lookup"><span data-stu-id="493ed-127">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="493ed-128"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性提供幾種 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉值來封送處理字串。</span><span class="sxs-lookup"><span data-stu-id="493ed-128">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>  
  
|<span data-ttu-id="493ed-129">列舉類型</span><span class="sxs-lookup"><span data-stu-id="493ed-129">Enumeration type</span></span>|<span data-ttu-id="493ed-130">Unmanaged 格式的描述</span><span class="sxs-lookup"><span data-stu-id="493ed-130">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="493ed-131">具有前置長度和 ANSI 字元的 COM 樣式 `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="493ed-131">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|  
|`UnmanagedType.BStr`|<span data-ttu-id="493ed-132">具有前置長度和 Unicode 字元的 COM 樣式 `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="493ed-132">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="493ed-133">ANSI 字元之 Null 終端陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="493ed-133">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPTStr`|<span data-ttu-id="493ed-134">平台相依字元之 Null 終端陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="493ed-134">A pointer to a null-terminated array of platform-dependent characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="493ed-135">Unicode 字元之 Null 終端陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="493ed-135">A pointer to a null-terminated array of Unicode characters.</span></span>|  
|`UnmanagedType.TBStr`|<span data-ttu-id="493ed-136">具有前置長度和平台相依字元的 COM 樣式 `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="493ed-136">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|  
|`VBByRefStr`|<span data-ttu-id="493ed-137">這個值可讓 Visual Basic .NET 變更 Unmanaged 程式碼中的字串，並且讓結果反映在 Managed 程式碼中。</span><span class="sxs-lookup"><span data-stu-id="493ed-137">A value that enables Visual Basic .NET to change a string in unmanaged code, and have the results reflected in managed code.</span></span> <span data-ttu-id="493ed-138">只有平台叫用支援這個值。</span><span class="sxs-lookup"><span data-stu-id="493ed-138">This value is supported only for platform invoke.</span></span> <span data-ttu-id="493ed-139">這是 `ByVal` 字串在 Visual Basic 中的預設值。</span><span class="sxs-lookup"><span data-stu-id="493ed-139">This is default value in Visual Basic for `ByVal` strings.</span></span>|  
  
 <span data-ttu-id="493ed-140">此表格適用於字串。</span><span class="sxs-lookup"><span data-stu-id="493ed-140">This table applies to strings.</span></span> <span data-ttu-id="493ed-141">不過，為了 <xref:System.Text.StringBuilder>，唯一允許的選項為 `LPStr`、`LPTStr` 和 `LPWStr`。</span><span class="sxs-lookup"><span data-stu-id="493ed-141">However, for <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>  
  
 <span data-ttu-id="493ed-142">下列類型定義會顯示對於平台叫用呼叫要如何正確使用 `MarshalAsAttribute`。</span><span class="sxs-lookup"><span data-stu-id="493ed-142">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>  
  
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
## <a name="strings-used-in-structures"></a><span data-ttu-id="493ed-143">在結構中使用的字串</span><span class="sxs-lookup"><span data-stu-id="493ed-143">Strings Used in Structures</span></span>  
 <span data-ttu-id="493ed-144">字串是結構的有效成員；不過，<xref:System.Text.StringBuilder> 緩衝區在結構中無效。</span><span class="sxs-lookup"><span data-stu-id="493ed-144">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="493ed-145">下表顯示當類型做為欄位封送處理時字串資料類型的封送處理選項。</span><span class="sxs-lookup"><span data-stu-id="493ed-145">The following table shows the marshaling options for the string data type when the type is marshaled as a field.</span></span> <span data-ttu-id="493ed-146"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性提供幾種 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉值來封送處理字串至欄位。</span><span class="sxs-lookup"><span data-stu-id="493ed-146">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>  
  
|<span data-ttu-id="493ed-147">列舉類型</span><span class="sxs-lookup"><span data-stu-id="493ed-147">Enumeration type</span></span>|<span data-ttu-id="493ed-148">Unmanaged 格式的描述</span><span class="sxs-lookup"><span data-stu-id="493ed-148">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`|<span data-ttu-id="493ed-149">具有前置長度和 Unicode 字元的 COM 樣式 `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="493ed-149">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="493ed-150">ANSI 字元之 Null 終端陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="493ed-150">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPTStr`|<span data-ttu-id="493ed-151">平台相依字元之 Null 終端陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="493ed-151">A pointer to a null-terminated array of platform-dependent characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="493ed-152">Unicode 字元之 Null 終端陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="493ed-152">A pointer to a null-terminated array of Unicode characters.</span></span>|  
|`UnmanagedType.ByValTStr`|<span data-ttu-id="493ed-153">一個固定長度的字元陣列；該陣列的類型由包含結構的字元集決定。</span><span class="sxs-lookup"><span data-stu-id="493ed-153">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|  
  
 <span data-ttu-id="493ed-154">`ByValTStr` 類型使用於出現在結構中的內嵌固定長度字元陣列。</span><span class="sxs-lookup"><span data-stu-id="493ed-154">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="493ed-155">其他類型適用於包含在結構內的字串參考，其中包含字串的指標。</span><span class="sxs-lookup"><span data-stu-id="493ed-155">Other types apply to string references contained within structures that contain pointers to strings.</span></span>  
  
 <span data-ttu-id="493ed-156">套用至包含結構之 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性的 `CharSet` 引數會決定在結構中字串的字元格式。</span><span class="sxs-lookup"><span data-stu-id="493ed-156">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="493ed-157">下列範例結構包含字串的參考和內嵌字串，以及 ANSI、Unicode 和平台相依字元。</span><span class="sxs-lookup"><span data-stu-id="493ed-157">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span>  
  
### <a name="type-library-representation"></a><span data-ttu-id="493ed-158">類型程式庫表示法</span><span class="sxs-lookup"><span data-stu-id="493ed-158">Type Library Representation</span></span>  
  
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
  
 <span data-ttu-id="493ed-159">下列程式碼範例示範如何使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性在不同格式中定義相同的結構。</span><span class="sxs-lookup"><span data-stu-id="493ed-159">The following code example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to define the same structure in different formats.</span></span>  
  
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
## <a name="fixed-length-string-buffers"></a><span data-ttu-id="493ed-160">固定長度字串緩衝區</span><span class="sxs-lookup"><span data-stu-id="493ed-160">Fixed-Length String Buffers</span></span>  
 <span data-ttu-id="493ed-161">在某些情況下，固定長度的字元緩衝區必須傳遞至 Unmanaged 程式碼以進行操作。</span><span class="sxs-lookup"><span data-stu-id="493ed-161">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="493ed-162">在此情況下只傳遞字串無法運作，因為被呼叫端不能修改傳遞緩衝區的內容。</span><span class="sxs-lookup"><span data-stu-id="493ed-162">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="493ed-163">即使該字串以傳址方式傳遞，也沒有任何方式來初始化指定大小的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="493ed-163">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>  
  
 <span data-ttu-id="493ed-164">解決方式為傳遞 <xref:System.Text.StringBuilder> 緩衝區做為引數，而非字串。</span><span class="sxs-lookup"><span data-stu-id="493ed-164">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a string.</span></span> <span data-ttu-id="493ed-165">`StringBuilder` 可以為已取值，而且由被呼叫端修改，前提是它不會超過 `StringBuilder` 的容量。</span><span class="sxs-lookup"><span data-stu-id="493ed-165">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="493ed-166">它也可以初始化為固定長度。</span><span class="sxs-lookup"><span data-stu-id="493ed-166">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="493ed-167">例如，如果您初始化 `StringBuilder` 緩衝區為 `N` 的容量，封送處理器會提供 (`N`+1) 個字元大小的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="493ed-167">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="493ed-168">+1 代表 Unmanged 字串具有 null 結束字元，但 `StringBuilder` 沒有。</span><span class="sxs-lookup"><span data-stu-id="493ed-168">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>  
  
 <span data-ttu-id="493ed-169">例如，Microsoft Win32 API `GetWindowText` 函式 (定義於 Windows.h) 是必須傳遞至 Unmanaged 程式碼操作的固定長度字元緩衝區。</span><span class="sxs-lookup"><span data-stu-id="493ed-169">For example, the Microsoft Win32 API `GetWindowText` function (defined in Windows.h) is a fixed-length character buffer that must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="493ed-170">`LpString` 指向大小為 `nMaxCount` 的呼叫端配置緩衝區。</span><span class="sxs-lookup"><span data-stu-id="493ed-170">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="493ed-171">呼叫端必須配置緩衝區，並設定 `nMaxCount` 引數為配置緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="493ed-171">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="493ed-172">下列程式碼顯示在 Windows.h 中所定義的 `GetWindowText` 函式宣告。</span><span class="sxs-lookup"><span data-stu-id="493ed-172">The following code shows the `GetWindowText` function declaration as defined in Windows.h.</span></span>  
  
```  
int GetWindowText(  
HWND hWnd,        // Handle to window or control.  
LPTStr lpString,  // Text buffer.  
int nMaxCount     // Maximum number of characters to copy.  
);  
```  
  
 <span data-ttu-id="493ed-173">`StringBuilder` 可以為已取值，而且由被呼叫端修改，前提是它不會超過 `StringBuilder` 的容量。</span><span class="sxs-lookup"><span data-stu-id="493ed-173">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="493ed-174">下列程式碼範例示範可以 `StringBuilder` 如何初始化為固定長度。</span><span class="sxs-lookup"><span data-stu-id="493ed-174">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="493ed-175">請參閱</span><span class="sxs-lookup"><span data-stu-id="493ed-175">See Also</span></span>  
 [<span data-ttu-id="493ed-176">預設的封送處理行為</span><span class="sxs-lookup"><span data-stu-id="493ed-176">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)  
 [<span data-ttu-id="493ed-177">Blittable 和非 Blittable 類型</span><span class="sxs-lookup"><span data-stu-id="493ed-177">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)  
 <span data-ttu-id="493ed-178">[方向屬性](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="493ed-178">[Directional Attributes](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span></span>  
 [<span data-ttu-id="493ed-179">複製和 Pin</span><span class="sxs-lookup"><span data-stu-id="493ed-179">Copying and Pinning</span></span>](copying-and-pinning.md)
