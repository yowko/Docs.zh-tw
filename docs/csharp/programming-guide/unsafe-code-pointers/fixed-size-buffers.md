---
title: 固定大小緩衝區 - C# 程式設計指南
ms.date: 04/23/2020
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 5920dd125ded34969d60feb299568b56402056ab
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140547"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>固定大小緩衝區 (C# 程式設計手冊)

在 C# 中，您可以使用 [fixed](../../language-reference/keywords/fixed-statement.md) 陳述式，在資料結構中建立具有固定大小陣列的緩衝區。 當您撰寫的方法會與其他語言或平台的資料來源互通時，固定大小緩衝區就很有用。 固定陣列可接受一般結構成員所允許的任何屬性或修飾詞。 唯一的限制是陣列類型必須為 `bool`、`byte`、`char`、`short`、`int`、`long`、`sbyte`、`ushort`、`uint`、`ulong`、`float` 或 `double`。

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>備註

在安全的程式碼中，包含陣列的 C# 結構不包含陣列項目。 相反地，該結構會包含元素的參考。 您可以將固定大小的陣列嵌入用於[不安全](../../language-reference/keywords/unsafe.md)程式碼區塊的 [struct](../../language-reference/builtin-types/struct.md)。

下列`struct`的大小不會取決於陣列中的元素數目，因為`pathName`是參考：

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

`struct` 可以在不安全的程式碼中包含內嵌陣列。 在下列範例中，`fixedBuffer` 陣列具有固定大小。 您可以使用 `fixed` 陳述式來建立第一個項目的指標。 透過這個指標即可存取陣列的項目。 `fixed` 陳述式會將 `fixedBuffer` 執行個體欄位釘選到記憶體中的特定位置。

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

128 個元素的 `char` 陣列大小為 256 個位元組。 不論編碼為何，在固定大小的 [char](../../language-reference/builtin-types/char.md) 緩衝區中，每個字元一律會有兩個位元組。 即使 char 緩衝區使用 `CharSet = CharSet.Auto` 或 `CharSet = CharSet.Ansi` 封送處理至 API 方法或結構也一樣。 如需詳細資訊，請參閱 <xref:System.Runtime.InteropServices.CharSet>。

上述範例示範如何存取 `fixed` 欄位而無需進行釘選，這是從 C# 7.3 開始可供使用的功能。

另一個常見的固定大小陣列是 [bool](../../language-reference/builtin-types/bool.md) 陣列。 `bool` 陣列中的元素大小一律為一個位元組。 `bool` 陣列不適用於建立位元陣列或緩衝區。

固定大小的緩衝區會使用來<xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>編譯，這會指示 common language RUNTIME （CLR）類型包含可能溢位的非受控陣列。 這類似于使用[stackalloc](../../language-reference/operators/stackalloc.md)所建立的記憶體，它會自動啟用 CLR 中的緩衝區溢位偵測功能。 上一個範例顯示如何在中存在固定大小的緩衝區`unsafe struct`。

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

編譯器產生的 c # `Buffer`的屬性如下所示：

```csharp
internal struct Buffer
{
    [StructLayout(LayoutKind.Sequential, Size = 256)]
    [CompilerGenerated]
    [UnsafeValueType]
    public struct <fixedBuffer>e__FixedBuffer
    {
        public char FixedElementField;
    }

    [FixedBuffer(typeof(char), 128)]
    public <fixedBuffer>e__FixedBuffer fixedBuffer;
}
```

固定大小緩衝區與一般陣列有下列不同之處：

- 僅可用於[不安全](../../language-reference/keywords/unsafe.md)的內容中。
- 只能是結構的實例欄位。
- 它們一律是向量或一維陣列。
- 宣告應包含長度，例如`fixed char id[8]`。 您不能使用 `fixed char id[]`。

## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [不安全的程式碼和指標](index.md)
- [fixed 陳述式](../../language-reference/keywords/fixed-statement.md)
- [互通性](../interop/index.md)
