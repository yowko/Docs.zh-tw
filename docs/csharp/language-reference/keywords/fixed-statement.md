---
title: fixed 陳述式 (C# 參考)
ms.date: 04/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5dd117461f792ec7a10b740fbad277de52d05623
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="fixed-statement-c-reference"></a>fixed 陳述式 (C# 參考)

`fixed` 陳述式可防止記憶體回收行程重新配置可移動的變數。 `fixed` 陳述式只能用於[不安全](unsafe.md)的內容中。 `Fixed` 也可用來建立[固定大小緩衝區](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)。

`fixed` 陳述式會將指標設定為 Managed 變數，並在陳述式執行期間「固定」該變數。 可移動之受控變數的指標只適用於 `fixed` 內容。 如果未使用 `fixed` 內容，記憶體回收可能會意外地重新配置變數。 C# 編譯器只能讓您將指標指派給 `fixed` 陳述式中的 Managed 變數。

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

您可以使用陣列、字串、固定大小緩衝區或變數位址，來初始化指標。 下列範例說明如何使用變數位址、陣列和字串。 如需固定大小緩衝區的詳細資訊，請參閱[固定大小緩衝區](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)。

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

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


在不安全模式中，您可以配置堆疊上的記憶體，這不受限於記憶體回收，因此不需要固定。 如需詳細資訊，請參閱 [stackalloc](stackalloc.md)。

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a>C# 語言規格

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>請參閱

 [C# 參考](../index.md)  
 [C# 程式設計指南](../../programming-guide/index.md)  
 [C# 關鍵字](index.md)  
 [Unsafe.DangerousAPI](unsafe.md)  
 [固定大小的緩衝區](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
