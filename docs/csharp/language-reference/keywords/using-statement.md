---
title: using 陳述式 - C# 參考
ms.date: 04/07/2020
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: a237a90b4782e0460857c3d5d887771bcc8ccaaf
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989177"
---
# <a name="using-statement-c-reference"></a>using 陳述式 (C# 參考)

提供方便的語法，以確保正確使用 <xref:System.IDisposable> 物件。 從 C# 8.0`using`開始,語句可<xref:System.IAsyncDisposable>確保正確使用 物件。

## <a name="example"></a>範例

下列範例顯示如何使用 `using` 陳述式。

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

從 C# 8.0 開始,對於不需要大`using`括弧的 語句,可以使用以下替代語法:

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a>備註

<xref:System.IO.File> 和 <xref:System.Drawing.Font> 是 Managed 類型的範例，這些類型會存取 Unmanaged 資源 (在本例中為檔案控制代碼和裝置內容)。 還有許多其他類型的 Unmanaged 資源，以及封裝這些資源的類別庫類型。 所有此類類型都必須實現<xref:System.IDisposable>介面<xref:System.IAsyncDisposable>或介面。

當 `IDisposable` 物件的存留期限制為單一方法時，您應該在 `using` 陳述式中宣告它並加以具現化。 `using` 陳述式會以正確的方式呼叫物件上的 <xref:System.IDisposable.Dispose%2A> 方法，而且 (當您如稍早所示使用它時) 它也會在一呼叫 <xref:System.IDisposable.Dispose%2A> 時讓物件本身超出範圍。 在塊`using`中,對像是唯讀的,不能修改或重新分配。 如果物件`IAsyncDisposable`支援`IDisposable`,`using`而非 ,<xref:System.IAsyncDisposable.DisposeAsync%2A>`awaits`文<xref:System.Threading.Tasks.Task>句呼叫與傳回的 。

語句`using`可<xref:System.IDisposable.Dispose%2A>確保<xref:System.IAsyncDisposable.DisposeAsync%2A>(或`using`) 即使塊中發生異常, 也會呼叫 。 通過將物件放在`try`<xref:System.IDisposable.Dispose%2A>塊中然後調用(<xref:System.IAsyncDisposable.DisposeAsync%2A>或`finally`在塊中;實際上,編譯器`using`就是這樣轉換 語句)來實現相同的結果。 稍早的程式碼範例會在編譯時期展開為下列程式碼 (注意額外的大括號是為了建立物件的有限範圍)：

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

較新的`using`語句語法轉換為類似的代碼。 塊`try`將在聲明變數的位置打開。 塊`finally`在封閉塊的末尾添加,通常在方法的末尾。

有關該語句的詳細資訊,`try`-`finally`請參閱[最後嘗試](try-finally.md)一文。

可以在單個`using`語句中聲明類型的多個實例,如以下示例所示。 請注意,在單個語句中聲明多個變數時,不能使用`var`隱式類型變數 ( ):

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

您可以使用與 C# 8 一起引入的新語法組合同一類型的多個聲明,如以下範例所示:

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

您可以實例化資源物件,然後將變數傳遞給`using`語句,但這不是最佳做法。 在此情況下，控制權離開 `using` 區塊之後，物件仍會留在範圍內，不過它可能無法再存取其非受控資源。 換句話說，它不再是完全初始化。 如果您嘗試在 `using` 區塊外部使用該物件，則會有導致擲回例外狀況的風險。 因此,最好實例化`using`語句中的物件並將其範圍限制`using`為 塊。

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

如需處置 `IDisposable` 物件的詳細資訊，請參閱[使用實作 IDisposable 的物件](../../../standard/garbage-collection/using-objects.md)。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)中的 [using 陳述式](~/_csharplang/spec/statements.md#the-using-statement)。 語言規格是 C# 語法及用法的限定來源。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 編程指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [using 指示詞](using-directive.md)
- [記憶體回收](../../../standard/garbage-collection/index.md)
- [使用實作 IDisposable 的物件](../../../standard/garbage-collection/using-objects.md)
- [IDisposable 介面](xref:System.IDisposable)
- [在 C# 8.0 中使用敘述](~/_csharplang/proposals/csharp-8.0/using.md)
