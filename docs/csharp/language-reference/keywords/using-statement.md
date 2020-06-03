---
title: using 陳述式 - C# 參考
ms.date: 05/29/2020
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: b889d2fcbdf854dbe8948744810f9b74e9f0dac2
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84307042"
---
# <a name="using-statement-c-reference"></a>using 陳述式 (C# 參考)

提供方便的語法，以確保正確使用 <xref:System.IDisposable> 物件。 從 c # 8.0 開始， `using` 語句可確保正確使用 <xref:System.IAsyncDisposable> 物件。

## <a name="example"></a>範例

下列範例顯示如何使用 `using` 陳述式。

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

從 c # 8.0 開始，您可以針對 `using` 不需要大括弧的語句使用下列替代語法：

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a>備註

<xref:System.IO.File> 和 <xref:System.Drawing.Font> 是 Managed 類型的範例，這些類型會存取 Unmanaged 資源 (在本例中為檔案控制代碼和裝置內容)。 還有許多其他類型的 Unmanaged 資源，以及封裝這些資源的類別庫類型。 所有這類類型都必須執行 <xref:System.IDisposable> 介面或 <xref:System.IAsyncDisposable> 介面。

當 `IDisposable` 物件的存留期限制為單一方法時，您應該在 `using` 陳述式中宣告它並加以具現化。 `using` 陳述式會以正確的方式呼叫物件上的 <xref:System.IDisposable.Dispose%2A> 方法，而且 (當您如稍早所示使用它時) 它也會在一呼叫 <xref:System.IDisposable.Dispose%2A> 時讓物件本身超出範圍。 在 `using` 區塊內，物件是唯讀的，無法修改或重新指派。 如果物件會執行 `IAsyncDisposable` ，而不是 `IDisposable` ，則 `using` 語句會呼叫 <xref:System.IAsyncDisposable.DisposeAsync%2A> 和 `awaits` 傳回的 <xref:System.Threading.Tasks.ValueTask> 。 如需的詳細資訊 <xref:System.IAsyncDisposable> ，請參閱[執行 DisposeAsync 方法](../../../standard/garbage-collection/implementing-disposeasync.md)。

`using`語句可確保 <xref:System.IDisposable.Dispose%2A> <xref:System.IAsyncDisposable.DisposeAsync%2A> 即使在區塊內發生例外狀況，也會呼叫（或） `using` 。 您可以藉由將物件放在 `try` 區塊內，然後 <xref:System.IDisposable.Dispose%2A> 在區塊中呼叫（或）來達到相同的結果 <xref:System.IAsyncDisposable.DisposeAsync%2A> `finally` ; 事實上，這就是 `using` 編譯器轉譯語句的方式。 稍早的程式碼範例會在編譯時期展開為下列程式碼 (注意額外的大括號是為了建立物件的有限範圍)：

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

較新的 `using` 語句語法會轉譯成類似的程式碼。 `try`區塊會在宣告變數的位置開啟。 `finally`區塊會加入封閉區塊的結尾，通常是在方法的結尾處。

如需有關語句的詳細資訊 `try` - `finally` ，請參閱[try finally](try-finally.md)文章。

一個類型的多個實例可以在單一語句中宣告 `using` ，如下列範例所示。 請注意， `var` 當您在單一語句中宣告多個變數時，無法使用隱含類型變數（）：

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

您也可以使用 c # 8 引進的新語法結合相同類型的多個宣告，如下列範例所示：

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

您可以具現化資源物件，然後將該變數傳遞給 `using` 語句，但這不是最佳作法。 在此情況下，控制權離開 `using` 區塊之後，物件仍會留在範圍內，不過它可能無法再存取其非受控資源。 換句話說，它不再是完全初始化。 如果您嘗試在 `using` 區塊外部使用該物件，則會有導致擲回例外狀況的風險。 基於這個理由，最好在語句中具現化物件 `using` ，並將其範圍限制為 `using` 區塊。

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

如需處置 `IDisposable` 物件的詳細資訊，請參閱[使用實作 IDisposable 的物件](../../../standard/garbage-collection/using-objects.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)中的 [using 陳述式](~/_csharplang/spec/statements.md#the-using-statement)。 語言規格是 C# 語法及用法的限定來源。

## <a name="see-also"></a>另請參閱

- [C # 參考](../index.md)
- [C # 程式設計指南](../../programming-guide/index.md)
- [C # 關鍵字](index.md)
- [using 指示詞](using-directive.md)
- [記憶體回收](../../../standard/garbage-collection/index.md)
- [使用實作 IDisposable 的物件](../../../standard/garbage-collection/using-objects.md)
- [IDisposable 介面](xref:System.IDisposable)
- [c # 8.0 中的 using 語句](~/_csharplang/proposals/csharp-8.0/using.md)
