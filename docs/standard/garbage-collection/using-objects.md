---
title: 使用實作 IDisposable 的物件
ms.date: 04/07/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 70955d496f5cf9e3bf44b9bc03a054d1c96efe98
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44260015"
---
# <a name="using-objects-that-implement-idisposable"></a>使用實作 IDisposable 的物件

通用語言執行平台的記憶體回收行程會回收受控物件所使用的記憶體，但是使用非受控資源的類型會實作 <xref:System.IDisposable> 介面，以允許回收配置給這些非受控資源的記憶體。 實作 <xref:System.IDisposable> 的物件使用完畢時，您應呼叫物件的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 實作。 您可以使用下列其中一種做法：  
  
* 使用 C# `using` 陳述式或 Visual Basic `Using` 陳述式。  
  
* 藉由實作 `try/finally` 區塊。  

## <a name="the-using-statement"></a>using 陳述式

C# 中的 `using` 陳述式和 Visual Basic 中的 `Using` 陳述式可簡化建立和清除物件所必須撰寫的程式碼。 `using` 陳述式會取得一項或多項資源、執行您指定的陳述式，然後自動處置該物件。 不過，`using` 陳述式只對建構物件的方法範圍內所使用的物件有其實用之處。  
  
下列範例會使用 `using` 陳述式建立和發行 <xref:System.IO.StreamReader?displayProperty=nameWithType> 物件。  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
請注意，雖然 <xref:System.IO.StreamReader> 類別會實作 <xref:System.IDisposable> 介面，指出它使用的是 Unmanaged 資源，但是這個範例並不會明確呼叫 <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> 方法。 當 C# 或 Visual Basic 編譯器遇到 `using` 陳述式時，會發出相當於下列明確包含 `try/finally` 區塊之程式碼的中繼語言 (IL)。  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
C# `using` 陳述式還可讓您以單一陳述式取得多項資源，其內部相當於巢狀的 `using` 陳述式。 下列範例會將兩個 <xref:System.IO.StreamReader> 物件具現化，以便讀取兩個不同檔案的內容。  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Try/finally 區塊

您可以選擇直接實作 `try/finally` 區塊，而不將 `try/finally` 區塊包裝在 `using` 陳述式中。 這可成為您的個人編碼風格，也可能基於下列其中一個原因而這樣做：  
  
* 包含 `catch` 區塊以處理 `try` 區塊中擲回的任何例外狀況。 否則，當 `try/catch` 區塊不存在時，`using` 陳述式擲回的所有例外狀況都會是未處理，就連 `using` 區塊中擲回的任何例外狀況也一樣。  
  
* 若要將實作 <xref:System.IDisposable> 且範圍對於物件宣告所在區塊並非區域的物件具現化。  
  
下列範例類似上述範例，不過它會使用 `try/catch/finally` 區塊具現化、使用和處置 <xref:System.IO.StreamReader> 物件，以及處理 <xref:System.IO.StreamReader> 建構函式和其 <xref:System.IO.StreamReader.ReadToEnd%2A> 方法擲回的所有例外狀況。 請注意，在 `finally` 中的程式碼會先確認實作 <xref:System.IDisposable> 的物件不是 `null`，再呼叫 <xref:System.IDisposable.Dispose%2A> 方法。 若未這樣做，可能導致執行階段產生 <xref:System.NullReferenceException> 例外狀況。  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
如果您的程式語言不支援 `using` 陳述式，但是允許直接呼叫 <xref:System.IDisposable.Dispose%2A> 方法，而使得您選擇實作或必須實作 `try/finally` 區塊，則可以遵循這個基本模式。 
  
## <a name="see-also"></a>另請參閱

* [清除 Unmanaged 資源](../../../docs/standard/garbage-collection/unmanaged.md)   
* [using 陳述式 (C# 參考)](~/docs/csharp/language-reference/keywords/using-statement.md)   
* [Using 陳述式 (Visual Basic)](~/docs/visual-basic/language-reference/statements/using-statement.md)
