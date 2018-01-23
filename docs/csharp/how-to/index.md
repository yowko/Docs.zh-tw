---
title: "操作說明文章 (C# 指南)"
description: "集結了快速提示與簡要的程式碼範例"
author: billwagner
ms.author: wiwagn
ms.date: 12/20/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: d1bef5813df40fb5c6e6b96e0042a682022beb8d
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2018
---
# <a name="how-to-c"></a>操作說明 (C#)

在 C# 指南的＜操作說明＞一節中，您可以找到常見問題的快速解答。 在某些形況下，文章可能會列在多個章節內。 這是因為我們希望使用者能從多個搜尋管道輕鬆找到這些文章。 

## <a name="general-c-concepts"></a>一般 C# 概念

以下有幾個提示和訣竅是常見的 C# 開發人員做法。

- [使用物件初始設定式將物件初始化](../programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md)。
- [了解向方法傳遞結構及類別的不同](../programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)。
- [如何使用 Lambda 運算式](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md)。
- [使用全域命名空間別名解決類型名稱衝突](../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)。
- [使用運算子多載](../programming-guide/statements-expressions-operators/how-to-use-operator-overloading-to-create-a-complex-number-class.md)。
- [實作和呼叫自訂擴充方法](../programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md)。
- 連 C# 程式設計人員都可能想要[從 VB 使用`My` 命名空間](../programming-guide/namespaces/how-to-use-the-my-namespace.md)。
- [使用擴充方法建立 `enum` 類型的新方法](../programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md)。

### <a name="class-and-struct-members"></a>類別和結構成員

您可以建立類別及結構來實作您的程式。 撰寫類別或結構時常會用到這些技術。

- [宣告自動實作屬性](../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)。
- [宣告和使用 R/W 屬性](../programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties.md)。
- [定義常數](../programming-guide/classes-and-structs/how-to-define-constants.md)。
- [覆寫 `ToString` 方法來提供字串輸出](../programming-guide/classes-and-structs/how-to-override-the-tostring-method.md)。
- [定義抽象屬性](../programming-guide/classes-and-structs/how-to-define-abstract-properties.md)。
- [使用 XML 文件功能來記錄程式碼](../programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)。
- [明確實作介面成員](../programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)讓公用介面保持精簡。
- [明確實作兩個介面的成員](../programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)。

### <a name="working-with-collections"></a>使用集合

這些文章有助您使用資料集合。

- [使用集合初始設定式將字典初始化](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md)。
- [使用 `foreach` 存取集合中的所有元素](../programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)。

## <a name="strings"></a>字串

字串是用來顯示或操作文字的基本資料類型。 這些文章會示範字串的常見做法。

- [比較字串](../programming-guide/strings/how-to-compare-strings.md)。
- [修改字串內容](../programming-guide/strings/how-to-modify-string-contents.md)。
- [判斷字串是否代表一個數字](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)。
- [使用 `String.Split` 來分隔字串](parse-strings-using-split.md)。
- [將多個字串合併為一個字串](concatenate-multiple-strings.md)。
- [搜尋字串中的文字](../programming-guide/strings/how-to-search-strings-using-string-methods.md)。
- [使用規則運算式搜尋字串](../programming-guide/strings/how-to-search-strings-using-regular-expressions.md)。

## <a name="convert-between-types"></a>在類型之間轉換

您可能需要將物件轉換為不同類型。

- [判斷字串是否代表一個數字](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)。
- [在代表十六進位數字的字串與數字之間轉換](../programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)。
- [將字串轉換為 <xref:System.DateTime>](../programming-guide/strings/how-to-convert-a-string-to-a-datetime.md)。
- [將位元組陣列轉換為 int](../programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)。
- [將字串轉換為數字](../programming-guide/types/how-to-convert-a-string-to-a-number.md)。
- [使用 `as` 與 `is` 安全地轉換為其他類型](../programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)。
- [定義 `struct` 類型的轉換運算子](../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)。
- [決定類型是不是可為 Null 的實值型別](../programming-guide/nullable-types/how-to-identify-a-nullable-type.md)。
- [在可為 Null 與不可為 Null 的實值型別間轉換](../programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md)。

## <a name="equality-and-ordering-comparisons"></a>相等和排序比較

您可以建立定義自身相等規則的類型，或是定義該類型物件的自然順序。

- [測試以參考為依據的相等](../programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)。
- [定義類型的實值相等](../programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)。

## <a name="exception-handling"></a>例外狀況處理

.NET 程式會透過擲回例外狀況，回報方法未成功完成其作業。 在這些文章中，您會了解如何利用例外狀況。

- [使用 `try` 與 `catch` 處理例外狀況](../programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md)。
- [使用 `finally` 子句清除資源](../programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md)。
- [從非 CLS (Common Language Specification) 例外狀況復原](../programming-guide/exceptions/how-to-catch-a-non-cls-exception.md)。

## <a name="delegates-and-events"></a>委派和事件

委派和事件會提供有關鬆散結合程式碼區塊的策略功能。

- [宣告和使用委派及將其具現化](../programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)。
- [合併多點傳送委派](../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)。

事件會提供發佈或訂閱通知的機制。

- [訂閱及取消訂閱事件](../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。
- [實作介面中宣告的事件](../programming-guide/events/how-to-implement-interface-events.md)。
- [在程式碼發佈事件時符合 .NET Framework 方針](../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)。
- [從衍生類別引發在基底類別中定義的事件](../programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)。
- [在字典中儲存事件執行個體](../programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)。
- [實作自訂事件存取子](../programming-guide/events/how-to-implement-custom-event-accessors.md)。

## <a name="linq-practices"></a>LINQ 做法

LINQ 可讓您撰寫程式碼，來查詢支援 LINQ 查詢運算式模式的任何資料來源。 這些文章有助您理解模式，以及如何利用各種資料來源。

- [查詢集合](../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)。
- [在查詢中使用 Lambda 運算式](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-in-a-query.md)。
- [在查詢運算式中使用 `var`](../programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)。
- [從查詢傳回元素屬性的子集](../programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md)。
- [撰寫具有複雜篩選的查詢](../programming-guide/concepts/linq/how-to-write-queries-with-complex-filtering.md)。
- [排序資料來源的元素](../programming-guide/concepts/linq/how-to-sort-elements.md)。
- [排序多個索引鍵的元素](../programming-guide/concepts/linq/how-to-sort-elements-on-multiple-keys.md)。
- [控制投影的類型](../programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md)。
- [計算來源序列中值的出現次數](../programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md)。
- [計算中繼值](../programming-guide/concepts/linq/how-to-calculate-intermediate-values.md)。
- [合併多個來源的資料](../programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)。
- [找出兩個序列之間的集合差異](../programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)。
- [為空白的查詢結果偵錯](../programming-guide/concepts/linq/how-to-debug-empty-query-results-sets.md)。
- [將自訂方法新增到 LINQ 查詢](../programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)。

## <a name="multiple-threads-and-async-processing"></a>多個執行緒和非同步處理

新式程式常使用非同步作業。 這些文章會協助您了解如何使用這些技術。

- [使用 `System.Threading.Tasks.Task.WhenAll` 改善非同步效能](../programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)。
- [使用 `async` 與 `await` 平行提出多個 Web 要求](../programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)。
- [使用執行緒集區](../programming-guide/concepts/threading/how-to-use-a-thread-pool.md)。

## <a name="command-line-args-to-your-program"></a>程式的命令列引數

一般來說，C# 程式具有命令列引數。 這些文章會向您說明如何存取及處理這些命令列引數。

- [使用 `for` 擷取所有命令列引數](../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)。
- [使用 `foreach` 擷取所有命令列引數](../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)。
