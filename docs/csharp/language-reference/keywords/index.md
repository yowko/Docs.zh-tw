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
ms.openlocfilehash: 928917d25b5f3f97c4b8cdff85efdaa1957be41e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399312"
---
# <a name="c-keywords"></a>C# 關鍵字

關鍵字是預先定義的保留識別項，它對編譯器具有特殊意義。 您必須在關鍵字加上 `@` 做為前置詞，才能將它們當做程式中的識別項使用。 例如，`@if` 是有效的識別項，但 `if` 不是，因為 `if` 是關鍵字。  
  
 本主題中的第一個表格列出在 C# 程式的任何部分中為保留識別項的關鍵字。 本主題中的第二個表格列出 C# 中的內容關鍵字。 內容關鍵字只在有限的程式內容中具有特殊意義，並且可在該內容以外的地方用來當做識別項。 一般而言，將新的關鍵字加入至 C# 語言時，會以內容關鍵字加入它們，以避免中斷利用舊版本撰寫的程式。  
  
|||||  
|---|---|---|---|  
|[抽象](abstract.md)|[作為](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[Bool](../builtin-types/bool.md)|  
|[打破](break.md)|[位元組](../builtin-types/integral-numeric-types.md)|[案例](switch.md)|[catch](try-catch.md)|  
|[字元](../builtin-types/char.md)|[已選取](checked.md)|[class](class.md)|[const](const.md)|  
|[繼續](continue.md)|[十進位](../builtin-types/floating-point-numeric-types.md)|[預設](default.md)|[委託](../builtin-types/reference-types.md)|  
|[做](do.md)|[雙](../builtin-types/floating-point-numeric-types.md)|[還](if-else.md)|[枚舉](../builtin-types/enum.md)|  
|[event](event.md)|[明確](../operators/user-defined-conversion-operators.md)|[Extern](extern.md)|[false](../builtin-types/bool.md)|  
|[最後](try-finally.md)|[fixed](fixed-statement.md)|[浮動](../builtin-types/floating-point-numeric-types.md)|[對於](for.md)|  
|[Foreach](foreach-in.md)|[去](goto.md)|[如果](if-else.md)|[隱 式](../operators/user-defined-conversion-operators.md)|  
|[在](in.md)|[Int](../builtin-types/integral-numeric-types.md)|[介面](interface.md)|[內部](internal.md)|
|[是](is.md)|[鎖定](lock-statement.md)|[長](../builtin-types/integral-numeric-types.md)|[Namespace](namespace.md)|
|[新增功能](../operators/new-operator.md)|[空](null.md)|[物件](../builtin-types/reference-types.md)|[運算元](../operators/operator-overloading.md)|
|[出](out.md)|[覆蓋](override.md)|[Params](params.md)|[私人](private.md)|
|[保護](protected.md)|[public](public.md)|[唯讀](readonly.md)|[ref](ref.md)|
|[返回](return.md)|[sbyte](../builtin-types/integral-numeric-types.md)|[密封](sealed.md)|[short](../builtin-types/integral-numeric-types.md)||
[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[靜態](static.md)|[字串](../builtin-types/reference-types.md)|
|[struct](../builtin-types/struct.md)|[開關](switch.md)|[這](this.md)|[扔](throw.md)|
|[true](../builtin-types/bool.md)|[嘗試](try-catch.md)|[類型](../operators/type-testing-and-cast.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[取消選取](unchecked.md)|[安全](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[使用](using.md)|[使用靜態](using-static.md)|[虛擬](virtual.md)|[無效](../builtin-types/void.md)|
|[揮發 性](volatile.md)|[而](while.md)|

## <a name="contextual-keywords"></a>內容關鍵字

 內容關鍵字可用來在程式碼中提供特定的意義，但它不是 C# 中的保留字。 某些內容關鍵字 (例如 `partial` 和 `where`) 在兩個以上的內容中具有特殊意義。  
  
||||  
|---|---|---|  
|[新增](add.md)|[別名](extern-alias.md)|[上升](ascending.md)|
|[async](async.md)|[等待](../operators/await.md)|[由](by.md)|
|[降](descending.md)|[動態](../builtin-types/reference-types.md)|[等於](equals.md)|
|[從](from-clause.md)|[get](get.md)|[全球](../operators/namespace-alias-qualifier.md)|
|[群組](group-clause.md)|[into](into.md)|[加入](join-clause.md)|
|[讓](let-clause.md)|[nameof](../operators/nameof.md)|[上](on.md)|
|[orderby](orderby-clause.md)|[partial (型別)](partial-type.md)|[partial (方法)](partial-method.md)|
|[移除](remove.md)|[選擇](select-clause.md)|[設置](set.md)|
|[非託管（泛型型別約束）](where-generic-type-constraint.md)|[值](value.md)|[無 功](var.md)|
|[when (篩選條件)](when.md)|[where (泛型型別條件約束)](where-generic-type-constraint.md)|[where (查詢子句)](where-clause.md)|
|[yield](yield.md)| | |
  
## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
