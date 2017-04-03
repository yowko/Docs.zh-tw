---
title: "double (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- double
- double_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
caps.latest.revision: 26
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ccdd29c78a3cdc9d32fa08b1be94eecd717418fc
ms.lasthandoff: 03/13/2017

---
# <a name="double-c-reference"></a>double (C# 參考)
`double` 關鍵字表示儲存 64 位元浮點值的簡單類型。 下表顯示 `double` 類型的精確度和大概範圍。  
  
|類型|大概範圍|精確度|.NET Framework 類型|  
|----------|-----------------------|---------------|-------------------------|  
|`double`|±5.0 × 10<sup>−324</sup> 至 ±1.7 × 10<sup>308</sup>|15-16 位數|<xref:System.Double?displayProperty=fullName>|  
  
## <a name="literals"></a>常值  
 根據預設，指派運算子右邊的實數常值會視為 `double`。 不過，如果您希望整數被視為 `double`，請使用後置字元 d 或 D，例如︰  
  
```  
  
double x = 3D;  
```  
  
## <a name="conversions"></a>轉換  
 您可以在一個運算式中混合使用數值整數型別和浮點類型。 在此情況下，整數型別會轉換成浮點類型。 運算式的評估會根據下列規則來執行：  
  
-   如果其中一個浮點類型是 `double`，則運算式會評估為 `double` 或 [bool](../../../csharp/language-reference/keywords/bool.md) (在關聯或布林運算式中)。  
  
-   運算式中沒有 `double` 類型，它會評估為 [float](../../../csharp/language-reference/keywords/float.md) 或 [bool](../../../csharp/language-reference/keywords/bool.md) (在關聯或布林運算式中)。  
  
 浮點運算式可以包含下列值的集合：  
  
-   正零和負零。  
  
-   正無限大和負無限大。  
  
-   非數字值 (NaN)。  
  
-   非零值的有限集合。  
  
 如需這些值的詳細資訊，請參閱 [IEEE](http://go.microsoft.com/fwlink/?LinkId=26269) 網站上的 IEEE Standard for Binary Floating-Point Arithmetic。  
  
## <a name="example"></a>範例  
 在下例中，一起新增 [int](../../../csharp/language-reference/keywords/int.md)、[short](../../../csharp/language-reference/keywords/short.md)、[float](../../../csharp/language-reference/keywords/float.md) 和 `double` 以得到 `double` 結果。  
  
 [!code-cs[csrefKeywordsTypes#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/double_1.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [預設值表](../../../csharp/language-reference/keywords/default-values-table.md)   
 [內建類型表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [浮點類型表](../../../csharp/language-reference/keywords/floating-point-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
