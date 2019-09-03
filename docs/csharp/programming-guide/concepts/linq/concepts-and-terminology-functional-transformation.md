---
title: 概念和術語 (功能性轉換) (C#)
ms.date: 07/20/2015
ms.assetid: 03defb3a-7e17-4ab1-8efa-4dd66621e860
ms.openlocfilehash: 3e2ecc4c2f70700ae92ee36b6f122059b922332e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040637"
---
# <a name="concepts-and-terminology-functional-transformation-c"></a>概念和術語 (功能性轉換) (C#)

本主題說明純功能性轉換的概念與術語。 轉換資料的功能性轉換方法所產生的程式碼通常比更傳統的命令性程式設計可以更快速地進行程式設計、更明確，而且更容易進行偵錯與維護。

請注意，本節中的主題用意不在於完整說明功能性程式設計。 而在於識別更容易將 XML 從一個組織結構轉換為另一個組織結構的某些功能性程式設計能力。

## <a name="what-is-pure-functional-transformation"></a>何謂純功能性轉換？

在「純功能性轉換」  中，一組稱為「純虛擬函式」  的函式會定義如何將一組結構化的資料從其原始格式轉換為另一個格式。 「純」這個字表示這些函式是「可組合的」  也就是說，這些函式需要是：

- 「獨立的」  ，讓這些函式可以自由排列與重新整理，而不會與程式的其餘部分有任何牽連或互相依賴。 純轉換與其環境無關，也不會影響其環境。 也就是說，用於轉換的函式沒有「副作用」  。

- 「無狀態」  ，如此一來，在相同的輸入上執行相同的函式或特定一組函式時，永遠會導致相同的輸出。 純轉換絲毫不會記得其先前的用途。

> [!IMPORTANT]
> 在本教學課程的其餘部分，「純虛擬函式」這個名詞用於一般含意，表示程式設計方法而非特定的語言功能。
>
> 請注意，在 C# 中，純虛擬函式必須實作為方法。
>
> 同時，您不應將純虛擬函式誤解為 C++ 的純虛擬方法。 後者表示包含的類別是抽象的，而且不會提供任何方法主體。

### <a name="functional-programming"></a>功能性程式設計

「函式程式設計」  是一種程式設計方法，可直接支援純功能性轉換。

根據過去的經驗，一般用途的函式程式設計語言 (例如，ML、Scheme、Haskell 與 F#) 主要受到學術團體的注意。 雖然函式程式設計一直可以使用 C# 撰寫純功能性轉換，但是其困難度始終讓大部分的程式設計人員卻步。 不過，在最近版本的 C# 中，新語言建構 (例如，Lambda 運算式和型別推斷) 讓函式程式設計更容易，產能也更高。

如需功能性程式設計的詳細資訊，請參閱[功能性程式設計與命令式程式設計 (C#)](./functional-programming-vs-imperative-programming.md).

#### <a name="domain-specific-fp-languages"></a>網域指定的 FP 語言

雖然目前尚未廣泛採用一般功能性程式設計語言，但是特定網域指定的功能性程式設計語言比較受歡迎。 例如，階層式樣式表 (CSS) 用於決定許多網頁的外觀及操作，而可延伸樣式表語言轉換 (XSLT) 樣式表則廣泛用於 XML 資料操作。 如需 XSLT 的詳細資訊，請參閱 [XSLT 轉換](../../../../standard/data/xml/xslt-transformations.md)。

## <a name="terminology"></a>用語

下表定義與功能性轉換相關的一些辭彙。

高順序 (第一級) 函式 \
可以視為程式設計物件的函式。 例如，高順序函式可以傳遞到其他函式，或從其他函式傳回。 在 C# 中，委派和 Lambda 運算式都是支援高順序函式的語言功能。 若要撰寫高順序函式，您可以宣告一或多個引數以取得委派，而且在呼叫高順序函式時，您通常可以使用 Lambda 運算式。 許多標準查詢運算子都是高順序函式。

如需詳細資訊，請參閱[標準查詢運算子概觀 (C#)](./standard-query-operators-overview.md)。

Lambda 運算式 \
基本上，這是可用於任何需要委派型別之處的內嵌匿名函式。 這是 Lambda 運算式的簡化定義，但這適用於此教學課程的用途。

如需詳細資訊，請參閱 [Lambda 運算式](../../statements-expressions-operators/lambda-expressions.md)。

集合 \
一組結構化的資料，通常屬於統一的型別。 為與 LINQ 相容，集合必須實作 <xref:System.Collections.IEnumerable> 介面或 <xref:System.Linq.IQueryable> 介面 (或以下其中一個泛型對應項目：<xref:System.Collections.Generic.IEnumerator%601> 或 <xref:System.Linq.IQueryable%601>)。

元組 (匿名型別) \
這是一個數學概念，一個 Tuple 表示一個有限的物件順序，每個都有特定的型別。 Tuple 也稱為排序清單。 匿名型別為此概念的語言實作，可以宣告未具名的類別型別，並同時具現化該類別的物件。

如需詳細資訊，請參閱[匿名型別](../../classes-and-structs/anonymous-types.md)。

型別推斷 (隱含型別) \
編譯器在沒有明確的型別宣告時，判斷變數型別的能力。

如需詳細資訊，請參閱[隱含類型區域變數](../../classes-and-structs/implicitly-typed-local-variables.md)。

延後執行與延遲評估 \
延後運算式的評估，直到實際需要其解決的值為止。 在集合中，支援延後執行。

如需詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](./introduction-to-linq-queries.md) 和 [LINQ to XML 中的延後執行和延遲評估 (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)。

這些語言功能將用於本節的所有程式碼範例中。

## <a name="see-also"></a>另請參閱

- [純功能性轉換簡介 (C#)](./introduction-to-pure-functional-transformations.md)
- [函數式程式設計與命令式程式設計的比較 (C#)](./functional-programming-vs-imperative-programming.md)
