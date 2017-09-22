---
title: "明確數值轉換表 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0315810522be319a6bb565c99e1c8f7d1ba4701b
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="explicit-numeric-conversions-table-c-reference"></a>明確數值轉換表 (C# 參考)
明確數值轉換是使用 cast 運算式，用來將任何數值類型轉換成任何其他數值類型，沒有任何隱含的轉換。 下表顯示這些轉換。  
  
 如需這些轉換的詳細資訊，請參閱[轉換和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)。  
  
|從|以|  
|----------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`byte`、`ushort`、`uint`、`ulong` 或 `char`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`Sbyte` 或 `char`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`sbyte`、`byte`、`ushort`、`uint`、`ulong` 或 `char`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`sbyte`、`byte`、`short` 或 `char`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`sbyte`、`byte`、`short`、`ushort`、`uint`、`ulong` 或 `char`。|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`sbyte`、`byte`、`short`、`ushort`、`int` 或 `char`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`ulong` 或 `char`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long` 或 `char`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`sbyte`、`byte` 或 `short`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char` 或 `decimal`。|  
|[double](../../../csharp/language-reference/keywords/double.md)|`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float` 或 `decimal`。|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float` 或 `double`。|  
  
## <a name="remarks"></a>備註  
  
-   明確的數值轉換可能會造成有效位數遺失或導致擲回例外狀況。  
  
-   當您將 `decimal` 值轉換為整數型別時，這個值會捨入到最接近整數值的零。 如果產生的整數值超出目的地類型的範圍，就會擲回 <xref:System.OverflowException>。  
  
-   從 `double` 或 `float` 值轉換為整數型別時，值會被截斷。 如果產生的整數值超出目的地類型的範圍，結果隨溢位檢查內容而異。 在已檢查的內容中會擲回 `OverflowException`，而在未經檢查的內容中，結果是目的地類型的未指定值。  
  
-   當您將 `double` 轉換成 `float` 時，`double` 值會捨入到最接近 `float` 值。 如果 `double` 值太小或太大以致不符合目的地類型，結果會是零或無限大。  
  
-   當您將 `float` 或 `double` 轉換成 `decimal` 時，來源值會轉換成 `decimal` 表示，必要時捨入到最接近第 28 個小數位數後的數字。 視來源值的值而定，可能會發生下列一種結果：  
  
    -   如果來源值太小無法以 `decimal` 表示，結果就會變成零。  
  
    -   如果來源值是 NaN (不是數字)、無限大或太大，無法以 `decimal` 表示，就會擲回 `OverflowException`。  
  
-   當您將 `decimal` 轉換成 `float` 或 `double` 時，`decimal` 值會捨入到最接近 `double` 或 `float` 值。  
  
 如需明確轉換的詳細資訊，請參閱＜C# 語言規格＞中的＜明確＞。 如需如何存取規格的詳細資訊，請參閱 [C# 語言規格](../../../csharp/language-reference/language-specification/index.md)。  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [轉型和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [() 運算子](../../../csharp/language-reference/operators/invocation-operator.md)   
 [整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建型別表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)

