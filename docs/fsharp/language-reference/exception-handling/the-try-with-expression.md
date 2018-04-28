---
title: 例外狀況：try...with 運算式 (F#)
description: "了解如何使用 例外狀況處理 F # 'try...with' 運算式。"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 06e40b79fc1958918dc0615ce9d1004e0a6e74a5
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="exceptions-the-trywith-expression"></a>例外狀況：try...with 運算式

本主題描述`try...with`運算式、 使用在 F # 語言中處理的例外狀況的運算式。


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
`try...with`運算式用來處理在 F # 中的例外狀況。 類似於`try...catch`C# 中的陳述式。 上述語法中的程式碼中*expression1*可能會產生例外狀況。 `try...with`運算式傳回的值。 如果不擲回任何例外狀況，則整個運算式傳回的值*expression1*。 如果擲回例外狀況，每個*模式*與例外狀況，以及對應的第一個模式符合依次比較*運算式*，稱為*例外狀況處理常式*，針對該分支會執行，而且整個運算式傳回運算式的值，該例外狀況處理常式中。 如果沒有模式符合，直到找到相符的處理常式的呼叫堆疊會傳播例外狀況。 從例外狀況處理常式中的每個運算式傳回之值的類型必須符合的運算式傳回的型別`try`區塊。

通常，也發生錯誤的事實表示沒有有效的值可以從每個例外狀況處理常式中的運算式傳回。 常見的模式是有運算式的型別是選項類型。 下列程式碼範例將說明這種模式。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

例外狀況可以是.NET 例外狀況，或者可以是 F # 例外狀況。 您可以使用，以定義 F # 例外狀況`exception`關鍵字。

您可以使用各種不同的模式來篩選的例外狀況類型和其他條件。下表摘要說明選項。


|模式|描述|
|-------|-----------|
|:? *例外狀況類型*|符合指定的.NET 例外狀況類型。|
|:? *例外狀況型別*為*識別碼*|符合指定的.NET 例外狀況類型，但可讓例外狀況名稱的值。|
|*例外狀況名稱*(*引數*)|比對的 F # 例外狀況類型，並將引數繫結。|
|*identifier*|比對任何例外狀況，並將名稱繫結到的例外狀況物件。 相當於 **： 嗎？System.Exception 為 * * * 識別碼*|
|*識別項*時*條件*|如果條件為 true，則比對任何例外狀況。|

## <a name="examples"></a>範例
下列程式碼範例說明使用各種例外狀況處理常式模式。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]
    
>[!NOTE] 
`try...with`建構是從個別運算式`try...finally`運算式。 因此，如果您的程式碼需要`with`區塊和`finally`區塊中，您必須將巢狀處理兩個運算式。

>[!NOTE] 
您可以使用`try...with`在非同步工作流程和其他計算運算式，在其中的大小寫的自訂的版本`try...with`運算式使用。 如需詳細資訊，請參閱[非同步工作流程](../asynchronous-workflows.md)，和[計算運算式](../computation-expressions.md)。


## <a name="see-also"></a>另請參閱
[例外狀況處理](index.md)

[例外狀況類型](exception-types.md)

[例外狀況：`try...finally` 運算式](the-try-finally-expression.md)
