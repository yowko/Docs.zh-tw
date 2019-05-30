---
title: fixed 陳述式 - C# 參考
ms.custom: seodec18
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: 2c49c8517e15534121b0f8dbc04902b46a92ef20
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959357"
---
# <a name="fixed-statement-c-reference"></a>fixed 陳述式 (C# 參考)

`fixed` 陳述式可防止記憶體回收行程重新配置可移動的變數。 `fixed` 陳述式只能用於[不安全](unsafe.md)的內容中。 您也可以使用 `fixed` 關鍵字來建立[大小固定的緩衝區](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)。

`fixed` 陳述式會將指標設定為 Managed 變數，並在陳述式執行期間「固定」該變數。 可移動之受控變數的指標只適用於 `fixed` 內容。 如果未使用 `fixed` 內容，記憶體回收可能會意外地重新配置變數。 C# 編譯器只能讓您將指標指派給 `fixed` 陳述式中的 Managed 變數。

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

您可以使用陣列、字串、固定大小緩衝區或變數位址，來初始化指標。 下列範例說明如何使用變數位址、陣列和字串：

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

從 C# 7.3 開始，`fixed` 陳述式對陣列、字串、固定大小緩衝區或非受控變數以外的其他型別進行操作。 針對名稱為 `GetPinnableReference` 的方法，可以將任何實作方法的型別加以固定。 `GetPinnableReference` 必須將 `ref` 變數傳回到非受控型別。 請參閱[指標型別](../../programming-guide/unsafe-code-pointers/pointer-types.md)主題，以取得詳細資訊。 .NET Core 2.0 中引入的 .NET 型別 <xref:System.Span%601?displayProperty=nameWithType> 和 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> 使用此模式，而且可以加以固定。 下列範例會顯示這一點：

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

如果您正在建立應該參與此模式的型別，請參閱 <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> 以取得實作模式的範例。

如果指標的型別全都相同，則可以在一個陳述式中初始化多個指標：

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

若要初始化不同類型的指標，只要巢狀 `fixed` 陳述式即可，如下列範例所示。

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

執行陳述式中的程式碼之後，任何固定的變數都會取消固定並受限於記憶體回收。 因此，請不要指向 `fixed` 陳述式之外的變數。 `fixed` 陳述式中所宣告變數的範圍會設為該陳述式，使其更加簡單：

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

在 `fixed` 陳述式中初始化的指標是唯讀變數。 如果您要修改指標值，則必須宣告第二個指標變數並予以修改。 在 `fixed` 陳述式中宣告的變數無法修改：

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

您可以配置堆疊上的記憶體，此處不受記憶體回收限制，因此不需要釘選。 若要那麼做，請使用 [`stackalloc` 運算子](stackalloc.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [fixed 陳述式](~/_csharplang/spec/unsafe-code.md#the-fixed-statement)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [Unsafe.DangerousAPI](unsafe.md)
- [固定大小的緩衝區](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
