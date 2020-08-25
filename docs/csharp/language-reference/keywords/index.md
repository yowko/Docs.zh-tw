---
title: C# 關鍵字
ms.date: 03/07/2017
f1_keywords:
- cs.keywords
helpviewer_keywords:
- keywords [C#]
- C# language, keywords
- Visual C#, keywords
- '@ keyword'
ms.custom: updateeachrelease
ms.assetid: e929b0f2-4b92-4d37-8060-23d323b098ad
ms.openlocfilehash: 3392b92cbd77e5b3f895af99a71f33d2ab43fa15
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812311"
---
# <a name="c-keywords"></a>C# 關鍵字

關鍵字是預先定義的保留識別項，它對編譯器具有特殊意義。 您必須在關鍵字加上 `@` 做為前置詞，才能將它們當做程式中的識別項使用。 例如，`@if` 是有效的識別項，但 `if` 不是，因為 `if` 是關鍵字。  
  
 本主題中的第一個表格列出在 C# 程式的任何部分中為保留識別項的關鍵字。 本主題中的第二個表格列出 C# 中的內容關鍵字。 內容關鍵字只在有限的程式內容中具有特殊意義，並且可在該內容以外的地方用來當做識別項。 一般而言，將新的關鍵字加入至 C# 語言時，會以內容關鍵字加入它們，以避免中斷利用舊版本撰寫的程式。  
  
|||||  
|---|---|---|---|  
|[抽象](abstract.md)|[按照](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](../builtin-types/bool.md)|  
|[break](break.md)|[byte](../builtin-types/integral-numeric-types.md)|[情況 下](switch.md)|[catch](try-catch.md)|  
|[char](../builtin-types/char.md)|[檢查](checked.md)|[class](class.md)|[const](const.md)|  
|[繼續](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[預設值](default.md)|[delegate](../builtin-types/reference-types.md)|  
|[do](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[else](if-else.md)|[枚舉](../builtin-types/enum.md)|  
|[event](event.md)|[明確](../operators/user-defined-conversion-operators.md)|[extern](extern.md)|[false](../builtin-types/bool.md)|  
|[最後](try-finally.md)|[固定](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[for](for.md)|  
|[foreach](foreach-in.md)|[goto](goto.md)|[if](if-else.md)|[隱 式](../operators/user-defined-conversion-operators.md)|  
|[in](in.md)|[int](../builtin-types/integral-numeric-types.md)|[interface](interface.md)|[internal](internal.md)|
|[是](is.md)|[鎖](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[命名 空間](namespace.md)|
|[新增功能](../operators/new-operator.md)|[null](null.md)|[object](../builtin-types/reference-types.md)|[operator](../operators/operator-overloading.md)|
|[擴展](out.md)|[override](override.md)|[params](params.md)|[私人](private.md)|
|[protected](protected.md)|[public](public.md)|[readonly](readonly.md)|[裁判](ref.md)|
|[返回](return.md)|[sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[string](../builtin-types/reference-types.md)|
|[結構](../builtin-types/struct.md)|[switch](switch.md)|[this](this.md)|[扔](throw.md)|
|[true](../builtin-types/bool.md)|[嘗試](try-catch.md)|[typeof](../operators/type-testing-and-cast.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[安全](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[使用](using.md)|[virtual](virtual.md)|[void](../builtin-types/void.md)|[volatile](volatile.md)|
|[而](while.md)|

## <a name="contextual-keywords"></a>內容關鍵字

 內容關鍵字可用來在程式碼中提供特定的意義，但它不是 C# 中的保留字。 某些內容關鍵字 (例如 `partial` 和 `where`) 在兩個以上的內容中具有特殊意義。  
  
||||  
|---|---|---|  
|[add](add.md)|[alias](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[await](../operators/await.md)|[逐](by.md)|
|[descending](descending.md)|[動態](../builtin-types/reference-types.md)|[equals](equals.md)|
|[from](from-clause.md)|[get](get.md)|[全球](../operators/namespace-alias-qualifier.md)|
|[群組](group-clause.md)|[into](into.md)|[join](join-clause.md)|
|[讓](let-clause.md)|[nameof](../operators/nameof.md)|[notnull](../../programming-guide/generics/constraints-on-type-parameters.md#notnull-constraint)|
|[on](on.md)|[orderby](orderby-clause.md)|[部分 (類型) ](partial-type.md)|
|[部分 (方法) ](partial-method.md)|[remove](remove.md)|[select](select-clause.md)|
|[set](set.md)|[非受控 (泛型型別條件約束) ](where-generic-type-constraint.md)|[value](value.md)|
|[無 功](var.md)|[when (篩選條件)](when.md)|[where (泛型型別條件約束)](where-generic-type-constraint.md)|
|[where (查詢子句)](where-clause.md)|[yield](yield.md)| |
  
## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
