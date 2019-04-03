---
title: 原生互通性最佳做法 - .NET
description: 了解在 .NET 中與原生元件建立介面的最佳做法。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 5b65f80d3a81fab0d74ce26aec3b454c716a5d51
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412054"
---
# <a name="native-interoperability-best-practices"></a>原生互通性最佳做法

.NET 提供您各種自訂原生互通性程式碼的方式。 此文章包含 Microsoft 的 .NET 小組在原生互通性上遵循的指導方針。

## <a name="general-guidance"></a>一般指引

本節中的指導方針適用於所有互通案例。

- **✔️ 請這樣做** 為您的方法和參數使用與要呼叫之原生方法相同的命名和大小寫。
- **✔️ 請考慮** 為常數值使用相同的命名和大小寫。
- **✔️ 請這樣做** 使用與原生類型對應相近的 .NET 類型。 例如在 C# 中，當原生類型是 `unsigned int` 時就使用 `uint`。
- **✔️ 請這樣做** 當您想要的行為與預設行為不同時，才使用 `[In]` 和 `[Out]` 屬性。
- **✔️ 請考慮** 使用 <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> 來建立您的原生陣列緩衝區集區。
- **✔️ 請考慮** 將您的 P/Invoke 委派包裝在與您的原生程式庫有相同名稱和大小寫的類型中。
  - 這樣可讓您的 `[DllImport]` 屬性使用 C# `nameof` 語言功能來傳入原生程式庫名稱，並確保您不會拼錯原生程式庫的名稱。

## <a name="dllimport-attribute-settings"></a>DllImport 屬性設定

| 設定 | 預設 | 建議 | 詳細資料 |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  保留預設值  | 當此項目明確設為 False 時，失敗的 HRESULT 傳回值會轉換成例外狀況 (結果為定義中的傳回值會變成 Null)。|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | 取決於 API  | 如果 API 使用 GetLastError 並使用 Marshal.GetLastWin32Error 來取得值，請將此項目設為 True。 如果 API 設定的條件指出有錯誤，請先取得該錯誤再進行其他呼叫，以避免不小心複寫它。|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | `CharSet.None`，會退而使用 `CharSet.Ansi` 行為  | 當定義中出現字串或字元時，請明確地使用 `CharSet.Unicode` 或 `CharSet.Ansi` | 此項目指定值為 `false` 時，字串的封送行為及 `ExactSpelling` 的作用。 請留意到，`CharSet.Ansi` 在 Unix 上實際是 UTF8。 Windows「多數」時候是使用 Unicode，而 Unix 是使用 UTF8。 請在[字元集相關文件](./charset.md)查看詳細資訊。 |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | 將此項目設為 True 可獲得些微效能好處，因為執行階段不會根據 `CharSet` 的設定，查看名稱尾碼是 "A" 或 "W" 的替代函式 ("A" 是 `CharSet.Ansi` 而 "W" 是 `CharSet.Unicode`)。 |

## <a name="string-parameters"></a>字串參數

當 CharSet 是 Unicode 時或引數明確標示為 `[MarshalAs(UnmanagedType.LPWSTR)]`「且」該字串是以傳值方式傳遞時 (不是 `ref` 或 `out`)，則該字串會被固定並由機器碼直接使用 (而不是複製)。

請記得將 `[DllImport]` 標示為 `Charset.Unicode`，除非您明確地想要對字串進行 ANSI 處理。

**❌ 請勿** 使用 `[Out] string` 參數。 使用 `[Out]` 屬性以傳值方式傳遞的字串參數，可能會使執行階段不穩定 (如果該字串是暫留字串)。 請在 <xref:System.String.Intern%2A?displayProperty=nameWithType> 的文件中查看字串暫留的詳細資訊。

**❌ 請避免** `StringBuilder` 參數。 `StringBuilder` 封送「一律」會建立原生緩衝區複本。 因此，這麼做可能非常沒有效率。 請考慮呼叫接受字串之 Windows API 的典型案例：

1. 建立所需容量的 SB (配置受控容量) **{1}**
2. 叫用
   1. 配置原生緩衝區 **{2}**  
   2. 若為 `[In]`，則複製內容 (`StringBuilder` 參數的預設值)  
   3. 若為 `[Out]`，則將原生緩衝區複製到新配置的受控陣列中 **{3}** (也是 `StringBuilder` 的預設值)  
3. `ToString()` 配置另一個受控陣列 **{4}**

這樣是由 *{4}* 配置從機器碼取得字串。 要限制此情況最好的方式是在其他呼叫中重複使用 `StringBuilder`，但這樣仍然只儲存 *1* 配置。 這樣比較好使用及從 `ArrayPool` 快取字元緩衝區，而且在後續的呼叫您可以直接取得 `ToString()` 的配置。

`StringBuilder` 的另一個問題是它一律會將傳回緩衝區備份複製到第一個 Null。 如果傳回的字串沒有中止，或者它是雙重 Null 結尾的字串，則您 P/Invoke 最佳的狀態會是不正確。

如果您「確實」使用 `StringBuilder`，最後一個陷阱是該容量**不**包含隱藏的 Null (封送一律會計算)。 這經常被誤解，因為大部分 API 都想要緩衝區「包含」Null。 這會導致浪費/不必要的配置。 此外，此陷阱會防止執行階段最佳化 `StringBuilder` 封送以減少複本。

**✔️ 請考慮** 使用來自 `ArrayPool`的 `char[]`。

如需字串封送的詳細資訊，請參閱[預設的字串封送](../../framework/interop/default-marshaling-for-strings.md)和[自訂字串封送](customize-parameter-marshalling.md#customizing-string-parameters)。

> __Windows 特定__  
> 針對 `[Out]` 字串，CLR 預設會使用 `CoTaskMemFree` 來釋放字串，或是針對標示為 `UnmanagedType.BSTR` 的字串使用 `SysStringFree`。  
**對於有輸出字串緩衝區的 API**：  
> 傳入的字元計數必須包含 Null。 如果傳回值小於呼叫接收的傳入字元計數，則該值是「不含」尾端 Null 的字元數目。 否則，該計數為緩衝區「包含」Null 字元所需的大小。  
> - 傳入 5，取得 4：該字串為 4 個字元與一個尾端 Null。
> - 傳入 6，取得 5：該字串為 5 個字元長，需要 6 個字元的緩衝區以保存 Null。  
> [字串的 Windows 資料類型](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a>布林值參數和欄位

布林值很容易弄錯。 根據預設，.NET `bool` 會封送到 Windows `BOOL` (4 個位元組的值)。 不過，C 和 C++ 中的 `_Bool` 和 `bool` 是「單一」位元組。 這可能導致難以追蹤的錯誤 (bug)，因為傳回值會有一半被捨棄，這有可能「潛在地」變更結果。 如需 .NET `bool` 值封送至 C 或 C++ `bool` 型別的詳細資訊，請參閱[自訂布林欄位封送](customize-struct-marshalling.md#customizing-boolean-field-marshalling)文件。

## <a name="guids"></a>GUID

GUID 可直接在特徵標記中使用。 許多 Windows API 都接受 `GUID&` 類型的別名，如 `REFIID`。 當以傳址方式傳遞時，可以透過 `ref` 或 `[MarshalAs(UnmanagedType.LPStruct)]` 屬性來傳遞它們。

| GUID | 傳址 GUID |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

**❌ 請勿** 將 `[MarshalAs(UnmanagedType.LPStruct)]` 用於 `ref` GUID 參數以外的任何項目。

## <a name="blittable-types"></a>Blittable 類型

Blittable 類型是受控碼和機器碼有相同位元層級表示的類型。 因此它們不需要為了從機器碼封送而傳換成其他格式，而這樣可以改善為它們所偏好的效能。

**Blittable 類型：**

- `byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`
- 非巢狀的一維 Blittable 類型陣列 (例如，`int[]`)
- 有固定配置的結構和類別的執行個體欄位只有 Blittable 值類型
  - 固定配置需要 `[StructLayout(LayoutKind.Sequential)]` 或 `[StructLayout(LayoutKind.Explicit)]`
  - 結構預設為 `LayoutKind.Sequential`，類別為 `LayoutKind.Auto`

**非 Blittable：**

- `bool`

**有時 Blittable：**

- `char`、 `string`

以傳址方式傳遞 Blittable 類型時，封送處理器會將它們固定，而不會複製到中繼緩衝區。 (類別會以傳址的方式繼承地傳遞，結構搭配使用 `ref` 或 `out` 時，會以傳址的方式傳遞。)

當 `char` 在一維陣列中時，**或**當它所屬的類型明確地以 `CharSet = CharSet.Unicode` 標示為 `[StructLayout]` 時，它是 Blittable 的。

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

當 `string` 不是包含在其他類型中，且它是當作引數傳遞並標示 `[MarshalAs(UnmanagedType.LPWStr)]` 或已設定`CharSet = CharSet.Unicode`的 `[DllImport]`。

您可以藉由嘗試建立固定的 `GCHandle`，以查看某個類型是否為 Blittable 的。 如果該類型不是字串或被視為 Blittable，則 `GCHandle.Alloc` 會擲回 `ArgumentException`。

**✔️ 請這樣做** 盡可能讓您的結構是 Blittable 的。

如需詳細資訊，請參閱:

- [Blittable 和非 Blittable 類型](../../framework/interop/blittable-and-non-blittable-types.md)  
- [類型封送處理](type-marshalling.md)

## <a name="keeping-managed-objects-alive"></a>讓受控物件保持運作

`GC.KeepAlive()` 會確保物件在範圍保持運作，直到叫用 KeepAlive 方法。

[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) 可讓封送處理器使物件在 P/Invoke 期間保持運作。 可以使用它，而不使用方法特徵標記中的 `IntPtr`。 應改為使用 `SafeHandle`，它可有效地取代此類別。

[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) 允許固定受控物件，並取得指向它的原生指標。 基本模式為：  

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

固定不是 `GCHandle` 的預設值。 其他主要模式是透過機器碼將參考傳遞至受控物件，然後再回到受控碼 (通常是使用回呼)。 以下是模式：

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

請注意，必須明確釋放 `GCHandle`，以避免記憶體流失。

## <a name="common-windows-data-types"></a>常見的 Windows 資料類型

以下是常用於 Windows API 中的資料類型清單，以及在呼叫至 Windows 程式碼內時要使用的 C# 類型。

下列類型在 32 位元和 64 位元 Windows 上的大小相同 (除了其名稱)。

| 寬度 | Windows          | C (Windows)          | C#       | 替代函式                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| 32    | `BOOL`           | `int`                | `int`    | `bool`                               |
| 8     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| 8     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| 8     | `CHAR`           | `char`               | `sbyte`  |                                      |
| 8     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| 16    | `SHORT`          | `short`              | `short`  |                                      |
| 16    | `CSHORT`         | `short`              | `short`  |                                      |
| 16    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| 16    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| 16    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| 32    | `INT`            | `int`                | `int`    |                                      |
| 32    | `LONG`           | `long`               | `int`    |                                      |
| 32    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| 32    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| 64    | `QWORD`          | `long long`          | `long`   |                                      |
| 64    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| 64    | `LONGLONG`       | `long long`          | `long`   |                                      |
| 64    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| 64    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| 32    | `HRESULT`        | `long`               | `int`    |                                      |
| 32    | `NTSTATUS`       | `long`               | `int`    |                                      |


下列類型 (為指標) 確實按照平台的寬度。 將 `IntPtr`/`UIntPtr` 用於這些。

| 帶正負號指標類型 (使用 `IntPtr`) | 不帶正負號指標類型 (使用 `UIntPtr`) |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

Windows `PVOID` 是 C `void*`，可以作為 `IntPtr` 或 `UIntPtr` 來封送，但建議盡可能使用 `void*`。

[Windows 資料類型](/windows/desktop/WinProg/windows-data-types)

[資料類型範圍](/cpp/cpp/data-type-ranges)

## <a name="structs"></a>結構

受控結構是在堆疊上建立的，直到方法傳回才會將它移除。 根據定義，他們是「固定的」(不會被 GC 移除)。 如果機器碼不使用目前方法結尾所傳遞的指標，您也可以直接接受不安全程式碼區塊中的位址。

Blittable 的結構效能更好，因為封送層可以直接使用它們。 請嘗試讓結構是 Blittable 的 (例如，避免`bool`)。 如需詳細資訊，請參閱 [Blittable 類型](#blittable-types)一節。

「如果」結構是 Blittable 的，為了獲得更好的效能，請使用 `sizeof()` 而不使用 `Marshal.SizeOf<MyStruct>()`。 如先前所述，您可以藉由嘗試建立固定的 `GCHandle`，以驗證類型是否為 Blittable 的。 如果該類型不是字串或被視為 Blittable，則 `GCHandle.Alloc` 會擲回 `ArgumentException`。

在定義中，結構的指標必須以 `ref` 傳遞，或者使用 `unsafe` 和 `*`。

**✔️ 請這樣做** 盡可能近似地對應受控結構與官方平台文件或標頭中所使用的圖形和名稱。

**✔️ 請這樣做** 針對 Blittable 結構使用 C# `sizeof()`，而不使用 `Marshal.SizeOf<MyStruct>()`，以改善效能。

`INT_PTR Reserved1[2]` 之類的陣列必須封送至兩個 `IntPtr` 欄位：`Reserved1a` 和 `Reserved1b`。 當原生陣列是基本類型時，我們可以使用 `fixed` 關鍵字來將它撰寫得更簡潔一點。 例如，在原生標頭中 `SYSTEM_PROCESS_INFORMATION` 看起來像這樣：

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

在 C# 中，我們可以將它撰寫像這樣：

```csharp
internal unsafe struct SYSTEM_PROCESS_INFORMATION
{
    internal uint NextEntryOffset;
    internal uint NumberOfThreads;
    private fixed byte Reserved1[48];
    internal Interop.UNICODE_STRING ImageName;
    ...
}
```

不過，固定的緩衝區有一些陷阱。 非 Blittable 類型的固定緩衝區不會正確地被封送，因此需要將原陣列展開成多個個別欄位。 此外，在 .NET Framework 和 .NET Core 3.0 之前，如果結構包含的固定緩衝區欄位是巢狀地包含在非 Blittable 結構中，則該固定緩衝區欄位不會正確地封送至機器碼。
