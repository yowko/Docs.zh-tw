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
ms.assetid: e929b0f2-4b92-4d37-8060-23d323b098ad
ms.openlocfilehash: 251046a8bd825a90d817965f9f747d08d4492197
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102030"
---
# <a name="c-keywords"></a>C# 關鍵字

關鍵字是預先定義的保留識別項，它對編譯器具有特殊意義。 您必須在關鍵字加上 `@` 做為前置詞，才能將它們當做程式中的識別項使用。 例如，`@if` 是有效的識別項，但 `if` 不是，因為 `if` 是關鍵字。  
  
 本主題中的第一個表格列出在 C# 程式的任何部分中為保留識別項的關鍵字。 本主題中的第二個表格列出 C# 中的內容關鍵字。 內容關鍵字只在有限的程式內容中具有特殊意義，並且可在該內容以外的地方用來當做識別項。 一般而言，將新的關鍵字加入至 C# 語言時，會以內容關鍵字加入它們，以避免中斷利用舊版本撰寫的程式。  
  
|||||  
|---|---|---|---|  
|[抽象](abstract.md)|[作為](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](../builtin-types/bool.md)|  
|[break](break.md)|[byte](../builtin-types/integral-numeric-types.md)|[情況 下](switch.md)|[catch](try-catch.md)|  
|[char](../builtin-types/char.md)|[檢查](checked.md)|[class](class.md)|[const](const.md)|  
|[繼續](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[預設](default.md)|[委託](../builtin-types/reference-types.md)|  
|[do](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[else](if-else.md)|[列舉](../builtin-types/enum.md)|  
|[event](event.md)|[明確](../operators/user-defined-conversion-operators.md)|[extern](extern.md)|[false](../builtin-types/bool.md)|  
|[最後](try-finally.md)|[固定](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[for](for.md)|  
|[Foreach](foreach-in.md)|[goto](goto.md)|[if](if-else.md)|[隱式](../operators/user-defined-conversion-operators.md)|  
|[in](in.md)|[int](../builtin-types/integral-numeric-types.md)|[介面](interface.md)|[internal](internal.md)|
|[is](is.md)|[鎖定](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[網路中](namespace.md)|
|[新增功能](../operators/new-operator.md)|[null](null.md)|[物件](../builtin-types/reference-types.md)|[算子](../operators/operator-overloading.md)|
|[出](out.md)|[override](override.md)|[params](params.md)|[private](private.md)|
|[protected](protected.md)|[public](public.md)|[唯讀](readonly.md)|[ref](ref.md)|
|[return](return.md)|[sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[string](../builtin-types/reference-types.md)|
|[struct](../builtin-types/struct.md)|[switch](switch.md)|[this](this.md)|[throw](throw.md)|
|[true](../builtin-types/bool.md)|[嘗試](try-catch.md)|[類型](../operators/type-testing-and-cast.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[安全](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[使用](using.md)|[virtual](virtual.md)|[void](../builtin-types/void.md)|[volatile](volatile.md)|
|[while](while.md)|

## <a name="contextual-keywords"></a>內容關鍵字

 內容關鍵字可用來在程式碼中提供特定的意義，但它不是 C# 中的保留字。 某些內容關鍵字 (例如 `partial` 和 `where`) 在兩個以上的內容中具有特殊意義。  
  
||||  
|---|---|---|  
|[新增](add.md)|[別名](extern-alias.md)|[ascending](ascending.md)|
|[async](async.md)|[等待](../operators/await.md)|[by](by.md)|
|[descending](descending.md)|[動態](../builtin-types/reference-types.md)|[equals](equals.md)|
|[from](from-clause.md)|[get](get.md)|[全球](../operators/namespace-alias-qualifier.md)|
|[群組](group-clause.md)|[into](into.md)|[加入](join-clause.md)|
|[讓](let-clause.md)|[nameof](../operators/nameof.md)|[上](on.md)|
|[順序](orderby-clause.md)|[部份(類型)](partial-type.md)|[部分(方法)](partial-method.md)|
|[移除](remove.md)|[選擇](select-clause.md)|[設定](set.md)|
|[非託管 (泛型類型約束)](where-generic-type-constraint.md)|[value](value.md)|[var](var.md)|
|[when (篩選條件)](when.md)|[where (泛型型別條件約束)](where-generic-type-constraint.md)|[where (查詢子句)](where-clause.md)|
|[yield](yield.md)| | |
  
## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
