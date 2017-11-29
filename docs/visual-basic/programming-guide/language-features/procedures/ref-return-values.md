---
title: "Ref 傳回值 (Visual Basic)"
ms.custom: 
ms.date: 04/28/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 560607f7aa304b25314daabeef3952e6bbef7426
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="support-for-reference-return-values-visual-basic"></a>如需參考傳回值 (Visual Basic) 的支援

從 C# 7 開始，C# 語言支援*參考傳回值*。 若要了解參考傳回值的方法之一是它們是相反的由參考傳遞至方法的引數。 修改參考所傳遞的引數時，所做的變更會反映在變數的值，呼叫端上。 當方法呼叫者提供參考傳回值時，呼叫端所做的參考傳回值的修改會反映在呼叫的方法的資料。

Visual Basic 不允許您撰寫方法具有參考傳回值，但它確實可讓您使用參考傳回值。 換句話說，您可以呼叫具有參考傳回值的方法，並修改該傳回值，並參考傳回值的變更會反映在呼叫的方法的資料。

## <a name="modifying-the-ref-return-value-directly"></a>直接修改 ref 傳回值

方法一律會成功，並沒有任何`ByRef`參數，您可以直接修改參考傳回值。 您只要將新值指派給傳回的參考傳回值的運算式。 

下列 C# 範例會定義`NumericValue.IncrementValue`遞增內部的值並將其傳回做為參考的方法傳回的值。 

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

將參考傳回值，然後修改下列 Visual Basic 範例中的呼叫端。 請注意，線條`NumericValue.IncrementValue`方法呼叫不會將值指派給方法。 相反地，它會指派值之方法所傳回的參考傳回值。

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a>使用 helper 方法

在其他情況下，直接修改參考傳回值的方法呼叫不一定需要這樣做。 例如，傳回的字串搜尋方法可能無法永遠找到相符項目。 在此情況下，您會想要修改參考傳回值，只有當搜尋已成功。

下列 C# 範例說明這個案例。 它會定義`Sentence`以 C# 撰寫的類別包含`FindNext`句子開頭為指定的子字串中尋找下一個文字的方法。 字串會以參考傳回值傳回，而參考所傳遞至方法的 `Boolean` 變數會指出搜尋是否成功。 參考傳回值指出呼叫端可以只讀取傳回的值;他或她也可以修改它，而且所做的修改會反映在內部所包含的資料在`Sentence`類別。

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

直接修改參考傳回值在此情況下不可靠，因為在方法呼叫可能會失敗，以尋找相符項目並傳回句子中的第一個單字。 在此情況下，呼叫端會不小心修改句子的第一個字。 這可能無法傳回呼叫端`null`(或`Nothing`在 Visual Basic 中)。 但在此情況下，嘗試修改的字串，其值是`Nothing`會擲回<xref:System.NullReferenceException>。 如果傳回呼叫端可能也會防止<xref:System.String.Empty?displayProperty=nameWithType>，但這需要呼叫端定義其值的字串變數<xref:System.String.Empty?displayProperty=nameWithType>。 呼叫者可以修改該字串，而本身的修改做任何用途，因為修改的字串有字沒有關聯性中所儲存的句子`Sentence`類別。

若要處理這種情況下，最好是將參考傳回值所參考的 helper 方法。 Helper 方法則會包含邏輯，以判斷是否方法呼叫成功，如果有，若要修改參考傳回值。 下列範例提供可能的實作。

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a>請參閱

[值或傳參考方式傳遞引數](passing-arguments-by-value-and-by-reference.md)   
[Visual Basic 中的程序](index.md)   


