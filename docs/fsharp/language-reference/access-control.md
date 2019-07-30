---
title: 存取控制
description: 瞭解如何以程式F#設計語言控制程式設計專案 (例如類型、方法和函式) 的存取。
ms.date: 05/16/2016
ms.openlocfilehash: ed77a09cf87aabf9a4134276e89e84aa42abd3c3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629967"
---
# <a name="access-control"></a>存取控制

*存取控制*是指宣告哪些用戶端可以使用特定的程式元素, 例如類型、方法和函式。

## <a name="basics-of-access-control"></a>存取控制的基本概念

在F#中, 存取控制`public`規範、 `internal`和`private`可以套用至模組、類型、方法、值定義、函數、屬性和明確欄位。

- `public`表示實體可由所有呼叫者存取。

- `internal`表示實體只能從相同的元件存取。

- `private`表示實體只能從封入類型或模組存取。

> [!NOTE]
> 存取規範`protected`不會用於中F#, 但如果您使用的類型是以支援`protected`存取的語言撰寫, 則此為可接受的。 因此, 如果您覆寫受保護的方法, 您的方法只會在類別和其子代內保持可存取狀態。

一般來說, 規範會放在機構名稱的前方, 但使用`mutable`或`inline`規範時 (出現在存取控制規範之後) 除外。

如果未使用存取規範, 則預設值為`public`, `let`但類型中的系結一律`private`會是類型。

中F#的簽章提供另一個機制來F#控制程式元素的存取。 存取控制不需要簽章。 如需詳細資訊，請參閱[簽章](signatures.md)。

## <a name="rules-for-access-control"></a>存取控制的規則

存取控制受限於下列規則:

- 繼承宣告 (也就是使用`inherit`來指定類別的基類)、介面宣告 (也就是指定類別實作為介面), 而抽象成員一律具有與封入類型相同的存取範圍。 因此, 您無法在這些結構上使用存取控制規範。

- 區分等位中個別案例的協助工具是由區分聯集本身的存取範圍所決定。 也就是說, 特定聯集的大小寫不會比等位本身更容易存取。

- 記錄類型之個別欄位的協助工具不能由記錄本身的存取範圍決定。 也就是說, 特定記錄標籤的存取權不如記錄本身。

## <a name="example"></a>範例

下列程式碼說明如何使用存取控制規範。 專案中有兩個檔案: `Module1.fs`和。 `Module2.fs` 每個檔案都是隱含的模組。 因此, 有兩個模組: `Module1`和`Module2`。 私用型別和內部型別定義于`Module1`中。 無法從存取私用`Module2`型別, 但內部型別可以。

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

下列程式碼會測試在中`Module1.fs`建立之類型的存取範圍。

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [簽章](signatures.md)
