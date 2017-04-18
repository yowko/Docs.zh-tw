---
title: "運算子多載 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "運算子 [.NET Framework] 的多載"
  - "名稱 [.NET Framework] 的多載運算子"
  - "成員設計方針操作員"
  - "多載運算子"
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 運算子多載
運算子多載可讓架構類型顯示為像是內建語言基本類型。  
  
 雖然允許而且在某些情況下很有用，但是應該謹慎使用運算子多載。 還有許多案例中的運算子多載已被濫用，例如架構設計人員何時啟動的作業，應該是簡單的方法使用運算子。 下列指導方針應該協助您決定何時以及如何使用運算子多載。  
  
 **X 避免** 運算子多載，除了定義應該像基本 （內建） 類型的類型。  
  
 **✓ 考慮** 應該像基本型別的型別中定義運算子多載。  
  
 例如， <xref:System.String?displayProperty=fullName> 具有 `operator==` 和 `operator!=` 定義。  
  
 **✓ 執行** 結構來表示數字中定義的運算子多載 \(例如 <xref:System.Decimal?displayProperty=fullName>\)。  
  
 **X 不** 別出心裁時定義運算子多載。  
  
 運算子多載是不是立即看出運算的結果將會的很有用。 比方說，是合理能減一 <xref:System.DateTime> 從另一個 `DateTime` 並取得 <xref:System.TimeSpan>。 不過，不適合使用聯集的邏輯運算子，來聯結兩個資料庫查詢，或要移位運算子用來寫入資料流。  
  
 **X 不** 提供運算子多載，除非至少其中一個運算元是定義此多載的型別。  
  
 **✓ 執行** 對稱方式多載運算子。  
  
 例如，如果您多載 `operator==`, ，您也應該多載 `operator!=`。 同樣地，如果您多載 `operator<`, ，您也應該多載 `operator>`, ，依此類推。  
  
 **✓ 考慮** 提供具有對應的好記名稱的方法，每個多載的運算子。  
  
 許多語言不支援運算子多載。 基於這個理由，建議您多載運算子的型別包括第二種方法提供對等功能的適當網域特定名稱。  
  
 下表包含運算子和對應的好記的方法名稱的清單。  
  
|C\# 運算子符號|中繼資料名稱|易記名稱|  
|---------------|------------|----------|  
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|  
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|  
|`+ (binary)`|`op_Addition`|`Add`|  
|`- (binary)`|`op_Subtraction`|`Subtract`|  
|`* (binary)`|`op_Multiply`|`Multiply`|  
|`/`|`op_Division`|`Divide`|  
|`%`|`op_Modulus`|`Mod or Remainder`|  
|`^`|`op_ExclusiveOr`|`Xor`|  
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|  
|`&#124;`|`op_BitwiseOr`|`BitwiseOr`|  
|`&&`|`op_LogicalAnd`|`And`|  
|`&#124;&#124;`|`op_LogicalOr`|`Or`|  
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
|`&#124;=`|`op_BitwiseOrAssignment`|`BitwiseOr`|  
|`,`|`op_Comma`|`Comma`|  
|`/=`|`op_DivisionAssignment`|`Divide`|  
|`--`|`op_Decrement`|`Decrement`|  
|`++`|`op_Increment`|`Increment`|  
|`- (unary)`|`op_UnaryNegation`|`Negate`|  
|`+ (unary)`|`op_UnaryPlus`|`Plus`|  
|`~`|`op_OnesComplement`|`OnesComplement`|  
  
### 多載運算子 \= \=  
 多載 `operator ==` 是相當複雜。 運算子的語意需要與其他數個成員，例如 <xref:System.Object.Equals%2A?displayProperty=fullName>。  
  
### 轉換運算子  
 轉換運算子是一元 （unary） 運算子，允許從一個類型轉換為另一個。 必須為靜態成員運算元或傳回型別定義運算子。 有兩種類型的轉換運算子︰ 隱含和明確。  
  
 **X 不** 如果這類轉換顯然不應該由使用者提供的轉換運算子。  
  
 **X 不** 定義轉換運算子的型別網域之外。  
  
 例如， <xref:System.Int32>, ，<xref:System.Double>, ，和 <xref:System.Decimal> 是所有的數字類型，而 <xref:System.DateTime> 不是。 因此，應該會有任何轉換運算子，將轉換 `Double(long)` 到 `DateTime`。 建構函式會偏好這種情況。  
  
 **X 不** 提供隱含轉換運算子，如果轉換可能會失真。  
  
 例如，不應該有的隱含轉換 `Double` 至 `Int32` 因為 `Double` 具有優於 `Int32`。 可以提供明確的轉換運算子，即使轉換可能會失真。  
  
 **X 不** 擲回例外狀況從隱含轉換。  
  
 就很難了解發生問題，因為它們可能不知道轉換正在進行中的使用者。  
  
 **✓ 執行** 擲回 <xref:System.InvalidCastException?displayProperty=fullName> 如果轉型運算子的呼叫會導致有損失的轉換和運算子的合約不允許轉換損失。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [成員設計方針](../../../docs/standard/design-guidelines/member.md)   
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)