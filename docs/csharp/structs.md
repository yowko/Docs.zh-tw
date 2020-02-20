---
title: 結構 - C# 手冊
description: 了解結構類型和其建立方式
ms.date: 10/12/2016
ms.technology: csharp-fundamentals
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: 540742ea6a215e09f0cc31b218ac10fbf6192352
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503986"
---
# <a name="structs"></a>結構

*struct* 是實值型別。 建立結構時，指派結構的變數會保留結構的實際資料。 將結構指派至新的變數時，將會複製結構。 因此，新的變數和原始變數會各自包含一份相同的資料。 針對其中一個複本所做的變更，並不會影響到另一個複本。

實值型別變數會直接包含其值，這表示配置的記憶體內嵌在宣告該變數的內容中。 實值型別變數不會有任何個別的堆積配置或記憶體回收額外負荷。

實值型別有兩種類別︰[struct](language-reference/keywords/struct.md) 和 [enum](language-reference/builtin-types/enum.md)。

內建的數字類型為結構，而您可以存取其屬性和方法︰

[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]

但您會將它們當作簡單的非彙總類型來宣告並將值指派給它們︰

[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)]

實值型別為 *sealed*，其表示您無法從 <xref:System.Int32> 衍生類型，也無法定義從任何使用者定義的類別或結構繼承的結構，因為結構只能從 <xref:System.ValueType> 繼承。 不過，結構可以實作一或多個介面。 您可以將結構類型轉型為介面類型；這會導致 *boxing* 作業將結構包裝在 Managed 堆積上的參考型別物件內。 當您將實值型別傳遞至會將 <xref:System.Object> 作為輸入參數的方法時，就會進行 Boxing 作業。 如需詳細資訊，請參閱 [Boxing 和 Unboxing](./programming-guide/types/boxing-and-unboxing.md )。

您使用 [struct](./language-reference/keywords/struct.md) 關鍵字來建立您自己自訂的實值型別。 一般來說，會使用結構作為一小組相關變數的容器，如下列範例所示︰

[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]

如需 .NET Framework 中實值型別的詳細資訊，請參閱[一般型別系統](../standard/common-type-system.md)。

結構與類別共用大部分相同的語法，不過結構的限制高於類別︰

- 在結構宣告內，除非欄位宣告為 `const` 或 `static`，否則無法初始化欄位。

- 結構無法宣告無參數建構函式 (不含參數的建構函式) 或完成項。

- 指派時會複製結構。 將結構指派給新的變數時，會複製所有資料，而且對新複本進行的任何修改都不會變更原始複本的資料。 使用實值型別集合 (例如 Dictionary<string, myStruct>) 時，請一定要記住這一點。

- 結構是實值型別，而類別是參考型別。

- 不同於類別，結構不需要使用 `new` 運算子就能具現化。

- 結構可以宣告具有參數的建構函式。

- 結構無法繼承自另一個結構或類別，而且不能作為類別的基底。 所有結構都直接繼承自 <xref:System.ValueType>，該項則繼承自 <xref:System.Object>。

- 結構（例如類別）可以執行介面。

## <a name="nullable-value-types"></a>可為 Null 的實值型別

一般實值型別的值不能為 [null](language-reference/keywords/null.md)。 不過，您可以在該型別後面添加 `?`，建立可為 null 的實值型別。 例如，`int?` 就是也能有 `int`null[ 值的 ](./language-reference/keywords/null.md) 型別。 可為 null 的實數值型別是 <xref:System.Nullable%601>泛型結構類型的實例。 可為 null 的實值型別在您將資料傳遞至資料庫，且其中的數值可能為 null 或未定義時，特別有用。 如需詳細資訊，請參閱[可為 null 的實數值型別](language-reference/builtin-types/nullable-value-types.md)。

## <a name="see-also"></a>另請參閱

- [類別](programming-guide/classes-and-structs/classes.md)
- [基本類型](basic-types.md)
