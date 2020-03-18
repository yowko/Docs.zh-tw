---
title: 運算子多載
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 0999e94c8d77396b237522e89c51206ce1226718
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400565"
---
# <a name="operator-overloads"></a>運算子多載
運算子多載允許框架類型顯示為內置語言基元。

 儘管在某些情況下允許並且很有用，但應謹慎使用操作員超載。 在許多情況下，運算子超載被濫用，例如框架設計器開始使用運算子執行應該簡單的操作。 以下指南將説明您決定何時以及如何使用運算子多載。

 ❌AVOID 定義運算子多載，但應感覺像基元（內置）類型的類型除外。

 ✔️考慮在應感覺像基元類型的類型中定義運算子多載。

 例如，<xref:System.String?displayProperty=nameWithType>已`operator==`和`operator!=`已定義。

 ✔️DO在表示數位（如<xref:System.Decimal?displayProperty=nameWithType>）的結構中定義運算子多載。

 ❌定義運算子超載時不要可愛。

 在操作結果立即明顯的情況下，操作員重載非常有用。 例如，能夠從另<xref:System.DateTime>`DateTime`一個中減去一個並獲取 一個<xref:System.TimeSpan>是有意義的。 但是，使用邏輯聯合運算子聯合兩個資料庫查詢或使用移位運算子寫入流是不適當的。

 ❌除非至少有一個運算元是定義重載的類型，否則不要提供運算子多載。

 ✔️以對稱方式執行重載運算子。

 例如，如果重載`operator==`， 還應重載 。 `operator!=` 同樣，如果重載`operator<`，也應重載`operator>`等。

 ✔️考慮提供與每個重載運算子對應的易記名稱的方法。

 許多語言不支援運算子多載。 因此，建議重載運算子的類型包括具有提供等效功能的適當特定于域的名稱的輔助方法。

 下表包含運算子清單和相應的友好方法名稱。

|C# 運算子符號|中繼資料名稱|易記名稱|
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

### <a name="overloading-operator-"></a>重載運算子 |
 超載`operator ==`相當複雜。 運算子的語義需要與其他幾個成員（如<xref:System.Object.Equals%2A?displayProperty=nameWithType>） 相容。

### <a name="conversion-operators"></a>轉換運算子
 轉換運算子是允許從一種類型轉換為另一種類型的單位運算子。 運算子必須定義為運算元或返回類型的靜態成員。 轉換運算子有兩種類型：隱式運算子和顯式運算子。

 ❌如果最終使用者沒有明確預期此類轉換，則不要提供轉換運算子。

 ❌不要在類型域之外定義轉換運算子。

 <xref:System.Int32>例如，<xref:System.Double>和<xref:System.Decimal>都是數位類型， 而不是。 <xref:System.DateTime> 因此，不應有轉換運算子將`Double(long)`轉換為 。 `DateTime` 在這種情況下，建構函式是首選。

 ❌如果轉換可能丟失，請不要提供隱式轉換運算子。

 例如，`Double`不應有從 到`Int32`的隱式轉換，`Double`因為 範圍比`Int32`寬。 即使轉換可能丟失，也可以提供顯式轉換運算子。

 ❌不要從隱式強制轉換中引發異常。

 最終使用者很難理解發生了什麼，因為他們可能不知道正在進行轉換。

 如果調用強制<xref:System.InvalidCastException?displayProperty=nameWithType>轉換運算子導致虧損轉換，並且操作員的合同不允許虧損轉換，則✔️強制進行丟棄。

 *部分© 2005， 2009 微軟公司.保留擁有權利。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [成員設計方針](../../../docs/standard/design-guidelines/member.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
