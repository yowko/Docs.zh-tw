---
title: 指定字元集
description: 瞭解如何指定使用窄（ANSI）或寬（Unicode）編碼的字元集。 您也可以指定自動執行時間選取。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- platform invoke, attribute fields
- attribute fields in platform invoke, CharSet
- CharSet field
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
ms.openlocfilehash: 789753742d8714e481f038e323407cbab0499f6c
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309790"
---
# <a name="specify-a-character-set"></a><span data-ttu-id="b80ec-104">指定字元集</span><span class="sxs-lookup"><span data-stu-id="b80ec-104">Specify a character set</span></span>

<span data-ttu-id="b80ec-105"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> 欄位控制字串封送處理，並決定平台叫用如何在 DLL 中尋找函式名稱。</span><span class="sxs-lookup"><span data-stu-id="b80ec-105">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="b80ec-106">這個主題將描述這兩種行為。</span><span class="sxs-lookup"><span data-stu-id="b80ec-106">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="b80ec-107">某些 API 匯出兩個版本的函式，接受字串引數：窄 (ANSI) 和寬 (Unicode)。</span><span class="sxs-lookup"><span data-stu-id="b80ec-107">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="b80ec-108">例如，Win32 API 包括 **MessageBox** 函式的下列進入點名稱：</span><span class="sxs-lookup"><span data-stu-id="b80ec-108">The Windows API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
- <span data-ttu-id="b80ec-109">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="b80ec-109">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="b80ec-110">提供 1 個位元組字元 ANSI 格式化，區別方式是在進入點名稱附加 "A"。</span><span class="sxs-lookup"><span data-stu-id="b80ec-110">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="b80ec-111">**MessageBoxA** 呼叫一律以 ANSI 格式的字串封送處理。</span><span class="sxs-lookup"><span data-stu-id="b80ec-111">Calls to **MessageBoxA** always marshal strings in ANSI format.</span></span>  
  
- <span data-ttu-id="b80ec-112">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="b80ec-112">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="b80ec-113">提供 2 個位元組字元 Unicode 格式化，區別方式是在進入點名稱附加 "W"。</span><span class="sxs-lookup"><span data-stu-id="b80ec-113">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="b80ec-114">**MessageBoxW** 呼叫一律以 Unicode 格式的字串封送處理。</span><span class="sxs-lookup"><span data-stu-id="b80ec-114">Calls to **MessageBoxW** always marshal strings in Unicode format.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="b80ec-115">字串封送處理及名稱比對</span><span class="sxs-lookup"><span data-stu-id="b80ec-115">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="b80ec-116">`CharSet` 欄位可接受下列值：</span><span class="sxs-lookup"><span data-stu-id="b80ec-116">The `CharSet` field accepts the following values:</span></span>  
  
 <span data-ttu-id="b80ec-117"><xref:System.Runtime.InteropServices.CharSet.Ansi> (預設值)</span><span class="sxs-lookup"><span data-stu-id="b80ec-117"><xref:System.Runtime.InteropServices.CharSet.Ansi> (default value)</span></span>  
  
- <span data-ttu-id="b80ec-118">字串封送處理</span><span class="sxs-lookup"><span data-stu-id="b80ec-118">String marshaling</span></span>  
  
     <span data-ttu-id="b80ec-119">平台叫用會將字串從其受管理的格式 (Unicode) 封送處理為 ANSI 格式。</span><span class="sxs-lookup"><span data-stu-id="b80ec-119">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
- <span data-ttu-id="b80ec-120">名稱比對</span><span class="sxs-lookup"><span data-stu-id="b80ec-120">Name matching</span></span>  
  
     <span data-ttu-id="b80ec-121">當 <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> 欄位是 `true` 時，如同 Visual Basic 中的預設值，平台叫用僅會搜尋您指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="b80ec-121">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="b80ec-122">例如，如果您指定 **MessageBox**，平台叫用會搜尋 **MessageBox**，並在找不到正確的拼字時失敗。</span><span class="sxs-lookup"><span data-stu-id="b80ec-122">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="b80ec-123">當 `ExactSpelling` 欄位是 `false` 時，如同在 C++ 和 C# 中的預設值，平台叫用會先搜尋未損壞別名 (**MessageBox**)，然後如果找不到未損壞別名則搜尋損壞名稱 (**MessageBoxA**)。</span><span class="sxs-lookup"><span data-stu-id="b80ec-123">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="b80ec-124">請注意，ANSI 名稱比對行為不同於 Unicode 名稱比對行為。</span><span class="sxs-lookup"><span data-stu-id="b80ec-124">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- <span data-ttu-id="b80ec-125">字串封送處理</span><span class="sxs-lookup"><span data-stu-id="b80ec-125">String marshaling</span></span>  
  
     <span data-ttu-id="b80ec-126">平台叫用會將字串從其受管理的格式 (Unicode) 複製為 Unicode 格式。</span><span class="sxs-lookup"><span data-stu-id="b80ec-126">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
- <span data-ttu-id="b80ec-127">名稱比對</span><span class="sxs-lookup"><span data-stu-id="b80ec-127">Name matching</span></span>  
  
     <span data-ttu-id="b80ec-128">當 `ExactSpelling` 欄位是 `true` 時，如同 Visual Basic 中的預設值，平台叫用僅會搜尋您指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="b80ec-128">When the `ExactSpelling` field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="b80ec-129">例如，如果您指定 **MessageBox**，則平台叫用會搜尋 **MessageBox**，並在找不到正確的拼字時失敗。</span><span class="sxs-lookup"><span data-stu-id="b80ec-129">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="b80ec-130">當 `ExactSpelling` 欄位是 `false` 時，如同在 C++ 和 C# 中的預設值，平台叫用會先搜尋損壞名稱 (**MessageBoxW**)，然後如果找不到損壞名稱則搜尋未損壞別名 (**MessageBox**)。</span><span class="sxs-lookup"><span data-stu-id="b80ec-130">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="b80ec-131">請注意，Unicode 名稱比對行為不同於 ANSI 名稱比對行為。</span><span class="sxs-lookup"><span data-stu-id="b80ec-131">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- <span data-ttu-id="b80ec-132">平台叫用會在執行階段，根據在目標平台，在 ANSI 和 Unicode 格式之間選擇。</span><span class="sxs-lookup"><span data-stu-id="b80ec-132">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specify-a-character-set-in-visual-basic"></a><span data-ttu-id="b80ec-133">在 Visual Basic 中指定字元集</span><span class="sxs-lookup"><span data-stu-id="b80ec-133">Specify a character set in Visual Basic</span></span>

<span data-ttu-id="b80ec-134">您可以藉由在宣告語句中加入 `Ansi` 、或關鍵字，在 Visual Basic 中指定字元集行為 `Unicode` `Auto` 。</span><span class="sxs-lookup"><span data-stu-id="b80ec-134">You can specify character-set behavior in Visual Basic by adding the `Ansi`, `Unicode`, or `Auto` keyword to the declaration statement.</span></span> <span data-ttu-id="b80ec-135">如果您省略 character set 關鍵字， <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> 欄位會預設為 ANSI 字元集。</span><span class="sxs-lookup"><span data-stu-id="b80ec-135">If you omit the character-set keyword, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span>

<span data-ttu-id="b80ec-136">下列範例會宣告 **MessageBox** 函式三次，每次都有不同的字元集行為。</span><span class="sxs-lookup"><span data-stu-id="b80ec-136">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="b80ec-137">第一個語句會省略 character set 關鍵字，因此字元集預設為 ANSI。</span><span class="sxs-lookup"><span data-stu-id="b80ec-137">The first statement omits the character-set keyword, so the character set defaults to ANSI.</span></span> <span data-ttu-id="b80ec-138">第二個和第三個語句使用關鍵字明確指定字元集。</span><span class="sxs-lookup"><span data-stu-id="b80ec-138">The second and third statements explicitly specify a character set with a keyword.</span></span>

```vb
Friend Class NativeMethods
    Friend Declare Function MessageBoxA Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Declare Unicode Function MessageBoxW Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="specify-a-character-set-in-c-and-c"></a><span data-ttu-id="b80ec-139">在 c # 和 c + + 中指定字元集</span><span class="sxs-lookup"><span data-stu-id="b80ec-139">Specify a character set in C# and C++</span></span>

<span data-ttu-id="b80ec-140"><xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> 欄位將基礎字元集識別為 ANSI 或 Unicode。</span><span class="sxs-lookup"><span data-stu-id="b80ec-140">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="b80ec-141">字元集控制應該如何封送處理方法的字串引數。</span><span class="sxs-lookup"><span data-stu-id="b80ec-141">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="b80ec-142">您可以使用下列格式之一來表示字元集：</span><span class="sxs-lookup"><span data-stu-id="b80ec-142">Use one of the following forms to indicate the character set:</span></span>  
  
```csharp
[DllImport("DllName", CharSet = CharSet.Ansi)]
[DllImport("DllName", CharSet = CharSet.Unicode)]
[DllImport("DllName", CharSet = CharSet.Auto)]
```
  
```cpp
[DllImport("DllName", CharSet = CharSet::Ansi)]
[DllImport("DllName", CharSet = CharSet::Unicode)]
[DllImport("DllName", CharSet = CharSet::Auto)]
```
  
 <span data-ttu-id="b80ec-143">下列範例示範 **MessageBox** 函式的三個 Managed 定義，其已屬性化以指定字元集。</span><span class="sxs-lookup"><span data-stu-id="b80ec-143">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="b80ec-144">在第一個定義中，根據其省略，`CharSet` 欄位預設為 ANSI 字元集。</span><span class="sxs-lookup"><span data-stu-id="b80ec-144">In the first definition, by its omission, the `CharSet` field defaults to the ANSI character set.</span></span>  
  
```csharp  
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll")]
    internal static extern int MessageBoxA(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Unicode)]
    internal static extern int MessageBoxW(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Auto)]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```  
  
```cpp
typedef void* HWND;

// Can use MessageBox or MessageBoxA.
[DllImport("user32")]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Can use MessageBox or MessageBoxW.
[DllImport("user32", CharSet = CharSet::Unicode)]
extern "C" int MessageBoxW(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Must use MessageBox.
[DllImport("user32", CharSet = CharSet::Auto)]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a><span data-ttu-id="b80ec-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b80ec-145">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="b80ec-146">在 Managed 程式碼中建立原型</span><span class="sxs-lookup"><span data-stu-id="b80ec-146">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="b80ec-147">平台叫用範例</span><span class="sxs-lookup"><span data-stu-id="b80ec-147">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="b80ec-148">使用平台叫用封送處理資料</span><span class="sxs-lookup"><span data-stu-id="b80ec-148">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
