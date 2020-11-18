---
title: 運算子多載
ms.date: 10/22/2008
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 40e1c6a4a65bfc20c94223e4012e34928b25a2ab
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830034"
---
# <a name="operator-overloads"></a>運算子多載
運算子多載可讓架構類型顯示為內建的語言基本類型。

 雖然在某些情況下允許且很有用，但應該謹慎使用運算子多載。 在許多情況下，運算子多載已被濫用，例如，當架構設計工具開始使用運算子進行應該是簡單方法的作業時。 下列指導方針可協助您決定何時及如何使用運算子多載。

 ❌ 請避免定義運算子多載，但應該類似基本 (內建) 類型的類型除外。

 ✔️考慮定義型別中的運算子多載，而該型別應該會像基本型別一樣。

 例如， <xref:System.String?displayProperty=nameWithType> 具有 `operator==` 和已 `operator!=` 定義。

 ✔️在代表數位 (的結構中定義運算子多載，例如 <xref:System.Decimal?displayProperty=nameWithType>) 。

 ❌ 在定義運算子多載時，請勿刻意進行。

 運算子多載很有用，因為在這種情況下，作業的結果將會立即被察覺。 例如，您可以從另一個減去另一個， <xref:System.DateTime> `DateTime` 然後取得 <xref:System.TimeSpan> 。 但是，不適合使用邏輯 union 運算子來 union 兩個資料庫查詢，或使用 shift 運算子來寫入資料流程。

 ❌ 除非至少有一個運算元的類型是定義多載，否則請勿提供運算子多載。

 ✔️以對稱方式進行多載運算子。

 例如，如果您多載 `operator==` ，您也應該多載 `operator!=` 。 同樣地，如果您多載 `operator<` ，您也應該多載 `operator>` ，依此類推。

 ✔️考慮提供具有易記名稱的方法，這些方法會對應至每個多載的運算子。

 許多語言不支援運算子多載。 基於這個理由，建議多載運算子的型別包含具有適當特定網功能變數名稱稱的次要方法，以提供對等的功能。

 下表包含運算子清單和對應的易記方法名稱。

|C # 運算子符號|中繼資料名稱|易記名稱|
|-------------------------|-------------------|-------------------|
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|
|`+ (binary)`|`op_Addition`|`Add`|
|`- (binary)`|`op_Subtraction`|`Subtract`|
|`* (binary)`|`op_Multiply`|`Multiply`|
|`/`|`op_Division`|`Divide`|
|`%`|`op_Modulus`|`Mod or Remainder`|
|`^`|`op_ExclusiveOr`|`Xor`|
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|
|`&&`|`op_LogicalAnd`|`And`|
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|
|`=`|`op_Assign`|`Assign`|
|`<<`|`op_LeftShift`|`LeftShift`|
|`>>`|`op_RightShift`|`RightShift`|
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|
|`==`|`op_Equality`|`Equals`|
|`!=`|`op_Inequality`|`Equals`|
|`>`|`op_GreaterThan`|`CompareTo`|
|`<`|`op_LessThan`|`CompareTo`|
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|
|`<=`|`op_LessThanOrEqual`|`CompareTo`|
|`*=`|`op_MultiplicationAssignment`|`Multiply`|
|`-=`|`op_SubtractionAssignment`|`Subtract`|
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|
|`%=`|`op_ModulusAssignment`|`Mod`|
|`+=`|`op_AdditionAssignment`|`Add`|
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|
|`,`|`op_Comma`|`Comma`|
|`/=`|`op_DivisionAssignment`|`Divide`|
|`--`|`op_Decrement`|`Decrement`|
|`++`|`op_Increment`|`Increment`|
|`- (unary)`|`op_UnaryNegation`|`Negate`|
|`+ (unary)`|`op_UnaryPlus`|`Plus`|
|`~`|`op_OnesComplement`|`OnesComplement`|

### <a name="overloading-operator-"></a>多載運算子 = =
 多載 `operator ==` 相當複雜。 運算子的語法必須與其他數個成員相容，例如 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 。

### <a name="conversion-operators"></a>轉換運算子
 轉換運算子是一元運算子，可允許從某個類型轉換成另一個類型。 運算子必須定義為運算元或傳回型別上的靜態成員。 轉換運算子有兩種類型：隱含和明確。

 ❌ 如果終端使用者無法明確地預期這類轉換，請不要提供轉換運算子。

 ❌ 請勿定義型別網域以外的轉換運算子。

 例如，、 <xref:System.Int32> <xref:System.Double> 和 <xref:System.Decimal> 都是數數值型別，而 <xref:System.DateTime> 不是。 因此，不應該有轉換運算子來將轉換成 `Double(long)` `DateTime` 。 在這種情況下，最好使用一個函式。

 ❌ 如果轉換可能失真，請勿提供隱含轉換運算子。

 例如，不應該從隱含轉換 `Double` 為， `Int32` 因為 `Double` 的範圍超出 `Int32` 。 即使轉換可能失真，也可以提供明確的轉換運算子。

 ❌ 請勿從隱含轉換擲回例外狀況。

 使用者很難瞭解發生什麼情況，因為他們可能不知道正在進行轉換。

 <xref:System.InvalidCastException?displayProperty=nameWithType>如果對轉換運算子的呼叫導致失真轉換，而且運算子的合約不允許失真轉換，✔️會擲回。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [成員設計方針](member.md)
- [架構設計指導方針](index.md)
