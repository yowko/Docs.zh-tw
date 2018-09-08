---
title: 運算子多載
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ca42d25a5f3456c6a10eff76d7015656322abae
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131243"
---
# <a name="operator-overloads"></a>運算子多載
運算子多載可讓顯示如同它們是內建語言基本類型的 framework 型別。  
  
 雖然允許，而且在某些情況下很有用，應該小心使用運算子多載。 有許多的案例中的運算子多載已被濫用，例如架構設計人員何時啟動的作業，應該是簡單的方法中使用運算子。 下列指導方針可協助您決定何時以及如何使用運算子多載。  
  
 **X AVOID** 運算子多載，除了定義應該像是基本 （內建） 類型的類型。  
  
 **✓ CONSIDER** 應該像是基本類型的類型中定義運算子多載。  
  
 例如，<xref:System.String?displayProperty=nameWithType>已經`operator==`和`operator!=`定義。  
  
 **✓ DO** 運算子多載定義表示數字的結構中 (例如<xref:System.Decimal?displayProperty=nameWithType>)。  
  
 **X DO NOT** 別出心裁時定義運算子多載。  
  
 運算子多載是在其中顯而易見的是作業的結果將會的很有用。 比方說，是合理能夠減一<xref:System.DateTime>從另一個`DateTime`，並取得<xref:System.TimeSpan>。 不過，它不適合使用聯集的這兩個資料庫查詢的邏輯聯集運算子，或使用 shift 鍵運算子來寫入資料流。  
  
 **X DO NOT** 提供運算子多載，除非其中至少一個運算元是定義多載的型別。  
  
 **✓ DO** 對稱方式多載運算子。  
  
 例如，如果您多載`operator==`，您也應該多載`operator!=`。 同樣地，如果您多載`operator<`，您也應該多載`operator>`，依此類推。  
  
 **✓ CONSIDER** 提供具有對應的好記名稱的方法與每個多載的運算子。  
  
 許多語言不支援運算子多載。 基於這個理由，建議您使用多載運算子的類型，包括第二種方法提供對等功能的適當定義域專屬名稱。  
  
 下表包含運算子和對應的好記的方法名稱的清單。  
  
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
  
### <a name="overloading-operator-"></a>多載運算子 = =  
 多載`operator ==`是相當複雜。 運算子的語意需要相容於數個其他的成員，例如<xref:System.Object.Equals%2A?displayProperty=nameWithType>。  
  
### <a name="conversion-operators"></a>轉換運算子  
 轉換運算子是一元 （unary） 運算子，允許從一個類型轉換為另一個。 運算子必須定義為運算元或傳回型別上的靜態成員。 有兩種類型的轉換運算子： 隱含和明確。  
  
 **X DO NOT** 提供轉換運算子，如果這類轉換不清楚所預期的使用者。  
  
 **X DO NOT** 定義轉換運算子的型別網域之外。  
  
 例如， <xref:System.Int32>， <xref:System.Double>，並<xref:System.Decimal>全部都是數值類型，而<xref:System.DateTime>不是。 因此，應該會有任何要轉換的轉換運算子`Double(long)`至`DateTime`。 建構函式是這種情況的慣用物件。  
  
 **X DO NOT** 提供隱含轉換運算子，如果轉換可能會失真。  
  
 比方說，不應該有的隱含轉換`Double`要`Int32`因為`Double`更廣的範圍，大於`Int32`。 您可以提供明確轉換運算子，即使轉換可能會失真。  
  
 **X DO NOT** 擲回例外狀況，從隱含轉換。  
  
 它是很難了解發生什麼動作，因為它們可能不會察覺轉換正在進行中的使用者。  
  
 **✓ DO** 擲回 <xref:System.InvalidCastException?displayProperty=nameWithType> 如果轉型運算子的呼叫會導致損失的轉換和運算子的合約不允許轉換損失。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [成員設計方針](../../../docs/standard/design-guidelines/member.md)  
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
