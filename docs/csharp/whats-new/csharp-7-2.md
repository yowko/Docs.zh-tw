---
title: C# 7.2 的新功能
description: C# 7.2 新功能的概觀。
ms.date: 08/16/2017
ms.openlocfilehash: 9525d52e5eab4b8213b8a1920531dc4b4d7ac0a3
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57673219"
---
# <a name="whats-new-in-c-72"></a>C# 7.2 的新功能

C# 7.2 是另一個小數點版本，其中新增了一些實用的功能。
此版本的主題之一是能夠避免不必要的複製或配置，讓實質型別作業能夠更有效率。

其餘功能則無足輕重。

C# 7.2 使用了[語言版本選取項目](../language-reference/configure-language-version.md)組態元素來選取編譯器語言版本。

此版本的新款語言功能包括：

* [撰寫安全、有效率之程式碼的技巧](#safe-efficient-code-enhancements)
  - 此為語法改進功能組合，其可讓使用參考語意進行實質型別作業變得可能。
* [無後置具名引數](#non-trailing-named-arguments)
  - 具名引數之後可以接著位置引數。
* [數值常值中的前置底線](#leading-underscores-in-numeric-literals)
  - 數值常值的任何列印數字之前，現都可加上前置底線。
* [`private protected` 存取修飾詞](#private-protected-access-modifier)
  - 您可利用 `private protected` 存取修飾詞，存取相同組件中的衍生類別。
* [`ref` 條件運算式](#conditional-ref-expressions)
  - 條件運算式 (`?:`) 的結果現在可以是參考。

## <a name="safe-efficient-code-enhancements"></a>安全、有效率的程式碼增強功能

您可利用 7.2 版新加入的語言功能，於使用參考語意時運用實值型別。 這些功能之設計目的是加強加效能，方法是將複製實質型別最小化，而不產生與使用參考型別相關的記憶體配置。 功能包括：

 - 參數上的 `in` 修飾詞，可指定引數將以傳址方式傳遞，但不受呼叫的方法修改。 將 `in` 修飾詞新增至引數是[來源相容變更](version-update-considerations.md#source-compatible-changes)。
 - 方法上 `ref readonly` 修飾詞的傳回內容，可指示方法要以傳址方式傳回其值，但不允許寫入該物件。 如果將傳回項目指派給值。則新增 `ref readonly` 修飾詞是[來源相容變更](version-update-considerations.md#source-compatible-changes)。 將 `readonly` 修飾詞新增至現有 `ref` 傳回陳述式是[不相容的變更](version-update-considerations.md#incompatible-changes)。 需要呼叫端更新 `ref` 本機變數的宣告，以包含 `readonly` 修飾詞。
 - `readonly struct` 宣告，可指示結構會固定，且應以 `in` 參數傳遞至其成員方法。 將 `readonly` 修飾詞新增至現有 struct 宣告是[二進位相容變更](version-update-considerations.md#binary-compatible-changes)。
 - `ref struct` 宣告，可指示結構類型會直接存取受控記憶體，且一律會配置堆疊。 將 `ref` 修飾詞新增至現有 `struct` 宣告是[不相容的變更](version-update-considerations.md#incompatible-changes)。 `ref struct` 不能是類別的成員，或用於可能會在堆積上配置的其他位置。

您可以在[撰寫安全、有效率的程式碼](../write-safe-efficient-code.md)深入了解這些變更。

## <a name="non-trailing-named-arguments"></a>無後置具名引數

當具名引數位於正確位置時，方法呼叫現在可以在位置引數前面使用具名引數。 如需詳細資訊，請參閱[具名和選擇性引數](../programming-guide/classes-and-structs/named-and-optional-arguments.md)。

## <a name="leading-underscores-in-numeric-literals"></a>數值常值中的前置底線

C# 7.0 中的數字分隔符號之實作支援，並不允許將 `_` 作為常值的第一個字元。 十六進位與二進位數值常值現在可以使用 `_` 開頭。

例如：

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a>_private protected_ 存取修飾詞

新的複合存取修飾詞：`private protected` 指出可藉由包含類別或在相同組件中宣告的衍生類別來存取成員。 `protected internal` 允許衍生類別或相同組件中的類別進行存取，而 `private protected` 則限制在相同組件中宣告的衍生類型進行存取。

如需詳細資訊，請參閱語言參考中的[存取修飾詞](../language-reference/keywords/access-modifiers.md)。

## <a name="conditional-ref-expressions"></a>`ref` 條件運算式

最後，條件運算式可能會產生參考結果，而不是實值結果。 例如，您可以撰寫下列程式碼，在兩個陣列的其中一個上，擷取對第一個元素的參考：

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

變數 `r` 是 `arr` 或 `otherArr` 中對第一個值的參考。

如需詳細資訊，請參閱語言參考中的[條件運算子 (?:)](../language-reference/operators/conditional-operator.md)。
