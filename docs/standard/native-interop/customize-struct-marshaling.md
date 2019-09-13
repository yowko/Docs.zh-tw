---
title: 自訂結構封送處理 - .NET
description: 了解如何自訂 .NET 如何以原生表示法封送處理您的結構。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: b174a817e82f9a9f123c79581656cc8e7179b435
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929043"
---
# <a name="customizing-structure-marshaling"></a>自訂結構封送處理

有時候，結構的預設封送處理規則並不是完全如您所需要。 .NET 執行階段提供一些延伸點，讓您自訂您結構的配置以及封送處理欄位的方式。

## <a name="customizing-structure-layout"></a>自訂結構配置

.NET 提供 <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> 屬性與 <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> 列舉，讓您可以自訂欄位在記憶體中的放置方式。 下列指導方針將可協助您避免常見問題。

**✔️ 考慮**使用 `LayoutKind.Sequential` (若可行)。

**✔️ 務必**只在封送處理中使用 `LayoutKind.Explicit` (當您的原生結構也有明確的配置 (例如聯集) 時)。

**❌ 避免**在於非 Windows 平台上封送處理結構時使用 `LayoutKind.Explicit`。 .NET Core 執行階段不支援以傳值方式傳遞明確結構至 Intel 或 AMD 64 位元非 Windows 系統上的原生函式。 不過，執行階段支援在所有平台上以傳參考方式傳遞明確結構。

## <a name="customizing-boolean-field-marshaling"></a>自訂布林值欄位封送處理

機器碼有許多不同的布林值表示法。 在 Windows 上，有三種方式可以代表布林值。 執行階段不知道您結構的原生定義，因此它可以做到的最佳程度是猜測如何封送處理您的布林值。 .NET 執行階段提供一種方式來指出如何封送處理您的布林值欄位。 下列範例示範如何將 .NET `bool` 封送處理為不同的原生布林值類型。

布林值預設為封送處理為原生 4 位元組 Win32 [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) 值，如下列範例所示：

```csharp
public struct WinBool
{
    public bool b;
}
```

```cpp
struct WinBool
{
    public BOOL b;
};
```

若要更為明確，您可以使用 <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> 值來取得與上面相同的行為：

```csharp
public struct WinBool
{
    [MarshalAs(UnmanagedType.Bool)]
    public bool b;
}
```

```cpp
struct WinBool
{
    public BOOL b;
};
```

使用下面的 `UnmanagedType.U1` 或 `UnmanagedType.I1` 值，您可以告訴執行階段將 `b` 欄位封送處理為 1 位元的原生 `bool` 類型。

```csharp
public struct CBool
{
    [MarshalAs(UnmanagedType.U1)]
    public bool b;
}
```

```cpp
struct CBool
{
    public bool b;
};
```

在 Windows 上，您可以使用 <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> 值來告訴執行階段將您的布林值封送處理為 2 位元的 `VARIANT_BOOL` 值：

```csharp
public struct VariantBool
{
    [MarshalAs(UnmanagedType.VariantBool)]
    public bool b;
}
```

```cpp
struct VariantBool
{
    public VARIANT_BOOL b;
};
```

> [!NOTE]
> `VARIANT_BOOL` 與 `VARIANT_TRUE = -1` 和 `VARIANT_FALSE = 0` 中的大部分布林值類型不同。 此外，不等於 `VARIANT_TRUE` 的所有值都會被視為 False。

## <a name="customizing-array-field-marshaling"></a>自訂陣列欄位封送處理

.NET 也包含一些可用來自訂陣列封送處理的方式。

根據預設，.NET 會將陣列封送處理為指向連續元素清單的指標：

```csharp
public struct DefaultArray
{
    public int[] values;
}
```

```cpp
struct DefaultArray
{
    int* values;
};
```

若您與 COM API 進行介面連接，您可能必須將陣列封送處理為 `SAFEARRAY*` 物件。 您可以使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> 與 <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> 值告訴執行階段將陣列封送處理為 `SAFEARRAY*`：

```csharp
public struct SafeArrayExample
{
    [MarshalAs(UnmanagedType.SafeArray)]
    public int[] values;
}
```

```cpp
struct SafeArrayExample
{
    SAFEARRAY* values;
};
```

若需要自訂 `SAFEARRAY` 中的元素類型，您可以使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> 與 <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> 欄位來自訂精確的 `SAFEARRAY` 元素類型。

若需要就地封送處理陣列，您可以使用 <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> 值告訴封送處理器就地封送處理陣列。 當您此用此封送處理時，您也必須提供值給 <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> 欄位作為陣列中的項目數目，以便執行階段可以正確地為結構配置空間。

```csharp
public struct InPlaceArray
{
    [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
    public int[] values;
}
```

```cpp
struct InPlaceArray
{
    int values[4];
};
```

> [!NOTE]
> .NET 不支援將可變長度陣列欄位封送處理為 C99 彈性陣列成員。

## <a name="customizing-string-field-marshaling"></a>自訂字串欄位封送處理

.NET 也為封送處理字串欄位提供各種自訂。

根據預設，.NET 會將字串封送處理為指向結尾為 Null 之字串的指標。 編碼取決於 <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> 中 <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> 欄位的值。 若未指定任何屬性，編碼會預設為 ANSI 編碼。

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
public struct DefaultString
{
    public string str;
}
```

```cpp
struct DefaultString
{
    char* str;
};
```

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct DefaultString
{
    public string str;
}
```

```cpp
struct DefaultString
{
    char16_t* str; // Could also be wchar_t* on Windows.
};
```

若需要為不同的藍未使用不同的編碼或只是想要在您的結構定義中更為明確，您可以使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> 屬性上的 <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> 或 <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> 值。

```csharp
public struct AnsiString
{
    [MarshalAs(UnmanagedType.LPStr)]
    public string str;
}
```

```cpp
struct AnsiString
{
    char* str;
};
```

```csharp
public struct UnicodeString
{
    [MarshalAs(UnmanagedType.LPWStr)]
    public string str;
}
```

```cpp
struct UnicodeString
{
    char16_t* str; // Could also be wchar_t* on Windows.
};
```

若想要使用 UTF-8 編碼來封送處理您的字串，您可以使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 中的 <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> 值。

```csharp
public struct UTF8String
{
    [MarshalAs(UnmanagedType.LPUTF8Str)]
    public string str;
}
```

```cpp
struct UTF8String
{
    char* str;
};
```

> [!NOTE]
> 使用 <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> 需要 .NET Framework 4.7 (或更新版本) 或 .NET Core 1.1 (或更新版本)。 它在 .NET Standard 2.0 中不提供。

若您要處理 COM API，您可能必須將字串封送處理為 `BSTR`。 使用 <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> 值，您可以將字串封送處理為 `BSTR`。

```csharp
public struct BString
{
    [MarshalAs(UnmanagedType.BStr)]
    public string str;
}
```

```cpp
struct BString
{
    BSTR str;
};
```

使用 WinRT 型 API 時，您可能需要將字串封送處理為 `HSTRING`。  使用 <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> 值時，您可以將字串封送處理為 `HSTRING`。

```csharp
public struct HString
{
    [MarshalAs(UnmanagedType.HString)]
    public string str;
}
```

```cpp
struct BString
{
    HSTRING str;
};
```

若您的 API 要求您在結構中就地傳遞字串，您可以使用 <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> 值。 請注意，由 `ByValTStr` 封送處理的字串編碼是由 `CharSet` 屬性決定。 此外，它要求字串長度必須由 <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> 欄位傳遞。

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
public struct DefaultString
{
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 4)]
    public string str;
}
```

```cpp
struct DefaultString
{
    char str[4];
};
```

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct DefaultString
{
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 4)]
    public string str;
}
```

```cpp
struct DefaultString
{
    char16_t str[4]; // Could also be wchar_t[4] on Windows.
};
```

## <a name="customizing-decimal-field-marshaling"></a>自訂十進位欄位封送處理

如果您在 Windows 上工作，您可能會遇到一些使用原生 [`CY` 或 `CURRENCY`](/windows/win32/api/wtypes/ns-wtypes-cy~r1) 結構的 API。 根據預設，.NET `decimal` 類型會封送處理為原生 [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) 結構。 不過，您可以使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 搭配 <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> 值來指示封送處理器將 `decimal` 值轉換為原生 `CY` 值。

```csharp
public struct Currency
{
    [MarshalAs(UnmanagedType.Currency)]
    public decimal dec;
}
```

```cpp
struct Currency
{
    CY dec;
};
```

## <a name="marshaling-systemobjects"></a>封送處理 `System.Object`

在 Windows 上，您可以將 `object` 型別欄位封送處理為機器碼。 您可以將這些欄位封送處理為下列三種類型的其中一種：

- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

根據預設，`object` 類型欄位將會封送處理為會包裝物件的 `IUnknown*`。

```csharp
public struct ObjectDefault
{
    public object obj;
}
```

```cpp
struct ObjectDefault
{
    IUnknown* obj;
};
```

若要將物件欄位封送處理為 `IDispatch*`，請新增具有 <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> 值的 <xref:System.Runtime.InteropServices.MarshalAsAttribute>。

```csharp
public struct ObjectDispatch
{
    [MarshalAs(UnmanagedType.IDispatch)]
    public object obj;
}
```

```cpp
struct ObjectDispatch
{
    IDispatch* obj;
};
```

若要將它封送處理為 `VARIANT`，請新增具有 <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> 值的 <xref:System.Runtime.InteropServices.MarshalAsAttribute>。

```csharp
public struct ObjectVariant
{
    [MarshalAs(UnmanagedType.Struct)]
    public object obj;
}
```

```cpp
struct ObjectVariant
{
    VARIANT obj;
};
```

下表說明 `obj` 的不同執行階段型別如何對應到 `VARIANT` 中儲存的各種型別：

| .NET 型別 | VARIANT 型別 | | .NET 型別 | VARIANT 型別 |
|------------|--------------|-|----------|--------------|
|  `byte`  | `VT_UI1` |     | `System.Runtime.InteropServices.BStrWrapper` | `VT_BSTR` |
| `sbyte`  | `VT_I1`  |     | `object`  | `VT_DISPATCH` |
| `short`  | `VT_I2`  |     | `System.Runtime.InteropServices.UnknownWrapper` | `VT_UNKNOWN` |
| `ushort` | `VT_UI2` |     | `System.Runtime.InteropServices.DispatchWrapper` | `VT_DISPATCH` |
| `int`    | `VT_I4`  |     | `System.Reflection.Missing` | `VT_ERROR` |
| `uint`   | `VT_UI4` |     | `(object)null` | `VT_EMPTY` |
| `long`   | `VT_I8`  |     | `bool` | `VT_BOOL` |
| `ulong`  | `VT_UI8` |     | `System.DateTime` | `VT_DATE` |
| `float`  | `VT_R4`  |     | `decimal` | `VT_DECIMAL` |
| `double` | `VT_R8`  |     | `System.Runtime.InteropServices.CurrencyWrapper` | `VT_CURRENCY` |
| `char`   | `VT_UI2` |     | `System.DBNull` | `VT_NULL` |
| `string` | `VT_BSTR`|
