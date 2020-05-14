---
title: 使用實作 IDisposable 的物件
ms.date: 05/13/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
ms.openlocfilehash: d0d55a9253fee1ffcfd5c10714a1118883f6c4ce
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396976"
---
# <a name="using-objects-that-implement-idisposable"></a>使用實作 IDisposable 的物件

通用語言執行平臺的垃圾收集行程會回收 managed 物件所使用的記憶體，但是使用非受控資源的類型 <xref:System.IDisposable> 會執行介面，以允許回收這些非受控資源所需的資源。 實作 <xref:System.IDisposable> 的物件使用完畢時，您應呼叫物件的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 實作。 您可以使用下列其中一種作法：

- 使用 c # `using` 語句（ `Using` 在 Visual Basic 中）。
- 藉由執行 `try/finally` 區塊，並 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 在中呼叫 `finally` 。

## <a name="the-using-statement"></a>using 陳述式

C # 中的[ `using` 語句](../../csharp/language-reference/keywords/using-statement.md)和中的[ `Using` 語句](../../visual-basic/language-reference/statements/using-statement.md)Visual Basic 會簡化您必須撰寫的程式碼，以清除物件。 `using` 陳述式會取得一項或多項資源、執行您指定的陳述式，然後自動處置該物件。 不過，`using` 陳述式只對建構物件的方法範圍內所使用的物件有其實用之處。

下列範例會使用 `using` 陳述式建立和發行 <xref:System.IO.StreamReader?displayProperty=nameWithType> 物件。

[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]

雖然類別會實作為 <xref:System.IO.StreamReader> <xref:System.IDisposable> 介面，這表示它會使用非受控資源，但此範例並不會明確地呼叫 <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> 方法。 當 C# 或 Visual Basic 編譯器遇到 `using` 陳述式時，會發出相當於下列明確包含 `try/finally` 區塊之程式碼的中繼語言 (IL)。

[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]

C# `using` 陳述式還可讓您以單一陳述式取得多項資源，其內部相當於巢狀的 `using` 陳述式。 下列範例會將兩個 <xref:System.IO.StreamReader> 物件具現化，以便讀取兩個不同檔案的內容。

[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Try/finally 區塊

您可以選擇直接實作 `try/finally` 區塊，而不將 `try/finally` 區塊包裝在 `using` 陳述式中。 這可能是您的個人編碼樣式，或者您可能會因為下列其中一個原因而想要這麼做：

- 包含 `catch` 區塊以處理區塊中擲回的例外狀況 `try` 。 否則，在語句中擲回的任何例外狀況 `using` 都不會被處理。

- 若要將實作 <xref:System.IDisposable> 且範圍對於物件宣告所在區塊並非區域的物件具現化。

下列範例類似上述範例，不過它會使用 `try/catch/finally` 區塊具現化、使用和處置 <xref:System.IO.StreamReader> 物件，以及處理 <xref:System.IO.StreamReader> 建構函式和其 <xref:System.IO.StreamReader.ReadToEnd%2A> 方法擲回的所有例外狀況。 區塊中的程式碼 `finally` <xref:System.IDisposable> 會在 `null` 呼叫方法之前，檢查所執行的物件 <xref:System.IDisposable.Dispose%2A> 。 若未這樣做，可能導致執行階段產生 <xref:System.NullReferenceException> 例外狀況。

[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]

如果您的程式語言不支援 `using` 陳述式，但是允許直接呼叫 <xref:System.IDisposable.Dispose%2A> 方法，而使得您選擇實作或必須實作 `try/finally` 區塊，則可以遵循這個基本模式。

## <a name="idisposable-instance-members"></a>IDisposable 實例成員

如果類別將 <xref:System.IDisposable> 實作為實例成員（也就是欄位或屬性），則類別也應該會執行 <xref:System.IDisposable> 。 如需詳細資訊，請參閱[執行 cascade dispose](implementing-dispose.md#cascade-dispose-calls)。

## <a name="see-also"></a>請參閱

- [清除 Unmanaged 資源](../../../docs/standard/garbage-collection/unmanaged.md)
- [using 語句（c # 參考）](../../csharp/language-reference/keywords/using-statement.md)
- [Using 陳述式 (Visual Basic)](../../visual-basic/language-reference/statements/using-statement.md)
