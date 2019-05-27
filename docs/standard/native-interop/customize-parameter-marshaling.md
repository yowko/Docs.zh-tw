---
title: 自訂參數封送處理 - .NET
description: 了解如何自訂 .NET 將您的參數封送處理為原生表示法的方式。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 877eb00c18c9108fe6bcfb50104ff5ed813e85f3
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65065971"
---
# <a name="customizing-parameter-marshaling"></a><span data-ttu-id="89b1e-103">自訂參數封送處理</span><span class="sxs-lookup"><span data-stu-id="89b1e-103">Customizing parameter marshaling</span></span>

<span data-ttu-id="89b1e-104">當 .NET 執行階段的預設參數封送處理行為不能滿足您要求時，可以使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> 屬性來自訂參數的封送處理方式。</span><span class="sxs-lookup"><span data-stu-id="89b1e-104">When the .NET runtime's default parameter marshaling behavior doesn't do what you want, use can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> attribute to customize how your parameters are marshaled.</span></span>

## <a name="customizing-string-parameters"></a><span data-ttu-id="89b1e-105">自訂字串參數</span><span class="sxs-lookup"><span data-stu-id="89b1e-105">Customizing string parameters</span></span>

<span data-ttu-id="89b1e-106">.NET 有各種不同的格式可用於封送處理字串。</span><span class="sxs-lookup"><span data-stu-id="89b1e-106">.NET has a variety of formats for marshaling strings.</span></span> <span data-ttu-id="89b1e-107">這些方法分為 C 樣式字串和以 Windows 為中心的字串格式的不同區段。</span><span class="sxs-lookup"><span data-stu-id="89b1e-107">These methods are split into distinct sections on C-style strings and Windows-centric string formats.</span></span>

### <a name="c-style-strings"></a><span data-ttu-id="89b1e-108">C 樣式字串</span><span class="sxs-lookup"><span data-stu-id="89b1e-108">C-Style strings</span></span>

<span data-ttu-id="89b1e-109">每種格式都將傳遞以 Null 結尾的字串至機器碼。</span><span class="sxs-lookup"><span data-stu-id="89b1e-109">Each of these formats passes a null-terminated string to native code.</span></span> <span data-ttu-id="89b1e-110">它們因原生字串的編碼方式而不同。</span><span class="sxs-lookup"><span data-stu-id="89b1e-110">They differ by the encoding of the native string.</span></span>

| <span data-ttu-id="89b1e-111">`System.Runtime.InteropServices.UnmanagedType` 值</span><span class="sxs-lookup"><span data-stu-id="89b1e-111">`System.Runtime.InteropServices.UnmanagedType` value</span></span> | <span data-ttu-id="89b1e-112">編碼</span><span class="sxs-lookup"><span data-stu-id="89b1e-112">Encoding</span></span> |
|------------------------------------------------------|----------|
| <span data-ttu-id="89b1e-113">LPStr</span><span class="sxs-lookup"><span data-stu-id="89b1e-113">LPStr</span></span> | <span data-ttu-id="89b1e-114">ANSI</span><span class="sxs-lookup"><span data-stu-id="89b1e-114">ANSI</span></span> |
| <span data-ttu-id="89b1e-115">LPUTF8Str</span><span class="sxs-lookup"><span data-stu-id="89b1e-115">LPUTF8Str</span></span> | <span data-ttu-id="89b1e-116">UTF-8</span><span class="sxs-lookup"><span data-stu-id="89b1e-116">UTF-8</span></span> | 
| <span data-ttu-id="89b1e-117">LPWStr</span><span class="sxs-lookup"><span data-stu-id="89b1e-117">LPWStr</span></span> | <span data-ttu-id="89b1e-118">UTF-16</span><span class="sxs-lookup"><span data-stu-id="89b1e-118">UTF-16</span></span> |
| <span data-ttu-id="89b1e-119">LPTStr</span><span class="sxs-lookup"><span data-stu-id="89b1e-119">LPTStr</span></span> | <span data-ttu-id="89b1e-120">UTF-16</span><span class="sxs-lookup"><span data-stu-id="89b1e-120">UTF-16</span></span> |

<span data-ttu-id="89b1e-121"><xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType> 格式會稍有不同。</span><span class="sxs-lookup"><span data-stu-id="89b1e-121">The <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType> format is slightly different.</span></span> <span data-ttu-id="89b1e-122">與 `LPWStr` 一樣，它將字串封送處理成以 UTF-16 編碼的原生 C 樣式字串。</span><span class="sxs-lookup"><span data-stu-id="89b1e-122">Like `LPWStr`, it marshals the string to a native C-style string encoded in UTF-16.</span></span> <span data-ttu-id="89b1e-123">不過，受控簽章允許您傳參考方式傳入字串，而符合的原生簽章接受以傳值方式傳入的字串。</span><span class="sxs-lookup"><span data-stu-id="89b1e-123">However, the managed signature has you pass in the string by reference and the matching native signature takes the string by value.</span></span> <span data-ttu-id="89b1e-124">此區別可讓您使用原生 API，該 API 接受以傳值方式傳入的字串，並在不必使用 `StringBuilder` 的情況下就地修改它。</span><span class="sxs-lookup"><span data-stu-id="89b1e-124">This distinction allows you to use a native API that takes a string by value and modifies it in-place without having to use a `StringBuilder`.</span></span> <span data-ttu-id="89b1e-125">我們建議您不要以手動方式使用此格式，因為它很容易導致與不相符的原生和受控簽章混淆。</span><span class="sxs-lookup"><span data-stu-id="89b1e-125">We recommend against manually using this format since it's prone to cause confusion with the mismatching native and managed signatures.</span></span>

### <a name="windows-centric-string-formats"></a><span data-ttu-id="89b1e-126">以 Windows 為中心的字串格式</span><span class="sxs-lookup"><span data-stu-id="89b1e-126">Windows-centric string formats</span></span>

<span data-ttu-id="89b1e-127">當與 COM 或 OLE 介面互動時，您可能會發現原生函式接受以 `BSTR` 引數形式表示的字串。</span><span class="sxs-lookup"><span data-stu-id="89b1e-127">When interacting with COM or OLE interfaces, you'll likely find that the native functions take strings as `BSTR` arguments.</span></span> <span data-ttu-id="89b1e-128">您可以使用 <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> 非受控型別將字串封送處理為 `BSTR`。</span><span class="sxs-lookup"><span data-stu-id="89b1e-128">You can use the <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> unmanaged type to marshal a string as a `BSTR`.</span></span>

<span data-ttu-id="89b1e-129">如果您正在與 WinRT API 進行互動，則可以使用 <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> 格式將字串封送處理為 `HSTRING`。</span><span class="sxs-lookup"><span data-stu-id="89b1e-129">If you're interacting with WinRT APIs, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> format to marshal a string as an `HSTRING`.</span></span>

## <a name="customizing-array-parameters"></a><span data-ttu-id="89b1e-130">自訂陣列參數</span><span class="sxs-lookup"><span data-stu-id="89b1e-130">Customizing array parameters</span></span>

<span data-ttu-id="89b1e-131">.NET 也提供您多種方法來封送處理陣列參數。</span><span class="sxs-lookup"><span data-stu-id="89b1e-131">.NET also provides you multiple ways to marshal array parameters.</span></span> <span data-ttu-id="89b1e-132">如果您正在呼叫接受 C 樣式陣列的 API，請使用 <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType> 非受控型別。</span><span class="sxs-lookup"><span data-stu-id="89b1e-132">If you're calling an API that takes a C-style array, use the <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType> unmanaged type.</span></span> <span data-ttu-id="89b1e-133">如果陣列中的值需要自訂封送處理，則您可以使用 `[MarshalAs]` 屬性上的 <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> 欄位來進行此動作。</span><span class="sxs-lookup"><span data-stu-id="89b1e-133">If the values in the array need customized marshaling, you can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> field on the `[MarshalAs]` attribute for that.</span></span>

<span data-ttu-id="89b1e-134">如果您使用 COM API，則可能需要將陣列參數封送處理為 `SAFEARRAY*`。</span><span class="sxs-lookup"><span data-stu-id="89b1e-134">If you're using COM APIs, you'll likely have to marshal your array parameters as `SAFEARRAY*`s.</span></span> <span data-ttu-id="89b1e-135">若要這樣做，您可以使用 <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> 非受控型別。</span><span class="sxs-lookup"><span data-stu-id="89b1e-135">To do so, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> unmanaged type.</span></span> <span data-ttu-id="89b1e-136">在[自訂 `object` 欄位](./customize-struct-marshaling.md#marshaling-systemobjects)表格中可以看到 `SAFEARRAY` 元素的預設型別。</span><span class="sxs-lookup"><span data-stu-id="89b1e-136">The default type of the elements of the `SAFEARRAY` can be seen in the table on [customizing `object` fields](./customize-struct-marshaling.md#marshaling-systemobjects).</span></span> <span data-ttu-id="89b1e-137">您可以使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> 和 <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> 欄位來自訂 `SAFEARRAY` 的確切元素型別。</span><span class="sxs-lookup"><span data-stu-id="89b1e-137">You can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> fields to customize the exact element type of the `SAFEARRAY`.</span></span>

## <a name="customizing-boolean-or-decimal-parameters"></a><span data-ttu-id="89b1e-138">自訂布林值或十進位參數</span><span class="sxs-lookup"><span data-stu-id="89b1e-138">Customizing boolean or decimal parameters</span></span>

<span data-ttu-id="89b1e-139">如需封送處理布林值或十進位參數的資訊，請參閱[自訂結構封送處理](customize-struct-marshaling.md)。</span><span class="sxs-lookup"><span data-stu-id="89b1e-139">For information on marshaling boolean or decimal parameters, see [Customizing structure marshaling](customize-struct-marshaling.md).</span></span>

## <a name="customizing-object-parameters-windows-only"></a><span data-ttu-id="89b1e-140">自訂物件參數 (僅限 Windows)</span><span class="sxs-lookup"><span data-stu-id="89b1e-140">Customizing object parameters (Windows-only)</span></span>

<span data-ttu-id="89b1e-141">在 Windows 上，.NET 執行階段提供不同的方式來將物件參數封送處理為機器碼。</span><span class="sxs-lookup"><span data-stu-id="89b1e-141">On Windows, the .NET runtime provides a number of different ways to marshal object parameters to native code.</span></span>

### <a name="marshaling-as-specific-com-interfaces"></a><span data-ttu-id="89b1e-142">封送處理為特定的 COM 介面</span><span class="sxs-lookup"><span data-stu-id="89b1e-142">Marshaling as specific COM interfaces</span></span>

<span data-ttu-id="89b1e-143">如果您的 API 接受 COM 物件的指標，則可以在 `object` 型別參數上使用下列任一 `UnmanagedType` 格式，以告知 .NET 封送處理為這些特定介面：</span><span class="sxs-lookup"><span data-stu-id="89b1e-143">If your API takes a pointer to a COM object, you can use any of the following `UnmanagedType` formats on an `object`-typed parameter to tell .NET to marshal as these specific interfaces:</span></span>

- `IUnknown`
- `IDispatch`
- `IInspectable`

<span data-ttu-id="89b1e-144">此外，如果您的類型標示為 `[ComVisible(true)]` 或您正在封送處理 `object` 類型，則可以使用 <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> 格式將物件封送處理為類型之 COM 檢視的 COM 可呼叫包裝函式。</span><span class="sxs-lookup"><span data-stu-id="89b1e-144">Additionally, if your type is marked `[ComVisible(true)]` or you're marshaling the `object` type, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> format to marshal your object as a COM callable wrapper for the COM view of your type.</span></span>

### <a name="marshaling-to-a-variant"></a><span data-ttu-id="89b1e-145">封送處理為 `VARIANT`</span><span class="sxs-lookup"><span data-stu-id="89b1e-145">Marshaling to a `VARIANT`</span></span>

<span data-ttu-id="89b1e-146">如果您的原生 API 接受 Win32 `VARIANT`，則可以使用 `object` 參數上的 <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> 格式將物件封送處理為 `VARIANT`。</span><span class="sxs-lookup"><span data-stu-id="89b1e-146">If your native API takes a Win32 `VARIANT`, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> format on your `object` parameter to marshal your objects as `VARIANT`s.</span></span> <span data-ttu-id="89b1e-147">有關 .NET 型別和 `VARIANT` 型別之間的對應，請參閱有關[自訂 `object` 欄位](customize-struct-marshaling.md#marshaling-systemobjects)的文件。</span><span class="sxs-lookup"><span data-stu-id="89b1e-147">See the documentation on [customizing `object` fields](customize-struct-marshaling.md#marshaling-systemobjects) for a mapping between .NET types and `VARIANT` types.</span></span>

### <a name="custom-marshalers"></a><span data-ttu-id="89b1e-148">自訂封送處理器</span><span class="sxs-lookup"><span data-stu-id="89b1e-148">Custom marshalers</span></span>

<span data-ttu-id="89b1e-149">如果要將原生 COM 介面投射到其他受控類型，可以使用 `UnmanagedType.CustomMarshaler` 格式和 <xref:System.Runtime.InteropServices.ICustomMarshaler> 的實作來提供自有自訂封送處理程式碼。</span><span class="sxs-lookup"><span data-stu-id="89b1e-149">If you want to project a native COM interface into a different managed type, you can use the `UnmanagedType.CustomMarshaler` format and an implementation of <xref:System.Runtime.InteropServices.ICustomMarshaler> to provide your own custom marshaling code.</span></span>
