---
title: 固定大小緩衝區 - C# 程式設計指南
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 5bfd9f3f559e4780b910a2e5a3430b08a2183ee3
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833495"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>固定大小緩衝區 (C# 程式設計手冊)

在 C# 中，您可以使用 [fixed](../../language-reference/keywords/fixed-statement.md) 陳述式，在資料結構中建立具有固定大小陣列的緩衝區。 當您撰寫的方法會與其他語言或平台的資料來源互通時，固定大小緩衝區就很有用。 固定陣列可接受一般結構成員所允許的任何屬性或修飾詞。 唯一的限制是陣列類型必須為 `bool`、`byte`、`char`、`short`、`int`、`long`、`sbyte`、`ushort`、`uint`、`ulong`、`float` 或 `double`。

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>備註

在安全的程式碼中，包含陣列的 C# 結構不包含陣列項目。 相反地，該結構會包含元素的參考。 您可以將固定大小的陣列嵌入用於[不安全](../../language-reference/keywords/unsafe.md)程式碼區塊的 [struct](../../language-reference/keywords/struct.md)。

下列 `struct` 的大小為 8 個位元組。 `pathName` 陣列是參考：

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

`struct` 可以在不安全的程式碼中包含內嵌陣列。 在下列範例中，`fixedBuffer` 陣列具有固定大小。 您可以使用 `fixed` 陳述式來建立第一個項目的指標。 透過這個指標即可存取陣列的項目。 `fixed` 陳述式會將 `fixedBuffer` 執行個體欄位釘選到記憶體中的特定位置。

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

128 個元素的 `char` 陣列大小為 256 個位元組。 不論編碼為何，在固定大小的 [char](../../language-reference/keywords/char.md) 緩衝區中，每個字元一律會有兩個位元組。 即使 char 緩衝區使用 `CharSet = CharSet.Auto` 或 `CharSet = CharSet.Ansi` 封送處理至 API 方法或結構也一樣。 如需詳細資訊，請參閱<xref:System.Runtime.InteropServices.CharSet>。

上述範例示範如何存取 `fixed` 欄位而無需進行釘選，這是從 C# 7.3 開始可供使用的功能。

另一個常見的固定大小陣列是 [bool](../../language-reference/keywords/bool.md) 陣列。 `bool` 陣列中的元素大小一律為一個位元組。 `bool` 陣列不適用於建立位元陣列或緩衝區。

> [!NOTE]
> 除了使用 [stackalloc](../../language-reference/operators/stackalloc.md) 所建立的記憶體以外，C# 編譯器和 Common Language Runtime (CLR) 不會執行任何安全性緩衝區溢位檢查。 請與所有不安全的程式碼一樣小心使用。

不安全的緩衝區與一般陣列的差異如下：

- 您只能在不安全的內容中使用不安全的緩衝區。
- 不安全的緩衝區一律是向量或一維陣列。
- 陣列的宣告應包含計數，例如 `char id[8]`。 您不能使用 `char id[]`。
- 不安全的緩衝區只能是不安全內容中結構的執行個體欄位。

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [Unsafe 程式碼和指標](index.md)
- [fixed 陳述式](../../language-reference/keywords/fixed-statement.md)
- [互通性](../interop/index.md)
