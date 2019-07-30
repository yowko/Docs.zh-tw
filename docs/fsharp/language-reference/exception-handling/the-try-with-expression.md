---
title: 例外狀況：Try...with 運算式
description: 瞭解如何使用F# 「試試 ...」具有「例外狀況處理」的運算式。
ms.date: 05/16/2016
ms.openlocfilehash: e4d615086a93e26b76cca460e797659ca13792b5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630255"
---
# <a name="exceptions-the-trywith-expression"></a>例外狀況：Try...with 運算式

本主題描述`try...with`運算式, 這是在F#語言中用於例外狀況處理的運算式。

## <a name="syntax"></a>語法

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a>備註

運算式是用來處理中F#的例外狀況。 `try...with` 這類似于中`try...catch` C#的語句。 在上述語法中,*運算式*中的程式碼可能會產生例外狀況。 `try...with`運算式會傳回值。 如果未擲回任何例外狀況, 則整個運算式會傳回值為*運算式*。 如果擲回例外狀況, 每個*模式*會依序與例外狀況進行比較, 而針對第一個比對模式, 會執行對應的*運算式*(稱為*例外狀況處理常式*), 並使用整體運算式傳回該例外狀況處理常式中運算式的值。 如果沒有符合的模式, 例外狀況會傳播呼叫堆疊, 直到找到相符的處理常式為止。 在例外狀況處理常式中, 從每個運算式傳回的數值型別, 必須符合從`try`區塊中的運算式傳回的類型。

通常, 發生錯誤的事實也表示沒有可從每個例外狀況處理常式中的運算式傳回的有效值。 常見的模式是讓運算式的類型是選項類型。 下列程式碼範例說明此模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

例外狀況可以是 .NET 例外狀況, 也可以F#是例外狀況。 您可以使用F# `exception`關鍵字來定義例外狀況。

您可以使用各種不同的模式來篩選例外狀況類型和其他條件;下表摘要說明這些選項。

|模式|說明|
|-------|-----------|
|:? *exception-type*|符合指定的 .NET 例外狀況類型。|
|:? *例外狀況-類型*做為*識別碼*|符合指定的 .NET 例外狀況類型, 但提供例外狀況的已命名值。|
|*exception-name*(*arguments*)|符合F#例外狀況類型, 並系結引數。|
|*identifier*|符合任何例外狀況, 並將名稱系結至例外狀況物件。 相當於 **:？Exception 作為**_識別碼_|
|*條件*的*識別碼*|如果條件為 true, 則符合任何例外狀況。|

## <a name="examples"></a>範例

下列程式碼範例說明如何使用各種例外狀況處理常式模式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> 結構是`try...finally`運算式中的另一個運算式。 `try...with` 因此, 如果您的`with`程式碼同時需要區塊`finally`和區塊, 您就必須將這兩個運算式加以嵌套。

> [!NOTE]
> 您可以在`try...with`非同步工作流程和其他計算運算式中使用, 在此情況下會使用`try...with`自訂版本的運算式。 如需詳細資訊, 請參閱[非同步工作流程](../asynchronous-workflows.md)和[計算運算式](../computation-expressions.md)。

## <a name="see-also"></a>另請參閱

- [例外狀況處理](index.md)
- [例外狀況類型](exception-types.md)
- [例外狀況：`try...finally`運算式](the-try-finally-expression.md)
