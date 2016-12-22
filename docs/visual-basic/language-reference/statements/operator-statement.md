---
title: "Operator Statement | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.operator"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operators [Visual Basic]"
  - "procedures, operator"
  - "Narrowing keyword, conversion operators"
  - "Visual Basic code, operators"
  - "Widening keyword, conversion operators"
  - "syntax, Operator procedures"
  - "operators [Visual Basic], overloading"
  - "overloaded operators"
  - "operator overloading"
  - "operator procedures"
  - "Operator statement"
  - "CType function, Operator statement"
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
caps.latest.revision: 28
caps.handback.revision: 28
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operator Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

宣告會在類別或結構上定義運算子程序的運算子符號、運算元和程式碼。  
  
## 語法  
  
```  
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]   
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]  
    [ statements ]  
    [ statements ]  
    Return returnvalue  
    [ statements ]  
End Operator  
```  
  
## 組件  
 `attrlist`  
 選擇項。  請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。  
  
 `Public`  
 必要項。  表示這個運算子程序具有 [Public](../../../visual-basic/language-reference/modifiers/public.md) 存取權。  
  
 `Overloads`  
 選擇項。  請參閱 [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)。  
  
 `Shared`  
 必要項。  表示這個運算子程序是 [Shared](../../../visual-basic/language-reference/modifiers/shared.md) 程序。  
  
 `Shadows`  
 選擇項。  請參閱 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。  
  
 `Widening`  
 除非您指定 `Narrowing`，否則這會是轉換運算子的必要項。  表示這個運算子程序會定義 [Widening](../../../visual-basic/language-reference/modifiers/widening.md) 轉換。  請參閱本說明網頁上「擴大和縮小轉換」的內容。  
  
 `Narrowing`  
 除非您指定 `Widening`，否則這會是轉換運算子的必要項。  表示這個運算子程序會定義 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) 轉換。  請參閱本說明網頁上「擴大和縮小轉換」的內容。  
  
 `operatorsymbol`  
 必要項。  這個運算子程序所定義之運算子的符號或識別項。  
  
 `operand1`  
 必要項。  一元 \(Unary\) 運算子 \(包括轉換運算子\) 之單一運算元的名稱和型別，或是二元 \(Binary\) 運算子之左運算元的名稱和型別。  
  
 `operand2`  
 二元運算子的必要項。  二元運算子之右運算元的名稱和型別。  
  
 `operand1` 和 `operand2` 具有下列語法和參數：  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|組件|描述|  
|--------|--------|  
|`ByVal`|選擇項，但是傳遞機制必須是 [ByVal](../../../visual-basic/language-reference/modifiers/byval.md)。|  
|`operandname`|必要項。  代表這個運算元的變數名稱。  請參閱[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`operandtype`|除非 `Option Strict` 為 `On`，否則為選擇項。  這個運算元的資料型別。|  
  
 `type`  
 除非 `Option Strict` 為 `On`，否則為選擇項。  運算子程序所傳回之值的資料型別。  
  
 `statements`  
 選擇項。  運算子程序所執行的陳述式區塊。  
  
 `returnvalue`  
 必要項。  運算子程序傳回給呼叫程式碼的值。  
  
 `End` `Operator`  
 必要項。  結束這個運算子程序的定義。  
  
## 備註  
 您只能在類別或結構中使用 `Operator`。  這表示運算子的「*宣告內容*」\(Declaration Context\) 不能是原始程式檔 \(Source File\)、命名空間 \(Namespace\)、模組、介面、程序和區塊。  如需詳細資訊，請參閱[Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 所有運算子都必須為 `Public Shared`。  您不能指定 `ByRef`、`Optional` 或 `ParamArray` 給任一個運算元。  
  
 您無法使用運算子符號或識別項，保留傳回值；  您必須使用 `Return` 陳述式，且它必須指定一個值。  `Return` 陳述式的數目不受限制並可以出現在程序中的任何位置。  
  
 不論是否使用 `Overloads` 關鍵字，以這種方式定義運算子都稱為「*運算子多載*」。  下表列出您可以定義的運算子。  
  
|型別|運算子|  
|--------|---------|  
|一元|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binary|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|轉換 \(一元\)|`CType`|  
  
 請注意，二元清單中的 `=` 運算子是比較運算子，而不是指派運算子。  
  
 在定義 `CType` 時，您必須指定 `Widening` 或 `Narrowing`。  
  
## 相符的配對  
 您必須將某些運算子定義為相符的配對。  如果要定義此類配對的任一個運算子，也必須定義另一個運算子。  相符的配對如下：  
  
-   `=` 和 `<>`  
  
-   `>` 和 `<`  
  
-   `>=` 和 `<=`  
  
-   `IsTrue` 和 `IsFalse`  
  
## 資料型別限制  
 您所定義的每一個運算子都必須包括定義它的類別或結構。  這表示類別或結構必須以下列的資料型別出現：  
  
-   一元運算子的運算元。  
  
-   至少為二元運算子的任一個運算元。  
  
-   轉換運算子的運算元或傳回型別。  
  
 有些運算子具有其他資料型別限制，如下所示：  
  
-   如果您定義 `IsTrue` 和 `IsFalse` 運算子，則兩者都必須傳回 `Boolean` 型別。  
  
-   如果您定義 `<<` 和 `>>` 運算子，則兩者都必須針對 `operand2` 的 `operandtype` 指定 `Integer` 型別。  
  
 傳回型別不必對應到任一個運算元的型別。  例如，即使兩個運算元都不是 `Boolean`，例如 `=` 或 `<>` 的比較運算子都可以傳回 `Boolean`。  
  
## 邏輯和位元運算子  
 `And`、`Or`、`Not` 和 `Xor` 運算子可以在 Visual Basic 中執行邏輯或位元運算。  然而，如果您在類別或結構上定義上述其中一個運算子，則只能定義它的位元運算。  
  
 您不能直接利用 `Operator` 陳述式，定義 `AndAlso`。  然而，如果您已滿足下列條件，則可以使用 `AndAlso`：  
  
-   您在要用於 `AndAlso` 的相同運算元型別上定義了 `And`。  
  
-   您的 `And` 定義會傳回與定義它的類別或結構相同的型別。  
  
-   您在定義 `And` 的類別或結構上已定義了 `IsFalse` 運算子。  
  
 同樣地，如果您已利用類別或結構的傳回型別，在相同運算元上定義 `Or`，並且在類別或結構上定義了 `IsTrue`，則可以使用 `OrElse`。  
  
## 擴大和縮小轉換  
 「*擴大轉換*」\(Widening Conversion\) 在執行階段永遠都會成功，然而「*縮小轉換*」\(Narrowing Conversion\) 在執行階段則會失敗。  如需詳細資訊，請參閱[Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
 如果您將轉換程序宣告為 `Widening`，則程序程式碼不得產生任何失敗。  這表示：  
  
-   它永遠必須傳回型別 `type` 的有效值。  
  
-   它必須處理所有可能的例外狀況 \(Exception\) 和其他錯誤情況。  
  
-   它必須處理所呼叫之程序傳回的任何錯誤。  
  
 如果轉換程序有可能不成功，或它有可能會造成無法處理的例外狀況，則您必須將它宣告為 `Narrowing`。  
  
## 範例  
 下列程式碼範例使用 `Operator` 陳述式定義結構的大綱，這個結構包括 `And`、`Or`、`IsFalse` 和 `IsTrue` 運算子的運算子程序。  `And` 和 `Or` 各採用型別 `abc` 的兩個運算元並且傳回型別 `abc`。  `IsFalse` 和 `IsTrue` 各採用型別 `abc` 的單一運算元並且傳回型別 `Boolean`。  這些定義會允許呼叫程式碼使用 `And`、`AndAlso`、`Or` 和 `OrElse` 與型別 `abc` 的運算元搭配。  
  
 [!code-vb[VbVbalrStatements#44](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/operator-statement_1.vb)]  
  
## 請參閱  
 [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)   
 [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md)   
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)   
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [How to: Call an Operator Procedure](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)   
 [How to: Use a Class that Defines Operators](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)