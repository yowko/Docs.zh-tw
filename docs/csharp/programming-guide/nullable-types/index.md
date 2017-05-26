---
title: "可為 Null 的型別 (C# 程式設計指南) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
caps.latest.revision: 44
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 75726b9864abc0c9b556085e5215c6692d80fb12
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="nullable-types-c-programming-guide"></a>可為 Null 的類型 (C# 程式設計手冊)
可為 Null 的型別是 <xref:System.Nullable%601?displayProperty=fullName> 結構的執行個體。 可為 Null 的型別可以代表其基礎值型別的正確值範圍，再加上額外的 `null` 值。 例如，您可以將範圍從 -2147483648 到 2147483647 的任何值指派給 `Nullable<Int32>` (發音為「Nullable of Int32」)，或為它指派 `null` 值。 您可以為 `Nullable<bool>` 指派下列值：[true](../../../csharp/language-reference/keywords/true.md)、[false](../../../csharp/language-reference/keywords/false.md) 或 [null](../../../csharp/language-reference/keywords/null.md)。 當您正在處理包含可能不會指派值之元素的資料庫和其他資料型別時，將 `null` 指派為數字或布林值型別的功能特別有用。 例如，資料庫中的布林值欄位可以儲存 `true` 或 `false` 的值，而它也可能是未定義的。  
  
 [!code-cs[csProgGuideTypes#3](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_1.cs)]  
  
 此範例將顯示下列輸出：  
  
 `num = Null`  
  
 `Nullable object must have a value.`  
  
 如需詳細資訊，請參閱[使用可為 Null 的型別](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
## <a name="nullable-types-overview"></a>可為 Null 的型別概觀  
 可為 Null 的型別特色如下：  
  
-   可為 Null 的型別代表可指派 `null` 值的實值型別變數。 您無法根據參考型別建立可為 Null 的型別。 (參考型別已經支援 `null` 值)。  
  
-   語法 `T?` 是 <xref:System.Nullable%601> 的縮寫，其中 `T` 是實值型別。 這兩種格式是可互換的。  
  
-   將值指派給可為 Null 的型別，就像您針對一般實值型別所做的一樣，例如 `int? x = 10;` 或 `double? d = 4.108`。 您也可以為可為 Null 的型別指派值 `null`: `int? x = null.`  
  
-   使用 <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> 方法來傳回指定的值，或者，如果值為 `null`，則傳回基礎型別的預設值，例如 `int j = x.GetValueOrDefault();`  
  
-   使用 <xref:System.Nullable%601.HasValue%2A> 和 <xref:System.Nullable%601.Value%2A> 唯讀屬性來測試是否為 Null 並擷取值，如下列範例所示︰`if(x.HasValue) j = x.Value;`  
  
    -   如果變數包含值，`HasValue` 屬性就會傳回 `true`，或者，如果它是 `null`，則會傳回 `false`。  
  
    -   如果指派了其中一個，則 `Value` 屬性會傳回值。 否則，會擲回 <xref:System.InvalidOperationException?displayProperty=fullName>。  
  
    -   `HasValue` 的預設值為 `false`。 `Value` 屬性沒有預設值。  
  
    -   您也可以使用 `==` 和 `!=` 運算子搭配可為 Null 的型別，如下列範例所示︰`if (x != null) y = x;`  
  
-   使用 `??` 運算子來指派預設值，在將目前值為 `null` 之可為 Null 的型別指派給非可為 Null 的型別時，將會套用此預設值，例如 `int? x = null; int y = x ?? -1;`  
  
-   不允許巢狀可為 Null 的型別。 系統將不會編譯下列這一行：`Nullable<Nullable<int>> n;`  
  
## <a name="related-sections"></a>相關章節  
 如需詳細資訊：  
  
-   [使用可為 Null 的型別](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [對可為 Null 的型別進行 boxing](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [??運算子](../../../csharp/language-reference/operators/null-conditional-operator.md)  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Nullable>   
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)   
 [C#](../../../csharp/csharp.md)   
 [C# 參考](../../../csharp/language-reference/index.md)   
 [「增益」(Lift) 的真正意義是什麼？(英文)](http://go.microsoft.com/fwlink/?LinkId=112382)

