---
title: 存取控制 (F#)
description: '了解如何控制存取權等型別、 方法和函式，在 F # 程式設計語言的程式設計項目。'
ms.date: 05/16/2016
ms.openlocfilehash: 6b13ac03d2a4a6c53b53d4c790760f5d51b334ee
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43456340"
---
# <a name="access-control"></a>存取控制

*存取控制*指宣告哪些用戶端可以使用特定程式項目，例如類型、 方法和函式。

## <a name="basics-of-access-control"></a>存取控制的基本概念
在 F # 中，存取控制規範`public`， `internal`，和`private`可以套用至模組、 類型、 方法、 值的定義，函式、 屬性和明確欄位。

- `public` 指出所有呼叫端可以存取實體。

- `internal` 表示實體，可以存取只能從相同的組件。

- `private` 表示實體，可以存取只能從封入類型或模組。

>[!NOTE] 
存取規範`protected`未使用在 F # 中，雖然它是可接受的如果您正在使用中支援的語言撰寫的類型`protected`存取。 因此，如果您覆寫受保護的方法，您的方法仍然只能在類別和其下階中存取。

一般情況下，規範放，除非在實體的名稱前面`mutable`或`inline`使用規範時，會在存取控制規範之後。

如果沒有存取規範，則預設值是`public`，除了`let`型別，其一律為繫結`private`為型別。

F # 中的簽章提供另一個機制來控制存取權 F # 程式項目。 簽章並不需要存取控制。 如需詳細資訊，請參閱[簽章](signatures.md)。

## <a name="rules-for-access-control"></a>存取控制規則
存取控制受限於下列規則：

- 繼承的宣告 (也就是使用`inherit`指定類別的基底類別)、 介面宣告 （也就，指定類別實作的介面），和擷取成員一律具有相同的存取範圍，為封入類型。 因此，存取控制規範不能使用這些建構。

- 差別等位中的個別案例的存取範圍取決於已區分的聯集本身的存取範圍。 也就是特定聯集是不比聯集本身存取。

- 協助工具的記錄類型的個別欄位不能取決於記錄本身的存取範圍。 也就是特定的記錄標籤是不比記錄本身存取。

## <a name="example"></a>範例
下列程式碼說明如何使用存取控制的規範。 在專案中，有兩個檔案`Module1.fs`和`Module2.fs`。 每個檔案是以隱含方式的模組。 因此，有兩個模組，`Module1`和`Module2`。 私用類型和一個內部型別會定義在`Module1`。 無法從存取私用類型`Module2`，但是內部型別。

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]
    
下列程式碼測試中建立型別的存取範圍`Module1.fs`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]
    
## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

[簽章](signatures.md)
