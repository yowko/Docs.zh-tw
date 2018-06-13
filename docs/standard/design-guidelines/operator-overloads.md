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
ms.openlocfilehash: 747fc21aceae60e362c72391ae265e45d6f8445f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579303"
---
# <a name="operator-overloads"></a>運算子多載
運算子多載可讓架構類型顯示為像是內建的語言基本類型。  
  
 雖然允許在某些情況下很有用，應小心使用運算子多載。 有許多情況下，在哪個運算子多載已被濫用，例如當架構設計人員開始使用運算子應該是簡單的方法的作業。 下列指導方針有助於您決定何時以及如何使用運算子多載。  
  
 **請避免 x**運算子多載，除了定義應該像是基本 （內建） 類型的類型。  
  
 **✓ 考慮**應該像是基本類型的類型中定義運算子多載。  
  
 例如，<xref:System.String?displayProperty=nameWithType>具有`operator==`和`operator!=`定義。  
  
 **✓ 不要**運算子多載定義表示數字的結構中 (例如<xref:System.Decimal?displayProperty=nameWithType>)。  
  
 **X 不**別出心裁時定義運算子多載。  
  
 運算子多載是在其中顯而易見的是作業的結果將會的很有用。 例如，合理能夠減一<xref:System.DateTime>從另一個`DateTime`並取得<xref:System.TimeSpan>。 不過，不適合使用聯集的這兩個資料庫查詢的邏輯聯集運算子，或使用 shift 鍵運算子來寫入資料流。  
  
 **X 不**提供運算子多載，除非其中至少一個運算元是定義多載的型別。  
  
 **✓ 不要**對稱方式多載運算子。  
  
 例如，如果您多載`operator==`，您也應該多載`operator!=`。 同樣地，如果您多載`operator<`，您也應該多載`operator>`，依此類推。  
  
 **✓ 考慮**提供具有對應的好記名稱的方法與每個多載的運算子。  
  
 許多語言不支援運算子多載。 基於這個理由，建議多載運算子的類型包括第二種方法提供對等功能的適當網域特定名稱。  
  
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
 多載`operator ==`是相當複雜。 運算子的語意必須相容於數個其他的成員，例如<xref:System.Object.Equals%2A?displayProperty=nameWithType>。  
  
### <a name="conversion-operators"></a>轉換運算子  
 轉換運算子是一元運算子，允許轉換成另一種類型。 運算子必須定義為運算元或傳回型別上的靜態成員。 有兩種類型的轉換運算子： 隱含與明確。  
  
 **X 不**提供轉換運算子，如果這類轉換不清楚所預期的使用者。  
  
 **X 不**定義轉換運算子的型別網域之外。  
  
 例如， <xref:System.Int32>， <xref:System.Double>，和<xref:System.Decimal>是所有的數字類型，而<xref:System.DateTime>不是。 因此，應該會有任何轉換運算子，將轉換`Double(long)`至`DateTime`。 建構函式是在這種情況下的慣用物件。  
  
 **X 不**提供隱含轉換運算子，如果轉換可能會失真。  
  
 例如，不應該有的隱含轉換`Double`至`Int32`因為`Double`已廣泛比`Int32`。 可以提供明確的轉換運算子，即使轉換可能會失真。  
  
 **X 不**擲回例外狀況，從隱含轉換。  
  
 並不容易了解發生什麼事，因為它們可能不會察覺轉換正在進行中的使用者。  
  
 **✓ 不要**擲回<xref:System.InvalidCastException?displayProperty=nameWithType>如果轉型運算子的呼叫會導致損失的轉換和運算子的合約不允許轉換損失。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [成員設計方針](../../../docs/standard/design-guidelines/member.md)  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
