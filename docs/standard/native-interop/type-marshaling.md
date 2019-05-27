---
title: 類型封送處理 - .NET
description: 了解 .NET 如何將您的類型封送處理至原生表示法。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: cb18a7607a3d99907401543b4d37995a956a3920
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65065961"
---
# <a name="type-marshaling"></a><span data-ttu-id="3db64-103">類型封送處理</span><span class="sxs-lookup"><span data-stu-id="3db64-103">Type marshaling</span></span>

<span data-ttu-id="3db64-104">當類型需要跨越受控程式碼和機器碼之間的界限時，**封送處理**便是轉換類型的程序。</span><span class="sxs-lookup"><span data-stu-id="3db64-104">**Marshaling** is the process of transforming types when they need to cross between managed and native code.</span></span>

<span data-ttu-id="3db64-105">之所以需要進行封送處理，是因受控程式碼和非受控程式碼中的類型並不相同。</span><span class="sxs-lookup"><span data-stu-id="3db64-105">Marshaling is needed because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="3db64-106">例如，在 Managed 程式碼中會有 `String`，而在 Unmanaged 程式碼中，字串可以是 Unicode (「寬」)、非 Unicode、以 null 終止的及 ASCII 等等。根據預設，P/Invoke 子系統會嘗試根據預設行為 (已於本文中描述) 執行正確動作。</span><span class="sxs-lookup"><span data-stu-id="3db64-106">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem tries to do the right thing based on the default behavior, described on this article.</span></span> <span data-ttu-id="3db64-107">不過，在您需要進行額外控制的情況下，您可以運用 [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) 屬性來指定非受控端的預期類型。</span><span class="sxs-lookup"><span data-stu-id="3db64-107">However, for those situations where you need extra control, you can employ the [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="3db64-108">比方說，如果您想要用以 null 終止的 ANSI 字串形式來傳送字串，您可以下列方式執行它︰</span><span class="sxs-lookup"><span data-stu-id="3db64-108">For instance, if you want the string to be sent as a null-terminated ANSI string, you could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshaling-common-types"></a><span data-ttu-id="3db64-109">對常見類型進行封送處理的預設規則</span><span class="sxs-lookup"><span data-stu-id="3db64-109">Default rules for marshaling common types</span></span>

<span data-ttu-id="3db64-110">一般而言，執行階段會在封送處理期間嘗試執行「正確動作」，以將您所需進行的工作減至最少。</span><span class="sxs-lookup"><span data-stu-id="3db64-110">Generally, the runtime tries to do the "right thing" when marshaling to require the least amount of work from you.</span></span> <span data-ttu-id="3db64-111">下表描述每個類型在用於參數或欄位時，對其進行封送處理的預設值。</span><span class="sxs-lookup"><span data-stu-id="3db64-111">The following tables describe how each type is marshaled by default when used in a parameter or field.</span></span> <span data-ttu-id="3db64-112">C99/C++11 固定寬度整數和字元類型是用來確保下表針對所有平台都是正確的。</span><span class="sxs-lookup"><span data-stu-id="3db64-112">The C99/C++11 fixed-width integer and character types are used to ensure that the following table is correct for all platforms.</span></span> <span data-ttu-id="3db64-113">您可以使用和這些類型具有相同對齊和大小需求的任何原生類型。</span><span class="sxs-lookup"><span data-stu-id="3db64-113">You can use any native type that has the same alignment and size requirements as these types.</span></span>

<span data-ttu-id="3db64-114">第一個表格會描述 P/Invoke 和欄位封送處理的封送處理皆相同之各種不同類型的對應。</span><span class="sxs-lookup"><span data-stu-id="3db64-114">This first table describes the mappings for various types for whom the marshaling is the same for both P/Invoke and field marshaling.</span></span>

| <span data-ttu-id="3db64-115">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="3db64-115">.NET Type</span></span> | <span data-ttu-id="3db64-116">原生類型</span><span class="sxs-lookup"><span data-stu-id="3db64-116">Native Type</span></span>  |
|-----------|-------------------------|
| `byte`    | `uint8_t`               |
| `sbyte`   | `int8_t`                |
| `short`   | `int16_t`               |
| `ushort`  | `uint16_t`              |
| `int`     | `int32_t`               |
| `uint`    | `uint32_t`              |
| `long`    | `int64_t`               |
| `ulong`   | `uint64_t`              |
| `char`    | <span data-ttu-id="3db64-117">`char` 或 `char16_t`，取決於 P/Invoke 或結構的 `CharSet`。</span><span class="sxs-lookup"><span data-stu-id="3db64-117">Either `char` or `char16_t` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="3db64-118">請參閱[字元集文件](charset.md)。</span><span class="sxs-lookup"><span data-stu-id="3db64-118">See the [charset documentation](charset.md).</span></span> |
| `string`  | <span data-ttu-id="3db64-119">`char*` 或 `char16_t*`，取決於 P/Invoke 或結構的 `CharSet`。</span><span class="sxs-lookup"><span data-stu-id="3db64-119">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="3db64-120">請參閱[字元集文件](charset.md)。</span><span class="sxs-lookup"><span data-stu-id="3db64-120">See the [charset documentation](charset.md).</span></span> |
| `System.IntPtr` | `intptr_t`        |
| `System.UIntPtr` | `uintptr_t`      |
| <span data-ttu-id="3db64-121">.NET 指標類型 (例如</span><span class="sxs-lookup"><span data-stu-id="3db64-121">.NET Pointer types (ex.</span></span> <span data-ttu-id="3db64-122">`void*`)</span><span class="sxs-lookup"><span data-stu-id="3db64-122">`void*`)</span></span>  | `void*` |
| <span data-ttu-id="3db64-123">衍生自 `System.Runtime.InteropServices.SafeHandle` 的類型</span><span class="sxs-lookup"><span data-stu-id="3db64-123">Type derived from `System.Runtime.InteropServices.SafeHandle`</span></span> | `void*` |
| <span data-ttu-id="3db64-124">衍生自 `System.Runtime.InteropServices.CriticalHandle` 的類型</span><span class="sxs-lookup"><span data-stu-id="3db64-124">Type derived from `System.Runtime.InteropServices.CriticalHandle`</span></span> | `void*`          |
| `bool`    | <span data-ttu-id="3db64-125">Win32 `BOOL` 類型</span><span class="sxs-lookup"><span data-stu-id="3db64-125">Win32 `BOOL` type</span></span>       |
| `decimal` | <span data-ttu-id="3db64-126">COM `DECIMAL` 結構</span><span class="sxs-lookup"><span data-stu-id="3db64-126">COM `DECIMAL` struct</span></span> |
| <span data-ttu-id="3db64-127">.NET 委派</span><span class="sxs-lookup"><span data-stu-id="3db64-127">.NET Delegate</span></span> | <span data-ttu-id="3db64-128">原生函式指標</span><span class="sxs-lookup"><span data-stu-id="3db64-128">Native function pointer</span></span> |
| `System.DateTime` | <span data-ttu-id="3db64-129">Win32 `DATE` 類型</span><span class="sxs-lookup"><span data-stu-id="3db64-129">Win32 `DATE` type</span></span> |
| `System.Guid` | <span data-ttu-id="3db64-130">Win32 `GUID` 類型</span><span class="sxs-lookup"><span data-stu-id="3db64-130">Win32 `GUID` type</span></span> |

<span data-ttu-id="3db64-131">如果您是以參數或結構的形式進行封送處理，則有幾個封送處理類別具有不同的預設值。</span><span class="sxs-lookup"><span data-stu-id="3db64-131">A few categories of marshaling have different defaults if you're marshaling as a parameter or structure.</span></span>

| <span data-ttu-id="3db64-132">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="3db64-132">.NET Type</span></span> | <span data-ttu-id="3db64-133">原生類型 (參數)</span><span class="sxs-lookup"><span data-stu-id="3db64-133">Native Type (Parameter)</span></span> | <span data-ttu-id="3db64-134">原生類型 (欄位)</span><span class="sxs-lookup"><span data-stu-id="3db64-134">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| <span data-ttu-id="3db64-135">.NET 陣列</span><span class="sxs-lookup"><span data-stu-id="3db64-135">.NET array</span></span> | <span data-ttu-id="3db64-136">針對陣列元素原生表示法之陣列開頭的指標。</span><span class="sxs-lookup"><span data-stu-id="3db64-136">A pointer to the start of an array of native representations of the array elements.</span></span> | <span data-ttu-id="3db64-137">需要有 `[MarshalAs]` 屬性，否則不允許</span><span class="sxs-lookup"><span data-stu-id="3db64-137">Not allowed without a `[MarshalAs]` attribute</span></span>|
| <span data-ttu-id="3db64-138">具有 `Sequential` 或 `Explicit`之 `LayoutKind` 的類別</span><span class="sxs-lookup"><span data-stu-id="3db64-138">A class with a `LayoutKind` of `Sequential` or `Explicit`</span></span> | <span data-ttu-id="3db64-139">針對類別之原生表示法的指標</span><span class="sxs-lookup"><span data-stu-id="3db64-139">A pointer to the native representation of the class</span></span> | <span data-ttu-id="3db64-140">類別的原生表示法</span><span class="sxs-lookup"><span data-stu-id="3db64-140">The native representation of the class</span></span> |

<span data-ttu-id="3db64-141">下表包含僅限 Windows 的預設封送處理規則。</span><span class="sxs-lookup"><span data-stu-id="3db64-141">The following table includes the default marshaling rules that are Windows-only.</span></span> <span data-ttu-id="3db64-142">在非 Windows 平台上，您無法對這些類型進行封送處理。</span><span class="sxs-lookup"><span data-stu-id="3db64-142">On non-Windows platforms, you cannot marshal these types.</span></span>

| <span data-ttu-id="3db64-143">.NET 類型</span><span class="sxs-lookup"><span data-stu-id="3db64-143">.NET Type</span></span> | <span data-ttu-id="3db64-144">原生類型 (參數)</span><span class="sxs-lookup"><span data-stu-id="3db64-144">Native Type (Parameter)</span></span> | <span data-ttu-id="3db64-145">原生類型 (欄位)</span><span class="sxs-lookup"><span data-stu-id="3db64-145">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | <span data-ttu-id="3db64-146">COM 介面</span><span class="sxs-lookup"><span data-stu-id="3db64-146">COM interface</span></span> | <span data-ttu-id="3db64-147">需要有 `[MarshalAs]` 屬性，否則不允許</span><span class="sxs-lookup"><span data-stu-id="3db64-147">Not allowed without a `[MarshalAs]` attribute</span></span> |
| `System.ArgIterator` | `va_list` | <span data-ttu-id="3db64-148">不允許</span><span class="sxs-lookup"><span data-stu-id="3db64-148">Not allowed</span></span> |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | <span data-ttu-id="3db64-149">不允許</span><span class="sxs-lookup"><span data-stu-id="3db64-149">Not allowed</span></span> |
| `System.Collections.IEnumerable` | `IDispatch*` | <span data-ttu-id="3db64-150">不允許</span><span class="sxs-lookup"><span data-stu-id="3db64-150">Not allowed</span></span> |
| `System.DateTimeOffset` | <span data-ttu-id="3db64-151">`int64_t` 代表從 1601 年 1 月 1 日午夜起的刻度數目</span><span class="sxs-lookup"><span data-stu-id="3db64-151">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> || <span data-ttu-id="3db64-152">`int64_t` 代表從 1601 年 1 月 1 日午夜起的刻度數目</span><span class="sxs-lookup"><span data-stu-id="3db64-152">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> |

<span data-ttu-id="3db64-153">某些類型只能以參數 (而非欄位) 的形式進行封送處理。</span><span class="sxs-lookup"><span data-stu-id="3db64-153">Some types can only be marshaled as parameters and not as fields.</span></span> <span data-ttu-id="3db64-154">這些類型已列於下表中：</span><span class="sxs-lookup"><span data-stu-id="3db64-154">These types are listed in the following table:</span></span>

| <span data-ttu-id="3db64-155">.NET 類型</span><span class="sxs-lookup"><span data-stu-id="3db64-155">.NET Type</span></span> | <span data-ttu-id="3db64-156">原生類型 (僅限參數)</span><span class="sxs-lookup"><span data-stu-id="3db64-156">Native Type (Parameter Only)</span></span> |
|-----------|------------------------------|
| `System.Text.StringBuilder` | <span data-ttu-id="3db64-157">`char*` 或 `char16_t*`，取決於 P/Invoke 的 `CharSet`。</span><span class="sxs-lookup"><span data-stu-id="3db64-157">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke.</span></span>  <span data-ttu-id="3db64-158">請參閱[字元集文件](charset.md)。</span><span class="sxs-lookup"><span data-stu-id="3db64-158">See the [charset documentation](charset.md).</span></span> |
| `System.ArgIterator` | <span data-ttu-id="3db64-159">`va_list` (僅限 Windows x86/x64/arm64)</span><span class="sxs-lookup"><span data-stu-id="3db64-159">`va_list` (on Windows x86/x64/arm64 only)</span></span> |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

<span data-ttu-id="3db64-160">如果這些預設值無法達成您的目的，您可以自訂對參數進行封送處理的方式。</span><span class="sxs-lookup"><span data-stu-id="3db64-160">If these defaults don't do exactly what you want, you can customize how parameters are marshaled.</span></span> <span data-ttu-id="3db64-161">[參數封送處理](customize-parameter-marshaling.md)一文會引導您了解如何自訂對不同參數類型進行封送處理的方式。</span><span class="sxs-lookup"><span data-stu-id="3db64-161">The [parameter marshaling](customize-parameter-marshaling.md) article walks you through how to customize how different parameter types are marshaled.</span></span>

## <a name="marshaling-classes-and-structs"></a><span data-ttu-id="3db64-162">封送處理類別和結構</span><span class="sxs-lookup"><span data-stu-id="3db64-162">Marshaling classes and structs</span></span>

<span data-ttu-id="3db64-163">封送處理類型的另一個層面是如何將結構傳遞給非受控方法。</span><span class="sxs-lookup"><span data-stu-id="3db64-163">Another aspect of type marshaling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="3db64-164">比方說，有些 Unmanaged 方法需要結構以作為參數。</span><span class="sxs-lookup"><span data-stu-id="3db64-164">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="3db64-165">在這些情況下，您需要在世界的受控部分建立對應的結構或類別，以將它作為參數。</span><span class="sxs-lookup"><span data-stu-id="3db64-165">In these cases, you need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="3db64-166">不過，只定義類別是不夠的，您也必須指示封送處理器如何將類別中的欄位對應至非受控結構。</span><span class="sxs-lookup"><span data-stu-id="3db64-166">However, just defining the class isn't enough, you also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="3db64-167">在這裡，`StructLayout` 屬性將會變得很有用。</span><span class="sxs-lookup"><span data-stu-id="3db64-167">Here the `StructLayout` attribute becomes useful.</span></span>

```csharp
[DllImport("kernel32.dll")]
static extern void GetSystemTime(SystemTime systemTime);

[StructLayout(LayoutKind.Sequential)]
class SystemTime {
    public ushort Year;
    public ushort Month;
    public ushort DayOfWeek;
    public ushort Day;
    public ushort Hour;
    public ushort Minute;
    public ushort Second;
    public ushort Milsecond;
}

public static void Main(string[] args) {
    SystemTime st = new SystemTime();
    GetSystemTime(st);
    Console.WriteLine(st.Year);
}
```

<span data-ttu-id="3db64-168">上述程式碼示範針對 `GetSystemTime()` 函式進行呼叫的簡單範例。</span><span class="sxs-lookup"><span data-stu-id="3db64-168">The previous code shows a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="3db64-169">請注意第 4 行。</span><span class="sxs-lookup"><span data-stu-id="3db64-169">The interesting bit is on line 4.</span></span> <span data-ttu-id="3db64-170">此屬性會指定類別的欄位應該循序對應至 Unmanaged 這一端上的結構。</span><span class="sxs-lookup"><span data-stu-id="3db64-170">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="3db64-171">這表示欄位的命名並不重要，只有其順序才重要，因為它需要對應至非受控結構，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="3db64-171">This means that the naming of the fields isn't important, only their order is important, as it needs to correspond to the unmanaged struct, shown in the following example:</span></span>

```c
typedef struct _SYSTEMTIME {
  WORD wYear;
  WORD wMonth;
  WORD wDayOfWeek;
  WORD wDay;
  WORD wHour;
  WORD wMinute;
  WORD wSecond;
  WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME*;
```

<span data-ttu-id="3db64-172">有時候，針對結構進行預設的封送處理並無法帶來您所需結果。</span><span class="sxs-lookup"><span data-stu-id="3db64-172">Sometimes the default marshaling for your structure doesn't do what you need.</span></span> <span data-ttu-id="3db64-173">[自訂結構封送處理](./customize-struct-marshaling.md)一文會指導您如何自訂對結構進行封送處理的方式。</span><span class="sxs-lookup"><span data-stu-id="3db64-173">The [Customizing structure marshaling](./customize-struct-marshaling.md) article teaches you how to customize how your structure is marshaled.</span></span>
