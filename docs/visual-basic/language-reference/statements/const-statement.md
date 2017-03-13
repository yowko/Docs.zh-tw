---
title: "Const Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Const"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Const statement [Visual Basic]"
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
caps.latest.revision: 28
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 28
---
# Const Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

宣告並定義一或多個常數。  
  
## 語法  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## 組件  
 `attributelist`  
 選擇項。  套用到這個陳述式中宣告之所有常數的屬性清單。  請參閱以角括弧 \("`<`" 和 "`>`"\) 括起來的[Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md)。  
  
 `accessmodifier`  
 選擇項。  使用此項，指定哪一個程式碼可以存取這些常數。  選項如下：[Public](../../../visual-basic/language-reference/modifiers/public.md)、[Protected](../../../visual-basic/language-reference/modifiers/protected.md)、[Friend](../../../visual-basic/language-reference/modifiers/friend.md)、`Protected Friend` 或 [Private](../../../visual-basic/language-reference/modifiers/private.md)。  
  
 `Shadows`  
 選擇項。  使用此項，重新宣告並隱藏基底類別中的程式設計項目。  請參閱 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。  
  
 `constantlist`  
 必要項。  這個陳述式中要宣告的常數清單。  
  
 `constant` `[ ,` `constant` `... ]`  
  
 每個 `constant` 都具有下列語法和組成部分：  
  
 `constantname` `[ As` `datatype` `] =` `initializer`  
  
|組件|描述|  
|--------|--------|  
|`constantname`|必要項。  常數名稱。  請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`datatype`|如果 `Option Strict` 為 `On`，則為必要項。  常數的資料型別。|  
|`initializer`|必要項。  在編譯時期評估並指派給常數的運算式。|  
  
## 備註  
 如果應用程式中有一個永遠不會變更的值，則您可以定義一個具名常數，然後以這個常數代替常值 \(Literal\)。  因為名稱會比值更容易記住。  您只需定義這個常數一次，便可以將這個常數用在程式碼中的許多地方。  在更新的版本中，如果需要重新定義值，則 `Const` 陳述式會是唯一需要進行的變更。  
  
 您只能在模組或程序層級使用 `Const`。  這表示變數的「*宣告內容*」\(Declaration Context\) 必須是類別、結構、模組、程序或區塊，且不可以是原始程式檔 \(Source File\)、命名空間 \(Namespace\) 或介面。  如需詳細資訊，請參閱[Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 在程序內的區域常數會預設為公用 \(Public\) 存取，而且您無法對這些常數使用任何存取修飾詞 \(Modifier\)。  類別和模組成員常數 \(在任何程序外\) 預設為私用 \(Private\) 存取，而結構成員常數則預設為公用存取。  您可以使用存取修飾詞調整存取層級。  
  
## 規則  
  
-   **宣告內容：** 在模組層級宣告的常數 \(在任何程序外\) 是「*成員常數*」\(Member Constant\)，屬於宣告它的類別、結構或模組的成員。  
  
     在程序層級宣告的常數則是「*區域常數*」，屬於宣告它的程序或區塊的區域常數。  
  
-   **屬性** ：您只能將屬性套用到成員常數，不能套用到區域常數。  屬性會提供資訊給組件的中繼資料 \(Metadata\)，這對於區域常數之類的暫時儲存體並沒有意義。  
  
-   **修飾詞。** 根據預設，所有的常數都是 `Shared`、`Static` 和 `ReadOnly`。  宣告常數時，您無法使用任何一個上述關鍵字。  
  
     在程序層級中，您無法使用 `Shadows` 或任何存取修飾詞宣告區域常數。  
  
-   **多個常數** 您可以在同一個宣告陳述式中宣告數個常數，並為每一個常數指定 `constantname` 部分。  常數之間以逗號 \(,\) 來分隔。  
  
## 資料型別規則  
  
-   **資料型別** `Const` 陳述式可以宣告變數的資料型別。  您可以指定任何資料型別或列舉型別名稱。  
  
-   **預設型別。** 如果沒有指定 `datatype`，則常數會採用 `initializer` 的資料型別。  如果同時指定 `datatype` 和 `initializer`，則 `initializer` 的資料型別必須可以轉換為 `datatype`。  如果既不指定 `datatype`，也不指定 `initializer`，則資料型別會預設值為 `Object`。  
  
-   **不同型別** 您宣告的每一個變數都可以使用個別的 `As` 子句，以便為不同常數指定不同資料型別。  不過無法使用一般 `As` 子句，宣告數個型別相同的常數。  
  
-   **初始設定**： 您必須初始化 `constantlist` 中每一個常數的值。  您可以使用 `initializer` 提供要指派給常數的運算式。  運算式可以是常值、其他已定義的常數，以及已定義之列舉型別成員的任意組合。  您可以利用算術和邏輯運算子 \(Logical Operator\) 來結合這樣的項目。  
  
     在 `initializer` 中不能使用變數或函式。  但是，您可以使用轉換關鍵字，例如 `CByte` 和 `CShort`。  如果您使用常數 `String` 或 `Char` 引數來呼叫，也可以使用 `AscW`，因為可以在編譯時期進行評估。  
  
## 行為  
  
-   **範圍。** ：區域常數只能從其程序或區塊內進行存取。  成員常數則可以從其類別、結構或模組內的任意位置進行存取。  
  
-   **限定性條件。** ：類別、結構或模組外的程式碼必須以該類別、結構或模組的名稱，限定成員常數的名稱。  程序或區塊外的程式碼，無法參考該程序或區塊內的任何區域常數。  
  
## 範例  
 下列範例會利用 `Const` 陳述式，宣告用於取代常值的常數。  
  
 [!code-vb[VbVbalrStatements#13](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_1.vb)]  
  
## 範例  
 如果您定義一個資料型別為 `Object` 的常數，則 Visual Basic 編譯器會指定這個常數的型別為 `initializer`，而不是 `Object`。  在下列範例中，常數 `naturalLogBase` 具有執行階段型別 `Decimal`。  
  
 [!code-vb[VbVbalrStatements#87](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_2.vb)]  
  
 前一個範例會在 [GetType Operator](../../../visual-basic/language-reference/operators/gettype-operator.md)所傳回的 <xref:System.Type> 物件上使用 <xref:System.Type.ToString%2A> 方法，因為 <xref:System.Type> 無法使用 `CStr` 轉換為 `String`。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md)   
 [\#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md)   
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md)   
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Constants and Enumerations](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)   
 [Constants and Enumerations](../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)