---
title: "C# 7.2 的新功能"
description: "C# 7.2 新功能的概觀。"
keywords: "C# 語言設計, 7.2, Visual Studio 2017,"
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: cc861f186bea681bb32a2f8041a7155026679987
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2017
---
# <a name="whats-new-in-c-72"></a>C# 7.2 的新功能

C# 7.2 是另一個小數點版本，其中新增了一些實用的功能。
此版本的主題之一是能夠避免不必要的複製或配置，讓實質型別作業能夠更有效率。 

其餘功能則無足輕重。

C# 7.2 使用了[語言版本選取項目](csharp-7-1.md#language-version-selection)組態元素來選取編譯器語言版本。

此版本的新款語言功能包括：

* [具備實值型別的參考語意](#reference-semantics-with-value-types)
  - 此為語法改進功能組合，其可讓使用參考語意進行實質型別作業變得可能。
* [無後置具名引數](#non-trailing-named-arguments)
  - 具名引數之後可以接著位置引數。
* [數值常值中的前置底線](#leading-underscores-in-numeric-literals)
  - 數值常值的任何列印數字之前，現都可加上前置底線。
* [`private protected` 存取修飾詞](#private-protected)
  - 您可利用 `private protected` 存取修飾詞，存取相同組件中的衍生類別。

## <a name="reference-semantics-with-value-types"></a>具備實值型別的參考語意

您可利用 7.2 版新加入的語言功能，於使用參考語意時運用實值型別。 這些功能之設計目的是加強加效能，方法是將複製實質型別最小化，而不產生與使用參考型別相關的記憶體配置。 功能包括：

 - 參數上的 `in` 修飾詞，可指定引數將以傳址方式傳遞，但不受呼叫的方法修改。
 - 方法上 `ref readonly` 修飾詞的傳回內容，可指示方法要以傳址方式傳回其值，但不允許寫入該物件。
 - `readonly struct` 宣告，可指示結構會固定，且應以 `in` 參數傳遞至其成員方法。
 - `ref struct` 宣告，可指示結構類型會直接存取受控記憶體，且一律會配置堆疊。

您可以在[使用具備參考語意的實值型別](../reference-semantics-with-value-types.md)中閱讀到這些變更的詳細內容。

## <a name="non-trailing-named-arguments"></a>無後置具名引數

當具名引數位於正確位置時，方法呼叫現在可以在位置引數前面使用具名引數。 如需詳細資訊，請參閱[具名和選擇性引數](../programming-guide/classes-and-structs/named-and-optional-arguments.md)。

## <a name="leading-underscores-in-numeric-literals"></a>數值常值中的前置底線

C# 7.0 中的數字分隔符號之實作支援，並不允許將 `_` 作為常值的第一個字元。 十六進位與二進位數值常值現在可以使用 `_` 開頭。 

例如: 

```csharp
int binaryValue = 0b_0101_0101;
```

## `private protected`

最後是新的複合存取修飾詞：`private protected` 可指示包含類別或相同組件中的衍生類別，皆可存取成員。 `protected internal` 允許衍生類別或相同組件中的類別進行存取，而 `private protected` 則限制在相同組件中宣告的衍生類型進行存取。

如需詳細資訊，請參閱語言參考中的[存取修飾詞](../language-reference/keywords/access-modifiers.md)。
