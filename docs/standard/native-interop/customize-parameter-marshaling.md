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
# <a name="customizing-parameter-marshaling"></a>自訂參數封送處理

當 .NET 執行階段的預設參數封送處理行為不能滿足您要求時，可以使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> 屬性來自訂參數的封送處理方式。

## <a name="customizing-string-parameters"></a>自訂字串參數

.NET 有各種不同的格式可用於封送處理字串。 這些方法分為 C 樣式字串和以 Windows 為中心的字串格式的不同區段。

### <a name="c-style-strings"></a>C 樣式字串

每種格式都將傳遞以 Null 結尾的字串至機器碼。 它們因原生字串的編碼方式而不同。

| `System.Runtime.InteropServices.UnmanagedType` 值 | 編碼 |
|------------------------------------------------------|----------|
| LPStr | ANSI |
| LPUTF8Str | UTF-8 | 
| LPWStr | UTF-16 |
| LPTStr | UTF-16 |

<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType> 格式會稍有不同。 與 `LPWStr` 一樣，它將字串封送處理成以 UTF-16 編碼的原生 C 樣式字串。 不過，受控簽章允許您傳參考方式傳入字串，而符合的原生簽章接受以傳值方式傳入的字串。 此區別可讓您使用原生 API，該 API 接受以傳值方式傳入的字串，並在不必使用 `StringBuilder` 的情況下就地修改它。 我們建議您不要以手動方式使用此格式，因為它很容易導致與不相符的原生和受控簽章混淆。

### <a name="windows-centric-string-formats"></a>以 Windows 為中心的字串格式

當與 COM 或 OLE 介面互動時，您可能會發現原生函式接受以 `BSTR` 引數形式表示的字串。 您可以使用 <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> 非受控型別將字串封送處理為 `BSTR`。

如果您正在與 WinRT API 進行互動，則可以使用 <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> 格式將字串封送處理為 `HSTRING`。

## <a name="customizing-array-parameters"></a>自訂陣列參數

.NET 也提供您多種方法來封送處理陣列參數。 如果您正在呼叫接受 C 樣式陣列的 API，請使用 <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType> 非受控型別。 如果陣列中的值需要自訂封送處理，則您可以使用 `[MarshalAs]` 屬性上的 <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> 欄位來進行此動作。

如果您使用 COM API，則可能需要將陣列參數封送處理為 `SAFEARRAY*`。 若要這樣做，您可以使用 <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> 非受控型別。 在[自訂 `object` 欄位](./customize-struct-marshaling.md#marshaling-systemobjects)表格中可以看到 `SAFEARRAY` 元素的預設型別。 您可以使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> 和 <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> 欄位來自訂 `SAFEARRAY` 的確切元素型別。

## <a name="customizing-boolean-or-decimal-parameters"></a>自訂布林值或十進位參數

如需封送處理布林值或十進位參數的資訊，請參閱[自訂結構封送處理](customize-struct-marshaling.md)。

## <a name="customizing-object-parameters-windows-only"></a>自訂物件參數 (僅限 Windows)

在 Windows 上，.NET 執行階段提供不同的方式來將物件參數封送處理為機器碼。

### <a name="marshaling-as-specific-com-interfaces"></a>封送處理為特定的 COM 介面

如果您的 API 接受 COM 物件的指標，則可以在 `object` 型別參數上使用下列任一 `UnmanagedType` 格式，以告知 .NET 封送處理為這些特定介面：

- `IUnknown`
- `IDispatch`
- `IInspectable`

此外，如果您的類型標示為 `[ComVisible(true)]` 或您正在封送處理 `object` 類型，則可以使用 <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> 格式將物件封送處理為類型之 COM 檢視的 COM 可呼叫包裝函式。

### <a name="marshaling-to-a-variant"></a>封送處理為 `VARIANT`

如果您的原生 API 接受 Win32 `VARIANT`，則可以使用 `object` 參數上的 <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> 格式將物件封送處理為 `VARIANT`。 有關 .NET 型別和 `VARIANT` 型別之間的對應，請參閱有關[自訂 `object` 欄位](customize-struct-marshaling.md#marshaling-systemobjects)的文件。

### <a name="custom-marshalers"></a>自訂封送處理器

如果要將原生 COM 介面投射到其他受控類型，可以使用 `UnmanagedType.CustomMarshaler` 格式和 <xref:System.Runtime.InteropServices.ICustomMarshaler> 的實作來提供自有自訂封送處理程式碼。
