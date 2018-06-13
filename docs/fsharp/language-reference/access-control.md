---
title: 存取控制 (F#)
description: '了解如何控制對等型別、 方法和函式，F # 程式語言中的程式設計項目。'
ms.date: 05/16/2016
ms.openlocfilehash: 0a5cc1faa1aef343aaca0abb0c42a0dd9a52fcbb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566518"
---
# <a name="access-control"></a>存取控制

*存取控制*指的是哪些用戶端可以使用特定程式項目，例如類型、 方法和函式的宣告。


## <a name="basics-of-access-control"></a>存取控制的基本概念
F # 中的存取控制規範`public`， `internal`，和`private`可以套用至模組、 類型、 方法、 值定義、 函式、 屬性和明確欄位。


- `public` 表示所有呼叫端都可以存取實體。

- `internal` 表示實體，可以存取只能從相同組件。

- `private` 表示實體，可以存取只能從封入類型或模組。


>[!NOTE] 
存取規範`protected`不使用在 F # 中，雖然它是可接受的如果您使用以支援語言所撰寫的型別`protected`存取。 因此，如果您覆寫的受保護的方法，您的方法仍然只能在類別和其下階中存取。

一般情況下，除非為實體的名稱前面放規範`mutable`或`inline`使用規範，而這會在存取控制規範之後。

如果使用沒有存取規範，則預設值是`public`，除了`let`永遠是的型別，繫結`private`型別。

F # 中的簽章提供另一個機制來控制 F # 程式項目的存取。 簽章並不需要存取控制。 如需詳細資訊，請參閱[簽章](signatures.md)。


## <a name="rules-for-access-control"></a>存取控制規則
存取控制受限於下列規則：


- 繼承宣告 (也就是使用`inherit`指定類別的基底類別)，介面宣告 （也就，指定類別實作的介面），以及抽象成員一定與封入類型相同的存取範圍。 因此，存取控制規範不能在這些建構函式。

- 差別等位中的個別案例不能有個別等位型別從其本身存取控制項修飾詞。

- 記錄類型的個別欄位不能有不同的記錄類型自己存取控制修飾詞。


## <a name="example"></a>範例
下列程式碼說明如何使用存取控制規範。 在專案中，有兩個檔案`Module1.fs`和`Module2.fs`。 每個檔案是以隱含方式的模組。 因此，有兩個模組，`Module1`和`Module2`。 私用類型和內部類型會定義在`Module1`。 無法從存取私用類型`Module2`，但可以內部型別。

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]
    
下列程式碼測試中建立的類型的存取範圍`Module1.fs`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]
    
## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

[簽章](signatures.md)
