---
title: 字串的預設封送處理
ms.date: 03/20/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d39d4dfd5413b95300b70f27437bd27ca2d67a20
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452380"
---
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="5a223-102">字串的預設封送處理</span><span class="sxs-lookup"><span data-stu-id="5a223-102">Default Marshaling for Strings</span></span>

<span data-ttu-id="5a223-103"><xref:System.String?displayProperty=nameWithType> 和 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 類別同時都有類似的封送處理行為。</span><span class="sxs-lookup"><span data-stu-id="5a223-103">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>

<span data-ttu-id="5a223-104">會封送處理字串為 COM 樣式 `BSTR` 類型或 Null 終端字串 (以 null 字元結束的字元陣列)。</span><span class="sxs-lookup"><span data-stu-id="5a223-104">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="5a223-105">字串內的字元可以做為 Unicode (Windows 系統上的預設值) 或 ANSI 封送處理。</span><span class="sxs-lookup"><span data-stu-id="5a223-105">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>

## <a name="strings-used-in-interfaces"></a><span data-ttu-id="5a223-106">在介面中使用的字串</span><span class="sxs-lookup"><span data-stu-id="5a223-106">Strings Used in Interfaces</span></span>

<span data-ttu-id="5a223-107">下表顯示當字串資料類型做為方法引數封送處理至 Unmanaged 程式碼時，字串資料類型的封送處理選項。</span><span class="sxs-lookup"><span data-stu-id="5a223-107">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="5a223-108"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性提供幾種 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉值來封送處理字串到 COM 介面。</span><span class="sxs-lookup"><span data-stu-id="5a223-108">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>

|<span data-ttu-id="5a223-109">列舉類型</span><span class="sxs-lookup"><span data-stu-id="5a223-109">Enumeration type</span></span>|<span data-ttu-id="5a223-110">Unmanaged 格式的描述</span><span class="sxs-lookup"><span data-stu-id="5a223-110">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="5a223-111">`UnmanagedType.BStr` (預設)</span><span class="sxs-lookup"><span data-stu-id="5a223-111">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="5a223-112">具有前置長度和 Unicode 字元的 COM 樣式 `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="5a223-112">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|`UnmanagedType.LPStr`|<span data-ttu-id="5a223-113">ANSI 字元之 Null 終端陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="5a223-113">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="5a223-114">Unicode 字元之 Null 終端陣列的指標</span><span class="sxs-lookup"><span data-stu-id="5a223-114">A pointer to a null-terminated array of Unicode characters.</span></span>|

<span data-ttu-id="5a223-115">此表格適用於 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="5a223-115">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="5a223-116">若是 <xref:System.Text.StringBuilder>，唯一允許的選項為 `UnmanagedType.LPStr` 和 `UnmanagedType.LPWStr`。</span><span class="sxs-lookup"><span data-stu-id="5a223-116">For <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>

<span data-ttu-id="5a223-117">下列範例會顯示在 `IStringWorker` 介面中所宣告的字串。</span><span class="sxs-lookup"><span data-stu-id="5a223-117">The following example shows strings declared in the `IStringWorker` interface.</span></span>

```csharp
public interface IStringWorker
{
    void PassString1(string s);
    void PassString2([MarshalAs(UnmanagedType.BStr)] string s);
    void PassString3([MarshalAs(UnmanagedType.LPStr)] string s);
    void PassString4([MarshalAs(UnmanagedType.LPWStr)] string s);
    void PassStringRef1(ref string s);
    void PassStringRef2([MarshalAs(UnmanagedType.BStr)] ref string s);
    void PassStringRef3([MarshalAs(UnmanagedType.LPStr)] ref string s);
    void PassStringRef4([MarshalAs(UnmanagedType.LPWStr)] ref string s);
}
```

```vb
Public Interface IStringWorker
    Sub PassString1(s As String)
    Sub PassString2(<MarshalAs(UnmanagedType.BStr)> s As String)
    Sub PassString3(<MarshalAs(UnmanagedType.LPStr)> s As String)
    Sub PassString4(<MarshalAs(UnmanagedType.LPWStr)> s As String)
    Sub PassStringRef1(ByRef s As String)
    Sub PassStringRef2(<MarshalAs(UnmanagedType.BStr)> ByRef s As String)
    Sub PassStringRef3(<MarshalAs(UnmanagedType.LPStr)> ByRef s As String)
    Sub PassStringRef4(<MarshalAs(UnmanagedType.LPWStr)> ByRef s As String)
End Interface
```

<span data-ttu-id="5a223-118">下列範例會顯示在類型程式庫中所述的對應介面。</span><span class="sxs-lookup"><span data-stu-id="5a223-118">The following example shows the corresponding interface described in a type library.</span></span>

```cpp
interface IStringWorker : IDispatch
{
    HRESULT PassString1([in] BSTR s);
    HRESULT PassString2([in] BSTR s);
    HRESULT PassString3([in] LPStr s);
    HRESULT PassString4([in] LPWStr s);
    HRESULT PassStringRef1([in, out] BSTR *s);
    HRESULT PassStringRef2([in, out] BSTR *s);
    HRESULT PassStringRef3([in, out] LPStr *s);
    HRESULT PassStringRef4([in, out] LPWStr *s);
};
```

## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="5a223-119">在平台叫用中使用的字串</span><span class="sxs-lookup"><span data-stu-id="5a223-119">Strings Used in Platform Invoke</span></span>

<span data-ttu-id="5a223-120">平台叫用會複製字串引數，從 .NET Framework 格式 (Unicode) 轉換為平台 Unmanaged 格式。</span><span class="sxs-lookup"><span data-stu-id="5a223-120">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="5a223-121">字串為不可變的，在呼叫傳回時並不會從 Unmanaged 記憶體複製回 Managed 記憶體。</span><span class="sxs-lookup"><span data-stu-id="5a223-121">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>

<span data-ttu-id="5a223-122">下表列出當字串做為平台叫用呼叫的方法引數封送處理時的封送處理選項。</span><span class="sxs-lookup"><span data-stu-id="5a223-122">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="5a223-123"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性提供幾種 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉值來封送處理字串。</span><span class="sxs-lookup"><span data-stu-id="5a223-123">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>

|<span data-ttu-id="5a223-124">列舉類型</span><span class="sxs-lookup"><span data-stu-id="5a223-124">Enumeration type</span></span>|<span data-ttu-id="5a223-125">Unmanaged 格式的描述</span><span class="sxs-lookup"><span data-stu-id="5a223-125">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="5a223-126">具有前置長度和 ANSI 字元的 COM 樣式 `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="5a223-126">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|
|`UnmanagedType.BStr`|<span data-ttu-id="5a223-127">具有前置長度和 Unicode 字元的 COM 樣式 `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="5a223-127">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="5a223-128">`UnmanagedType.LPStr` (預設)</span><span class="sxs-lookup"><span data-stu-id="5a223-128">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="5a223-129">ANSI 字元之 Null 終端陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="5a223-129">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="5a223-130">平台相依字元之 Null 終端陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="5a223-130">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="5a223-131">UTF-8 編碼字元之 Null 終端陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="5a223-131">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="5a223-132">Unicode 字元之 Null 終端陣列的指標</span><span class="sxs-lookup"><span data-stu-id="5a223-132">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.TBStr`|<span data-ttu-id="5a223-133">具有前置長度和平台相依字元的 COM 樣式 `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="5a223-133">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|
|`VBByRefStr`|<span data-ttu-id="5a223-134">這個值可讓 Visual Basic .NET 變更非受控程式碼中的字串，且讓結果反映在受控程式碼中。</span><span class="sxs-lookup"><span data-stu-id="5a223-134">A value that enables Visual Basic .NET to change a string in unmanaged code and have the results reflected in managed code.</span></span> <span data-ttu-id="5a223-135">只有平台叫用支援這個值。</span><span class="sxs-lookup"><span data-stu-id="5a223-135">This value is supported only for platform invoke.</span></span> <span data-ttu-id="5a223-136">這是 `ByVal` 字串在 Visual Basic 中的預設值。</span><span class="sxs-lookup"><span data-stu-id="5a223-136">This is the default value in Visual Basic for `ByVal` strings.</span></span>|

<span data-ttu-id="5a223-137">此表格適用於 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="5a223-137">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="5a223-138">若是 <xref:System.Text.StringBuilder>，唯一允許的選項為 `LPStr`、`LPTStr` 和 `LPWStr`。</span><span class="sxs-lookup"><span data-stu-id="5a223-138">For <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>

<span data-ttu-id="5a223-139">下列類型定義會顯示對於平台叫用呼叫要如何正確使用 `MarshalAsAttribute`。</span><span class="sxs-lookup"><span data-stu-id="5a223-139">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>

```csharp
class StringLibAPI
{
    [DllImport("StringLib.dll")]
    public static extern void PassLPStr([MarshalAs(UnmanagedType.LPStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPWStr([MarshalAs(UnmanagedType.LPWStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPTStr([MarshalAs(UnmanagedType.LPTStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPUTF8Str([MarshalAs(UnmanagedType.LPUTF8Str)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassBStr([MarshalAs(UnmanagedType.BStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassAnsiBStr([MarshalAs(UnmanagedType.AnsiBStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassTBStr([MarshalAs(UnmanagedType.TBStr)] string s);
}
```

```vb
Class StringLibAPI
    Public Declare Auto Sub PassLPStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPStr)> s As String)
    Public Declare Auto Sub PassLPWStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPWStr)> s As String)
    Public Declare Auto Sub PassLPTStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPTStr)> s As String)
    Public Declare Auto Sub PassLPUTF8Str Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPUTF8Str)> s As String)
    Public Declare Auto Sub PassBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.BStr)> s As String)
    Public Declare Auto Sub PassAnsiBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.AnsiBStr)> s As String)
    Public Declare Auto Sub PassTBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.TBStr)> s As String)
End Class
```

## <a name="strings-used-in-structures"></a><span data-ttu-id="5a223-140">在結構中使用的字串</span><span class="sxs-lookup"><span data-stu-id="5a223-140">Strings Used in Structures</span></span>

<span data-ttu-id="5a223-141">字串是結構的有效成員；不過，<xref:System.Text.StringBuilder> 緩衝區在結構中無效。</span><span class="sxs-lookup"><span data-stu-id="5a223-141">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="5a223-142">下表顯示當類型作為欄位封送處理時 <xref:System.String> 資料類型的封送處理選項。</span><span class="sxs-lookup"><span data-stu-id="5a223-142">The following table shows the marshaling options for the <xref:System.String> data type when the type is marshaled as a field.</span></span> <span data-ttu-id="5a223-143"><xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性提供幾種 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉值來封送處理字串至欄位。</span><span class="sxs-lookup"><span data-stu-id="5a223-143">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>

|<span data-ttu-id="5a223-144">列舉類型</span><span class="sxs-lookup"><span data-stu-id="5a223-144">Enumeration type</span></span>|<span data-ttu-id="5a223-145">Unmanaged 格式的描述</span><span class="sxs-lookup"><span data-stu-id="5a223-145">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr`|<span data-ttu-id="5a223-146">具有前置長度和 Unicode 字元的 COM 樣式 `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="5a223-146">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="5a223-147">`UnmanagedType.LPStr` (預設)</span><span class="sxs-lookup"><span data-stu-id="5a223-147">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="5a223-148">ANSI 字元之 Null 終端陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="5a223-148">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="5a223-149">平台相依字元之 Null 終端陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="5a223-149">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="5a223-150">UTF-8 編碼字元之 Null 終端陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="5a223-150">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="5a223-151">Unicode 字元之 Null 終端陣列的指標</span><span class="sxs-lookup"><span data-stu-id="5a223-151">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.ByValTStr`|<span data-ttu-id="5a223-152">一個固定長度的字元陣列；該陣列的類型由包含結構的字元集決定。</span><span class="sxs-lookup"><span data-stu-id="5a223-152">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|

<span data-ttu-id="5a223-153">`ByValTStr` 類型使用於出現在結構中的內嵌固定長度字元陣列。</span><span class="sxs-lookup"><span data-stu-id="5a223-153">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="5a223-154">其他類型適用於包含在結構內的字串參考，其中包含字串的指標。</span><span class="sxs-lookup"><span data-stu-id="5a223-154">Other types apply to string references contained within structures that contain pointers to strings.</span></span>

<span data-ttu-id="5a223-155">套用至包含結構之 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 的 `CharSet` 引數會決定在結構中字串的字元格式。</span><span class="sxs-lookup"><span data-stu-id="5a223-155">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="5a223-156">下列範例結構包含字串的參考和內嵌字串，以及 ANSI、Unicode 和平台相依字元。</span><span class="sxs-lookup"><span data-stu-id="5a223-156">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span> <span data-ttu-id="5a223-157">下列 C++ 程式碼顯示這些結構在型別程式庫中的表示：</span><span class="sxs-lookup"><span data-stu-id="5a223-157">The representation of these structures in a type library is shown in the following C++ code:</span></span>

```cpp
struct StringInfoA
{
    char *  f1;
    char    f2[256];
};

struct StringInfoW
{
    WCHAR * f1;
    WCHAR   f2[256];
    BSTR    f3;
};

struct StringInfoT
{
    TCHAR * f1;
    TCHAR   f2[256];
};
```

<span data-ttu-id="5a223-158">下列範例示範如何使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 在不同格式中定義相同的結構。</span><span class="sxs-lookup"><span data-stu-id="5a223-158">The following example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> to define the same structure in different formats.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
struct StringInfoA
{
    [MarshalAs(UnmanagedType.LPStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
}

[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
struct StringInfoW
{
    [MarshalAs(UnmanagedType.LPWStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
    [MarshalAs(UnmanagedType.BStr)] public string f3;
}

[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Auto)]
struct StringInfoT
{
    [MarshalAs(UnmanagedType.LPTStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
}
```

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

## <a name="fixed-length-string-buffers"></a><span data-ttu-id="5a223-159">固定長度字串緩衝區</span><span class="sxs-lookup"><span data-stu-id="5a223-159">Fixed-Length String Buffers</span></span>

<span data-ttu-id="5a223-160">在某些情況下，固定長度的字元緩衝區必須傳遞至 Unmanaged 程式碼以進行操作。</span><span class="sxs-lookup"><span data-stu-id="5a223-160">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="5a223-161">在此情況下只傳遞字串無法運作，因為被呼叫端不能修改傳遞緩衝區的內容。</span><span class="sxs-lookup"><span data-stu-id="5a223-161">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="5a223-162">即使該字串以傳址方式傳遞，也沒有任何方式來初始化指定大小的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5a223-162">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>

<span data-ttu-id="5a223-163">解決方式為傳遞 <xref:System.Text.StringBuilder> 緩衝區作為引數，而非 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="5a223-163">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a <xref:System.String>.</span></span> <span data-ttu-id="5a223-164">`StringBuilder` 可以為已取值，而且由被呼叫端修改，前提是它不會超過 `StringBuilder` 的容量。</span><span class="sxs-lookup"><span data-stu-id="5a223-164">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="5a223-165">它也可以初始化為固定長度。</span><span class="sxs-lookup"><span data-stu-id="5a223-165">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="5a223-166">例如，如果您初始化 `StringBuilder` 緩衝區為 `N` 的容量，封送處理器會提供 (`N`+1) 個字元大小的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5a223-166">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="5a223-167">+1 代表 Unmanged 字串具有 null 結束字元，但 `StringBuilder` 沒有。</span><span class="sxs-lookup"><span data-stu-id="5a223-167">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>

<span data-ttu-id="5a223-168">例如，Windows [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) API 函式 (定義於 *winuser.h*) 要求呼叫端將固定長度字元緩衝區傳遞到函式撰寫視窗文字的位置。</span><span class="sxs-lookup"><span data-stu-id="5a223-168">For example, the Windows [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) API function (defined in *winuser.h*) requires that the caller pass a fixed-length character buffer to which the function writes the window's text.</span></span> <span data-ttu-id="5a223-169">`LpString` 指向大小為 `nMaxCount` 的呼叫端配置緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5a223-169">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="5a223-170">呼叫端必須配置緩衝區，並設定 `nMaxCount` 引數為配置緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="5a223-170">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="5a223-171">下列範例顯示在 *winuser.h* 中所定義的 `GetWindowText` 函式宣告。</span><span class="sxs-lookup"><span data-stu-id="5a223-171">The following example shows the `GetWindowText` function declaration as defined in *winuser.h*.</span></span>

```cpp
int GetWindowText(
    HWND hWnd,        // Handle to window or control.
    LPTStr lpString,  // Text buffer.
    int nMaxCount     // Maximum number of characters to copy.
);
```

<span data-ttu-id="5a223-172">`StringBuilder` 可以為已取值，而且由被呼叫端修改，前提是它不會超過 `StringBuilder` 的容量。</span><span class="sxs-lookup"><span data-stu-id="5a223-172">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="5a223-173">下列程式碼範例示範可以 `StringBuilder` 如何初始化為固定長度。</span><span class="sxs-lookup"><span data-stu-id="5a223-173">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;
using System.Text;

internal static class NativeMethods
{
    [DllImport("User32.dll")]
    internal static extern void GetWindowText(IntPtr hWnd, StringBuilder lpString, int nMaxCount);
}

public class Window
{
    internal IntPtr h;        // Internal handle to Window.
    public String GetText()
    {
        StringBuilder sb = new StringBuilder(256);
        NativeMethods.GetWindowText(h, sb, sb.Capacity + 1);
        return sb.ToString();
    }
}
```

```vb
Imports System.Text

Friend Class NativeMethods
    Friend Declare Auto Sub GetWindowText Lib "User32.dll" _
        (hWnd As IntPtr, lpString As StringBuilder, nMaxCount As Integer)
End Class

Public Class Window
    Friend h As IntPtr ' Friend handle to Window.
    Public Function GetText() As String
        Dim sb As New StringBuilder(256)
        NativeMethods.GetWindowText(h, sb, sb.Capacity + 1)
        Return sb.ToString()
   End Function
End Class
```

## <a name="see-also"></a><span data-ttu-id="5a223-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a223-174">See also</span></span>

- [<span data-ttu-id="5a223-175">預設的封送處理行為</span><span class="sxs-lookup"><span data-stu-id="5a223-175">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="5a223-176">封送處理字串</span><span class="sxs-lookup"><span data-stu-id="5a223-176">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="5a223-177">Blittable 和非 Blittable 類型</span><span class="sxs-lookup"><span data-stu-id="5a223-177">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="5a223-178">[方向屬性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5a223-178">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="5a223-179">複製和 Pin</span><span class="sxs-lookup"><span data-stu-id="5a223-179">Copying and Pinning</span></span>](copying-and-pinning.md)
