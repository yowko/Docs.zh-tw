---
title: 使用平台叫用封送處理資料
description: 在 .NET 中使用平台叫用封送處理資料。 查看 Windows Api 和 C 樣式函式中使用的資料類型清單，並尋找其 .NET managed 類型對等專案。
ms.date: 03/20/2019
dev_langs:
- cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
ms.openlocfilehash: 27045790780c1eef9537bdf7e52deb579e2b467c
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904100"
---
# <a name="marshaling-data-with-platform-invoke"></a><span data-ttu-id="c5e8d-104">使用平台叫用封送處理資料</span><span class="sxs-lookup"><span data-stu-id="c5e8d-104">Marshaling Data with Platform Invoke</span></span>

<span data-ttu-id="c5e8d-105">若要呼叫從 Unmanaged 程式庫匯出的函式，.NET Framework 應用程式需要代表此 Unmanaged 函式之 Managed 程式碼中的函式原型。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-105">To call functions exported from an unmanaged library, a .NET Framework application requires a function prototype in managed code that represents the unmanaged function.</span></span> <span data-ttu-id="c5e8d-106">若要建立使平台叫用正確地封送處理資料的原型，您必須執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c5e8d-106">To create a prototype that enables platform invoke to marshal data correctly, you must do the following:</span></span>

- <span data-ttu-id="c5e8d-107">將 <xref:System.Runtime.InteropServices.DllImportAttribute> 屬性套用至使用 Managed 程式碼的靜態函式或方法。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-107">Apply the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to the static function or method in managed code.</span></span>

- <span data-ttu-id="c5e8d-108">將 Unmanaged 資料類型替代為 Managed 資料類型。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-108">Substitute managed data types for unmanaged data types.</span></span>

<span data-ttu-id="c5e8d-109">您可以使用 Unmanaged 函式所提供的文件，以選擇性欄位套用屬性，並且將 Unmanaged 資料類型替代為 Managed 資料類型，來建構對等的 Managed 原型。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-109">You can use the documentation supplied with an unmanaged function to construct an equivalent managed prototype by applying the attribute with its optional fields and substituting managed data types for unmanaged types.</span></span> <span data-ttu-id="c5e8d-110">如需如何套用 <xref:System.Runtime.InteropServices.DllImportAttribute> 的指示，請參閱[使用 Unmanaged DLL 函式](consuming-unmanaged-dll-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-110">For instructions about how to apply the <xref:System.Runtime.InteropServices.DllImportAttribute>, see [Consuming Unmanaged DLL Functions](consuming-unmanaged-dll-functions.md).</span></span>

<span data-ttu-id="c5e8d-111">本節提供範例，示範如何建立 Managed 函式原型，供傳遞引數至函式和接收 Unmanaged 程式庫所匯出函式的傳回值。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-111">This section provides samples that demonstrate how to create managed function prototypes for passing arguments to and receiving return values from functions exported by unmanaged libraries.</span></span> <span data-ttu-id="c5e8d-112">此範例也會示範使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性和 <xref:System.Runtime.InteropServices.Marshal> 類別來明確封送處理資料的時機。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-112">The samples also demonstrate when to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute and the <xref:System.Runtime.InteropServices.Marshal> class to explicitly marshal data.</span></span>

## <a name="platform-invoke-data-types"></a><span data-ttu-id="c5e8d-113">平台叫用資料類型</span><span class="sxs-lookup"><span data-stu-id="c5e8d-113">Platform invoke data types</span></span>

<span data-ttu-id="c5e8d-114">下表列出 Windows API 和 C 樣式函式中所使用的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-114">The following table lists data types used in the Windows APIs and C-style functions.</span></span> <span data-ttu-id="c5e8d-115">許多 Unmanaged 程式庫包含傳遞資料類型做為參數和傳回值的函式。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-115">Many unmanaged libraries contain functions that pass these data types as parameters and return values.</span></span> <span data-ttu-id="c5e8d-116">第三個行列出對應的 .NET Framework 內建實值類型或您在 Managed 程式碼中使用的類別。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-116">The third column lists the corresponding .NET Framework built-in value type or class that you use in managed code.</span></span> <span data-ttu-id="c5e8d-117">在某些情況下，您可將本表格中所列的類型取代為相同大小的類型。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-117">In some cases, you can substitute a type of the same size for the type listed in the table.</span></span>

|<span data-ttu-id="c5e8d-118">Windows API 中的 Unmanaged 類型</span><span class="sxs-lookup"><span data-stu-id="c5e8d-118">Unmanaged type in Windows APIs</span></span>|<span data-ttu-id="c5e8d-119">Unmanaged C 語言類型</span><span class="sxs-lookup"><span data-stu-id="c5e8d-119">Unmanaged C language type</span></span>|<span data-ttu-id="c5e8d-120">Managed 類型</span><span class="sxs-lookup"><span data-stu-id="c5e8d-120">Managed type</span></span>|<span data-ttu-id="c5e8d-121">描述</span><span class="sxs-lookup"><span data-stu-id="c5e8d-121">Description</span></span>|
|--------------------------------|-------------------------------|------------------------|-----------------|
|`VOID`|`void`|<xref:System.Void?displayProperty=nameWithType>|<span data-ttu-id="c5e8d-122">套用至未傳回值的函式。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-122">Applied to a function that does not return a value.</span></span>|
|`HANDLE`|`void *`|<span data-ttu-id="c5e8d-123"><xref:System.IntPtr?displayProperty=nameWithType> 或 <xref:System.UIntPtr?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c5e8d-123"><xref:System.IntPtr?displayProperty=nameWithType> or <xref:System.UIntPtr?displayProperty=nameWithType></span></span>|<span data-ttu-id="c5e8d-124">在 32 位元 Windows 作業系統上為 32 位元，在 64 位元 Windows 作業系統上為 64 位元。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-124">32 bits on 32-bit Windows operating systems, 64 bits on 64-bit Windows operating systems.</span></span>|
|`BYTE`|`unsigned char`|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="c5e8d-125">8 位元</span><span class="sxs-lookup"><span data-stu-id="c5e8d-125">8 bits</span></span>|
|`SHORT`|`short`|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="c5e8d-126">16 位元</span><span class="sxs-lookup"><span data-stu-id="c5e8d-126">16 bits</span></span>|
|`WORD`|`unsigned short`|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="c5e8d-127">16 位元</span><span class="sxs-lookup"><span data-stu-id="c5e8d-127">16 bits</span></span>|
|`INT`|`int`|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="c5e8d-128">32 位元</span><span class="sxs-lookup"><span data-stu-id="c5e8d-128">32 bits</span></span>|
|`UINT`|`unsigned int`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="c5e8d-129">32 位元</span><span class="sxs-lookup"><span data-stu-id="c5e8d-129">32 bits</span></span>|
|`LONG`|`long`|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="c5e8d-130">32 位元</span><span class="sxs-lookup"><span data-stu-id="c5e8d-130">32 bits</span></span>|
|`BOOL`|`long`|<span data-ttu-id="c5e8d-131"><xref:System.Boolean?displayProperty=nameWithType> 或 <xref:System.Int32?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c5e8d-131"><xref:System.Boolean?displayProperty=nameWithType> or <xref:System.Int32?displayProperty=nameWithType></span></span>|<span data-ttu-id="c5e8d-132">32 位元</span><span class="sxs-lookup"><span data-stu-id="c5e8d-132">32 bits</span></span>|
|`DWORD`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="c5e8d-133">32 位元</span><span class="sxs-lookup"><span data-stu-id="c5e8d-133">32 bits</span></span>|
|`ULONG`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="c5e8d-134">32 位元</span><span class="sxs-lookup"><span data-stu-id="c5e8d-134">32 bits</span></span>|
|`CHAR`|`char`|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="c5e8d-135">使用 ANSI 裝飾。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-135">Decorate with ANSI.</span></span>|
|`WCHAR`|`wchar_t`|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="c5e8d-136">使用 Unicode 裝飾。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-136">Decorate with Unicode.</span></span>|
|`LPSTR`|`char *`|<span data-ttu-id="c5e8d-137"><xref:System.String?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c5e8d-137"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="c5e8d-138">使用 ANSI 裝飾。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-138">Decorate with ANSI.</span></span>|
|`LPCSTR`|`const char *`|<span data-ttu-id="c5e8d-139"><xref:System.String?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c5e8d-139"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="c5e8d-140">使用 ANSI 裝飾。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-140">Decorate with ANSI.</span></span>|
|`LPWSTR`|`wchar_t *`|<span data-ttu-id="c5e8d-141"><xref:System.String?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c5e8d-141"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="c5e8d-142">使用 Unicode 裝飾。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-142">Decorate with Unicode.</span></span>|
|`LPCWSTR`|`const wchar_t *`|<span data-ttu-id="c5e8d-143"><xref:System.String?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c5e8d-143"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="c5e8d-144">使用 Unicode 裝飾。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-144">Decorate with Unicode.</span></span>|
|`FLOAT`|`float`|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="c5e8d-145">32 位元</span><span class="sxs-lookup"><span data-stu-id="c5e8d-145">32 bits</span></span>|
|`DOUBLE`|`double`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="c5e8d-146">64 位元</span><span class="sxs-lookup"><span data-stu-id="c5e8d-146">64 bits</span></span>|

<span data-ttu-id="c5e8d-147">如需 Visual Basic、C# 和 C++ 中的對應類型，請參閱 [.NET Framework 類別庫簡介](../../standard/class-library-overview.md#system-namespace)。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-147">For corresponding types in Visual Basic, C#, and C++, see the [Introduction to the .NET Framework Class Library](../../standard/class-library-overview.md#system-namespace).</span></span>

## <a name="pinvokelibdll"></a><span data-ttu-id="c5e8d-148">PinvokeLib.dll</span><span class="sxs-lookup"><span data-stu-id="c5e8d-148">PinvokeLib.dll</span></span>

<span data-ttu-id="c5e8d-149">下列程式碼定義 Pinvoke.dll 所提供的程式庫函式。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-149">The following code defines the library functions provided by Pinvoke.dll.</span></span> <span data-ttu-id="c5e8d-150">本節所描述的許多範例會呼叫此程式庫。</span><span class="sxs-lookup"><span data-stu-id="c5e8d-150">Many samples described in this section call this library.</span></span>

### <a name="example"></a><span data-ttu-id="c5e8d-151">範例</span><span class="sxs-lookup"><span data-stu-id="c5e8d-151">Example</span></span>

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
