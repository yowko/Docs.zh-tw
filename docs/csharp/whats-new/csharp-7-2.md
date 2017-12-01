---
title: "在 C# 7.2 最新消息"
description: "7.2 C# 中的新功能的概觀。"
keywords: "C# 語言設計中，7.2，Visual Studio 2017，"
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: a580a4a3a0a49e97ea8fb96699d1d978a9bc0a64
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="whats-new-in-c-72"></a>在 C# 7.2 最新消息

C# 7.2 是另一個點發行，加入一些有用的功能。
這一版的一個佈景主題使用更有效率地實值類型，避免不必要的複本或配置。 

其餘的功能會很小，很好的功能。

使用 C# 7.2[語言版本選擇](csharp-7-1.md#language-version-selection)選取編譯器語言版本的組態項目。

在此版本中的新語言功能包括：

* [具有實值類型的參考語意](#reference-semantics-with-value-types)
  - 啟用使用參考語意的實值類型使用的語法改進項目組合。
* [非尾端的具名引數](#non-trailing-named-arguments)
  - 具名引數後面可以接著位置引數。
* [數值常值中的前置底線](#leading-underscores-in-numeric-literals)
  - 數值常值現在可以有任何列印的數字之前的前置底線。
* [`private protected`存取修飾詞](#private-protected)
  - `private protected`存取修飾詞可讓您在相同的組件中的衍生類別的存取。

## <a name="reference-semantics-with-value-types"></a>具有實值類型的參考語意

7.2 中導入的語言功能可讓您使用實值型別時使用的參考語意。 它們被設計來提升效能，請將複製的實值類型而不會產生與使用參考類型相關聯的記憶體配置降到最低。 此功能包含：

 - `in`修飾詞來指定引數是傳址方式傳遞，但不是能修改以呼叫之方法的參數。
 - `ref readonly`方法傳回時，以指出方法傳址方式傳回其值，但不允許寫入該物件上的修飾詞。
 - `readonly struct`宣告，以表示結構是不變，而且會傳遞做為`in`其成員方法的參數。
 - `ref struct`宣告，以指出結構類型會直接存取受管理的記憶體，且必須一律堆疊配置。

您可以閱讀更多個需所有這些變更中[使用實值型別參考語意](../reference-semantics-with-value-types.md)。

## <a name="non-trailing-named-arguments"></a>非尾端的具名引數

方法會呼叫現在可以使用具名引數前面位置引數，這些具名引數時在正確的位置。 如需詳細資訊，請參閱[具名和選擇性引數](../programming-guide/classes-and-structs/named-and-optional-arguments.md)。

## <a name="leading-underscores-in-numeric-literals"></a>數值常值中的前置底線

不允許對 C# 7.0 中的數字分隔符號的支援實作`_`是常值的第一個字元。 十六進位和二進位的數值常值可能會立即開始使用`_`。 

例如: 

```csharp
int binaryValue = 0b_0101_0101;
```

## `private protected`

最後，為新複合的存取修飾詞：`private protected`表示可能會由相同組件中宣告的衍生類別中存取成員。 雖然`protected internal`可讓您存取由衍生的類別或類別，可位於相同的組件，`private protected`限制存取相同組件中宣告的衍生類型。

如需詳細資訊，請參閱[存取修飾詞](../language-reference/keywords/access-modifiers.md)語言參考中。
