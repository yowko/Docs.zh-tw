---
title: 概念和術語 (功能性轉換) -LINQ to XML
description: 瞭解純功能性轉換的概念與術語。
ms.date: 07/20/2015
ms.assetid: 03defb3a-7e17-4ab1-8efa-4dd66621e860
ms.openlocfilehash: a1c9c582235ac63fe50dd585ef5f046e9be8170e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552283"
---
# <a name="concepts-and-terminology-functional-transformation-linq-to-xml"></a>概念和術語 (功能性轉換)  (LINQ to XML) 

本文介紹純功能性轉換的概念和術語。 轉換資料的功能性轉換方法會產生程式碼，通常比更傳統的命令式程式設計更快、更具表達性，而且更容易進行偵測和維護。

請注意，本節中的文章並不是要完整解說功能性程式設計。 相反地，這些文章會識別一些功能性程式設計功能，讓您更輕鬆地將 XML 轉換成另一個圖形。

## <a name="what-is-pure-functional-transformation"></a>什麼是純功能性轉換

在「純功能性轉換」** 中，一組稱為「純虛擬函式」** 的函式會定義如何將一組結構化的資料從其原始格式轉換為另一個格式。 "Pure" 這個字表示函式是可 *組合*的，這需要它們是：

- 「獨立的」**，讓這些函式可以自由排列與重新整理，而不會與程式的其餘部分有任何牽連或互相依賴。 純轉換與其環境無關，也不會影響其環境。 也就是說，用於轉換的函式沒有「副作用」**。
- 「無狀態」**，如此一來，在相同的輸入上執行相同的函式或特定一組函式時，永遠會導致相同的輸出。 純轉換絲毫不會記得其先前的用途。

> [!IMPORTANT]
> 在本教學課程的其餘部分，「純虛擬函式」這個名詞用於一般含意，表示程式設計方法而非特定的語言功能。
>
> 請注意，純虛擬函式必須實作為 c # 中的方法，以及做為 Visual Basic 中的函式。
>
> 您不應該將純虛擬函式與 c + + 中的純虛擬方法混淆。 後者表示包含的類別是抽象的，而且不會提供任何方法主體。

### <a name="functional-programming"></a>函式程式設計

「函式程式設計」** 是一種程式設計方法，可直接支援純功能性轉換。

根據過去的經驗，一般用途的函式程式設計語言 (例如，ML、Scheme、Haskell 與 F#) 主要受到學術團體的注意。 雖然功能性程式設計一直可以在 C# 和 Visual Basic 中撰寫純功能性轉換，但是其困難度始終讓大部分的程式設計人員卻步。 不過，在這些語言的最新版本中，新的語言結構（例如 lambda 運算式和型別推斷）讓功能性程式設計更簡單且更具生產力。

如需功能性程式設計的詳細資訊，請參閱功能性程式設計 [與命令式程式設計](functional-vs-imperative-programming.md)的比較。

#### <a name="domain-specific-functional-programming-languages"></a>特定領域的功能性程式設計語言

雖然尚未廣泛採用一般功能性程式設計語言，但某些特定領域的功能性程式設計語言已有更好的成功。 例如，階層式樣式表 (CSS) 用來判斷許多網頁的外觀和操作方式，而且 (XSLT) 樣式表單中的可延伸樣式表單語言轉換會廣泛用於 XML 資料操作中。 如需 XSLT 的詳細資訊，請參閱 [XSLT 轉換](../data/xml/xslt-transformations.md)。

## <a name="terminology"></a>詞彙

下列清單定義一些與功能轉換相關的詞彙。

高順序 (第一級) 函式 \
可以視為程式設計物件的函式。 例如，高順序函式可以傳遞到其他函式，或從其他函式傳回。 在 C# 和 Visual Basic 中，委派和 Lambda 運算式都是支援高順序函式的語言功能。 若要撰寫高順序函式，您可以宣告一或多個引數以取得委派，而且在呼叫高順序函式時，您通常可以使用 Lambda 運算式。 許多標準查詢運算子都是高順序函式。

如需詳細資訊，請參閱 [標準查詢運算子總覽 (c # ) ](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) 和 [標準查詢運算子總覽 (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。

Lambda 運算式 \
基本上，這是可用於任何需要委派型別之處的內嵌匿名函式。 這是 lambda 運算式的簡化定義，但適用于本教學課程的目的。

如需詳細資訊，請參閱 [lambda 運算式 (c # 程式設計手冊) ](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) 和 [lambda 運算式 (Visual Basic) # B4 ](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。

集合 \
一組結構化的資料，通常屬於統一的型別。 為與 LINQ 相容，集合必須實作 <xref:System.Collections.IEnumerable> 介面或 <xref:System.Linq.IQueryable> 介面 (或以下其中一個泛型對應項目：<xref:System.Collections.Generic.IEnumerator%601> 或 <xref:System.Linq.IQueryable%601>)。

元組 (匿名型別) \
這是一個數學概念，一個 Tuple 表示一個有限的物件順序，每個都有特定的型別。 Tuple 也稱為排序清單。 匿名型別為此概念的語言實作，可以宣告未具名的類別型別，並同時具現化該類別的物件。

如需詳細資訊，請參閱 [匿名型別 (c # 程式設計手冊) ](../../csharp/programming-guide/classes-and-structs/anonymous-types.md) 和 [匿名型別 (Visual Basic) ](../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。

型別推斷 (隱含型別) \
編譯器在沒有明確的型別宣告時，判斷變數型別的能力。

如需詳細資訊，請參閱 [隱含類型區域變數 (c # 程式設計手冊) ](../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) 和 [區欄位型別推斷 (Visual Basic) ](../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。

延後執行與延遲評估 \
延後運算式的評估，直到實際需要其解決的值為止。 在集合中，支援延後執行。

如需更多 c # 資訊，請參閱 [LINQ 查詢的簡介 (c # ) ](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md) 和 [LINQ to XML (c # ) 中的順延強制和延遲評估 ](../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)。

如需詳細 Visual Basic 資訊，請參閱 LINQ to XML (Visual Basic) 中的 [基本查詢作業 (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md) 和 [延後執行和延遲評估 ](../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)。

這些語言功能將用於本節的所有程式碼範例中。

## <a name="see-also"></a>另請參閱

- [純功能性轉換簡介](introduction-pure-functional-transformations.md)
- [功能性程式設計與命令式程式設計](functional-vs-imperative-programming.md)
