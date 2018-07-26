---
title: 可為 Null 的類型 (C# 程式設計手冊)
ms.date: 05/15/2017
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: 64b326b82cd022ed6590a232546690e2ec2a5c78
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245582"
---
# <a name="nullable-types-c-programming-guide"></a>可為 Null 的類型 (C# 程式設計手冊)
可為 Null 的型別是 <xref:System.Nullable%601?displayProperty=nameWithType> 結構的執行個體。 可為 Null 的型別可以代表其基礎值型別的正確值範圍，再加上額外的 `null` 值。 例如，您可以將範圍從 -2147483648 到 2147483647 的任何值指派給 `Nullable<Int32>` (發音為「Nullable of Int32」)，或為它指派 `null` 值。 您可以為 `Nullable<bool>` 指派下列值：[true](../../../csharp/language-reference/keywords/true.md)、[false](../../../csharp/language-reference/keywords/false.md) 或 [null](../../../csharp/language-reference/keywords/null.md)。 當您正在處理包含可能不會指派值之元素的資料庫和其他資料型別時，將 `null` 指派為數字或布林值型別的功能特別有用。 例如，資料庫中的布林值欄位可以儲存 `true` 或 `false` 的值，而它也可能是未定義的。 
  
[!code-csharp[nullable-types](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]  
  
如需詳細資訊，請參閱[使用可為 Null 的型別](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
## <a name="nullable-types-overview"></a>可為 Null 的型別概觀  
 可為 Null 的型別特色如下：  
  
-   可為 Null 的型別代表可指派 `null` 值的實值型別變數。 您無法根據參考型別建立可為 Null 的型別。 (參考型別已經支援 `null` 值)。  
  
-   語法 `T?` 是 <xref:System.Nullable%601> 的縮寫，其中 `T` 是實值型別。 這兩種格式是可互換的。  
  
-   將值指派給可為 Null 的型別，就像您針對一般實值型別所做的一樣，例如 `int? x = 10;` 或 `double? d = 4.108;`。 您也可以為可為 Null 的型別指派值 `null`：`int? x = null;`。  
  
-   使用 <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> 方法來傳回指派的值，或者，如果值為 `null`，則傳回基礎類型的預設值，例如 `int j = x.GetValueOrDefault();`  
  
-   使用 <xref:System.Nullable%601.HasValue%2A> 和 <xref:System.Nullable%601.Value%2A> 唯讀屬性，以測試是否有 Null 並擷取值，如下列範例所示：`if(x.HasValue) j = x.Value;`  
  
    -   如果變數包含值，`HasValue` 屬性就會傳回 `true`，或者，如果它是 `null`，則會傳回 `false`。  
  
    -   如果指派了其中一個，則 `Value` 屬性會傳回值。 否則會擲回 <xref:System.InvalidOperationException?displayProperty=nameWithType>。  
  
    -   `HasValue` 的預設值為 `false`。 `Value` 屬性沒有預設值。  
  
    -   您也可以使用 `==` 和 `!=` 運算子搭配可為 Null 的型別，如下列範例所示︰`if (x != null) y = x;`  
  
-   使用 `??` 運算子來指派預設值，在將目前值為 `null` 之可為 Null 的型別指派給非可為 Null 的型別時，將會套用此預設值，例如 `int? x = null; int y = x ?? -1;`  
  
-   不允許巢狀可為 Null 的型別。 系統將不會編譯下列這一行：`Nullable<Nullable<int>> n;`  
  
## <a name="related-sections"></a>相關章節  
 如需詳細資訊：  
  
-   [使用可為 Null 的型別](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [對可為 Null 的型別進行 boxing](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [??運算子](../../../csharp/language-reference/operators/null-coalescing-operator.md)  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Nullable>  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C#](../../../csharp/index.md)  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [「增益」(Lift) 的真正意義是什麼？(英文)](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
