---
title: 使用平台叫用封送處理資料
ms.date: 03/20/2019
dev_langs:
- cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cb310dc6d786c3c7711f4c194c6623324c777dd
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412392"
---
# <a name="marshaling-data-with-platform-invoke"></a><span data-ttu-id="407b9-102">使用平台叫用封送處理資料</span><span class="sxs-lookup"><span data-stu-id="407b9-102">Marshaling Data with Platform Invoke</span></span>

<span data-ttu-id="407b9-103">若要呼叫從 Unmanaged 程式庫匯出的函式，.NET Framework 應用程式需要代表此 Unmanaged 函式之 Managed 程式碼中的函式原型。</span><span class="sxs-lookup"><span data-stu-id="407b9-103">To call functions exported from an unmanaged library, a .NET Framework application requires a function prototype in managed code that represents the unmanaged function.</span></span> <span data-ttu-id="407b9-104">若要建立使平台叫用正確地封送處理資料的原型，您必須執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="407b9-104">To create a prototype that enables platform invoke to marshal data correctly, you must do the following:</span></span>

- <span data-ttu-id="407b9-105">將 <xref:System.Runtime.InteropServices.DllImportAttribute> 屬性套用至使用 Managed 程式碼的靜態函式或方法。</span><span class="sxs-lookup"><span data-stu-id="407b9-105">Apply the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to the static function or method in managed code.</span></span>

- <span data-ttu-id="407b9-106">將 Unmanaged 資料類型替代為 Managed 資料類型。</span><span class="sxs-lookup"><span data-stu-id="407b9-106">Substitute managed data types for unmanaged data types.</span></span>

<span data-ttu-id="407b9-107">您可以使用 Unmanaged 函式所提供的文件，以選擇性欄位套用屬性，並且將 Unmanaged 資料類型替代為 Managed 資料類型，來建構對等的 Managed 原型。</span><span class="sxs-lookup"><span data-stu-id="407b9-107">You can use the documentation supplied with an unmanaged function to construct an equivalent managed prototype by applying the attribute with its optional fields and substituting managed data types for unmanaged types.</span></span> <span data-ttu-id="407b9-108">如需如何套用 <xref:System.Runtime.InteropServices.DllImportAttribute> 的指示，請參閱[使用 Unmanaged DLL 函式](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="407b9-108">For instructions about how to apply the <xref:System.Runtime.InteropServices.DllImportAttribute>, see [Consuming Unmanaged DLL Functions](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md).</span></span>

<span data-ttu-id="407b9-109">本節提供範例，示範如何建立 Managed 函式原型，供傳遞引數至函式和接收 Unmanaged 程式庫所匯出函式的傳回值。</span><span class="sxs-lookup"><span data-stu-id="407b9-109">This section provides samples that demonstrate how to create managed function prototypes for passing arguments to and receiving return values from functions exported by unmanaged libraries.</span></span> <span data-ttu-id="407b9-110">此範例也會示範使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性和 <xref:System.Runtime.InteropServices.Marshal> 類別來明確封送處理資料的時機。</span><span class="sxs-lookup"><span data-stu-id="407b9-110">The samples also demonstrate when to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute and the <xref:System.Runtime.InteropServices.Marshal> class to explicitly marshal data.</span></span>

## <a name="platform-invoke-data-types"></a><span data-ttu-id="407b9-111">平台叫用資料類型</span><span class="sxs-lookup"><span data-stu-id="407b9-111">Platform invoke data types</span></span>

<span data-ttu-id="407b9-112">下表列出 Windows API 和 C 樣式函式中所使用的資料類型。</span><span class="sxs-lookup"><span data-stu-id="407b9-112">The following table lists data types used in the Windows APIs and C-style functions.</span></span> <span data-ttu-id="407b9-113">許多 Unmanaged 程式庫包含傳遞資料類型做為參數和傳回值的函式。</span><span class="sxs-lookup"><span data-stu-id="407b9-113">Many unmanaged libraries contain functions that pass these data types as parameters and return values.</span></span> <span data-ttu-id="407b9-114">第三個行列出對應的 .NET Framework 內建實值類型或您在 Managed 程式碼中使用的類別。</span><span class="sxs-lookup"><span data-stu-id="407b9-114">The third column lists the corresponding .NET Framework built-in value type or class that you use in managed code.</span></span> <span data-ttu-id="407b9-115">在某些情況下，您可將本表格中所列的類型取代為相同大小的類型。</span><span class="sxs-lookup"><span data-stu-id="407b9-115">In some cases, you can substitute a type of the same size for the type listed in the table.</span></span>

|<span data-ttu-id="407b9-116">Windows API 中的 Unmanaged 類型</span><span class="sxs-lookup"><span data-stu-id="407b9-116">Unmanaged type in Windows APIs</span></span>|<span data-ttu-id="407b9-117">Unmanaged C 語言類型</span><span class="sxs-lookup"><span data-stu-id="407b9-117">Unmanaged C language type</span></span>|<span data-ttu-id="407b9-118">Managed 類型</span><span class="sxs-lookup"><span data-stu-id="407b9-118">Managed type</span></span>|<span data-ttu-id="407b9-119">說明</span><span class="sxs-lookup"><span data-stu-id="407b9-119">Description</span></span>|
|--------------------------------|-------------------------------|------------------------|-----------------|
|`VOID`|`void`|<xref:System.Void?displayProperty=nameWithType>|<span data-ttu-id="407b9-120">套用至未傳回值的函式。</span><span class="sxs-lookup"><span data-stu-id="407b9-120">Applied to a function that does not return a value.</span></span>|
|`HANDLE`|`void *`|<span data-ttu-id="407b9-121"><xref:System.IntPtr?displayProperty=nameWithType> 或 <xref:System.UIntPtr?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="407b9-121"><xref:System.IntPtr?displayProperty=nameWithType> or <xref:System.UIntPtr?displayProperty=nameWithType></span></span>|<span data-ttu-id="407b9-122">在 32 位元 Windows 作業系統上為 32 位元，在 64 位元 Windows 作業系統上為 64 位元。</span><span class="sxs-lookup"><span data-stu-id="407b9-122">32 bits on 32-bit Windows operating systems, 64 bits on 64-bit Windows operating systems.</span></span>|
|`BYTE`|`unsigned char`|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="407b9-123">8 位元</span><span class="sxs-lookup"><span data-stu-id="407b9-123">8 bits</span></span>|
|`SHORT`|`short`|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="407b9-124">16 位元</span><span class="sxs-lookup"><span data-stu-id="407b9-124">16 bits</span></span>|
|`WORD`|`unsigned short`|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="407b9-125">16 位元</span><span class="sxs-lookup"><span data-stu-id="407b9-125">16 bits</span></span>|
|`INT`|`int`|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="407b9-126">32 位元</span><span class="sxs-lookup"><span data-stu-id="407b9-126">32 bits</span></span>|
|`UINT`|`unsigned int`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="407b9-127">32 位元</span><span class="sxs-lookup"><span data-stu-id="407b9-127">32 bits</span></span>|
|`LONG`|`long`|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="407b9-128">32 位元</span><span class="sxs-lookup"><span data-stu-id="407b9-128">32 bits</span></span>|
|`BOOL`|`long`|<span data-ttu-id="407b9-129"><xref:System.Boolean?displayProperty=nameWithType> 或 <xref:System.Int32?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="407b9-129"><xref:System.Boolean?displayProperty=nameWithType> or <xref:System.Int32?displayProperty=nameWithType></span></span>|<span data-ttu-id="407b9-130">32 位元</span><span class="sxs-lookup"><span data-stu-id="407b9-130">32 bits</span></span>|
|`DWORD`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="407b9-131">32 位元</span><span class="sxs-lookup"><span data-stu-id="407b9-131">32 bits</span></span>|
|`ULONG`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="407b9-132">32 位元</span><span class="sxs-lookup"><span data-stu-id="407b9-132">32 bits</span></span>|
|`CHAR`|`char`|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="407b9-133">使用 ANSI 裝飾。</span><span class="sxs-lookup"><span data-stu-id="407b9-133">Decorate with ANSI.</span></span>|
|`WCHAR`|`wchar_t`|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="407b9-134">使用 Unicode 裝飾。</span><span class="sxs-lookup"><span data-stu-id="407b9-134">Decorate with Unicode.</span></span>|
|`LPSTR`|`char *`|<span data-ttu-id="407b9-135"><xref:System.String?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="407b9-135"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="407b9-136">使用 ANSI 裝飾。</span><span class="sxs-lookup"><span data-stu-id="407b9-136">Decorate with ANSI.</span></span>|
|`LPCSTR`|`const char *`|<span data-ttu-id="407b9-137"><xref:System.String?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="407b9-137"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="407b9-138">使用 ANSI 裝飾。</span><span class="sxs-lookup"><span data-stu-id="407b9-138">Decorate with ANSI.</span></span>|
|`LPWSTR`|`wchar_t *`|<span data-ttu-id="407b9-139"><xref:System.String?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="407b9-139"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="407b9-140">使用 Unicode 裝飾。</span><span class="sxs-lookup"><span data-stu-id="407b9-140">Decorate with Unicode.</span></span>|
|`LPCWSTR`|`const wchar_t *`|<span data-ttu-id="407b9-141"><xref:System.String?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="407b9-141"><xref:System.String?displayProperty=nameWithType> or <xref:System.Text.StringBuilder?displayProperty=nameWithType></span></span>|<span data-ttu-id="407b9-142">使用 Unicode 裝飾。</span><span class="sxs-lookup"><span data-stu-id="407b9-142">Decorate with Unicode.</span></span>|
|`FLOAT`|`float`|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="407b9-143">32 位元</span><span class="sxs-lookup"><span data-stu-id="407b9-143">32 bits</span></span>|
|`DOUBLE`|`double`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="407b9-144">64 位元</span><span class="sxs-lookup"><span data-stu-id="407b9-144">64 bits</span></span>|

<span data-ttu-id="407b9-145">如需 Visual Basic、C# 和 C++ 中的對應類型，請參閱 [.NET Framework 類別庫簡介](../../standard/class-library-overview.md#system-namespace)。</span><span class="sxs-lookup"><span data-stu-id="407b9-145">For corresponding types in Visual Basic, C#, and C++, see the [Introduction to the .NET Framework Class Library](../../standard/class-library-overview.md#system-namespace).</span></span>

## <a name="pinvokelibdll"></a><span data-ttu-id="407b9-146">PinvokeLib.dll</span><span class="sxs-lookup"><span data-stu-id="407b9-146">PinvokeLib.dll</span></span>

<span data-ttu-id="407b9-147">下列程式碼定義 Pinvoke.dll 所提供的程式庫函式。</span><span class="sxs-lookup"><span data-stu-id="407b9-147">The following code defines the library functions provided by Pinvoke.dll.</span></span> <span data-ttu-id="407b9-148">本節所描述的許多範例會呼叫此程式庫。</span><span class="sxs-lookup"><span data-stu-id="407b9-148">Many samples described in this section call this library.</span></span>

### <a name="example"></a><span data-ttu-id="407b9-149">範例</span><span class="sxs-lookup"><span data-stu-id="407b9-149">Example</span></span>

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
