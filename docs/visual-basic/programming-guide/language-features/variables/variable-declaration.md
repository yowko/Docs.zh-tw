---
title: "Visual Basic 中的變數宣告 | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "變數 [Visual Basic]，宣告"
  - "成員變數，宣告"
  - "Dim 陳述式，變數宣告"
  - "宣告變數"
  - "變數 [Visual Basic]，範圍"
  - "變數 [Visual Basic]，資料類型"
  - "資料類型 [Visual Basic]，變數宣告"
  - "存留期，變數"
  - "變數 [Visual Basic]，存留期"
  - "存取層級，變數"
  - "範圍，宣告陳述式"
  - "變數 [Visual Basic]，存取層級"
  - "區域變數，宣告"
  - "範圍，變數"
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
caps.latest.revision: 31
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 31
---
# Visual Basic 中的變數宣告
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您宣告變數以指定它的名稱和特性。  變數的宣告陳述式 \(Declaration Statement\) 是 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)。  它的位置及內容會決定變數的特性。  
  
 如需變數命名規則 \(Rule\) 及考慮事項等資訊，請參閱[Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
## 宣告層級  
  
### 區域和成員變數  
 *區域變數*\(Local Variable\) 是在程序中宣告的變數。  「*成員變數*」\(Member Variable\) 是 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 型別的成員；該變數是在類別 \(Class\)、結構或模組內部之模組層次宣告的，而不是在類別、結構或模組內部之任何程序內宣告。  
  
### 共用與執行個體變數  
 在類別或結構中，成員變數的分類取決於它是否為共用。  如果它是用[共用](../../../../visual-basic/language-reference/modifiers/shared.md)關鍵字宣告的，它就是一個「*共用變數*」\(Shared Variable\)，並且存在於該類別或結構內所有執行個體 \(Instance\) 共用的一個複本中。  
  
 否則它就是一個「*執行個體變數*」\(Instance Variable\)，而且會為該類別或結構的每個執行個體建立一個單獨複本。  執行個體變數之複製到它建立類別或結構的執行個體是使用。  它是執行個體變數複本的獨立在類別或結構的其他執行個體的。  
  
## 宣告資料型別  
 宣告陳述式中的 [As](../../../../visual-basic/language-reference/statements/as-clause.md) 子句可定義您所宣告的變數之資料型別或物件型別。  您可以為變數指定下列任何一個型別：  
  
-   基礎資料型別 \(Elementary Data Type\)，例如 `Boolean`、`Long` 或 `Decimal`  
  
-   複合資料型別，例如陣列或結構  
  
-   於您的或其他應用程式定義的物件型別或類別  
  
-   [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] 類別，例如 <xref:System.Windows.Forms.Label> 或 <xref:System.Windows.Forms.TextBox>  
  
-   介面型別，例如 <xref:System.IComparable> 或 <xref:System.IDisposable>  
  
 您可以在一個陳述式中宣告數個變數，不必重複資料型別。  在下列陳述式中，變數 `i`、`j` 及 `k` 將宣告為型別 `Integer`；`l` 及 `m` 則為 `Long`；而 `x` 及 `y` 則為 `Single`︰  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 如需資料型別的詳細資訊，請參閱 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)。  如需物件的詳細資訊，請參閱 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)和[使用元件進行程式設計](../Topic/Programming%20with%20Components.md)。  
  
## 區域型別推斷  
 「*型別推斷*」\(Type Inference\) 用於判斷未使用 `As` 子句宣告之區域變數的資料型別。  編譯器是根據初始化運算式的型別推斷變數的型別。  這可讓您宣告變數，而不需要明確陳述型別。  在下列範例中，`num1` 和 `num2` 都會強型別為整數。  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/variable-declaration_1.vb)]  
  
 如果您要使用區域型別推斷，`Option Infer` 必須設定為 `On`。  如需詳細資訊，請參閱[Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)與[Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)。  
  
## 宣告變數的特性。  
 變數的「*存留期*」\(Lifetime\) 是它可使用的期間。  一般來說，只要宣告變數的項目 \(如程序或類別\) 持續存在，該變數就存在。  如果變數不需要繼續存在於存留期其內含項目之外，您不需要執行任何特殊在宣告。  如果變數需要存在的期間較其所屬項目更長，您可以在變數的 `Dim` 陳述式 \(Statement\) 中包含 `Static` 或 `Shared` 關鍵字。  如需詳細資訊，請參閱[Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)。  
  
 變數的「*範圍*」\(Scope\) 不需要限定名稱即可參考其所有程式碼集合。  變數的範圍取決於它被宣告的地方。  位於指定區域內的程式碼不需要完整名稱就可使用該區域定義的變數。  如需詳細資訊，請參閱[Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)。  
  
 變數的「*存取層次*」\(Access Level\) 是具有存取權限程式碼的延伸。  此乃由存取修飾詞 \(Modifier\) 決定 \(例如 [Public](../../../../visual-basic/language-reference/modifiers/public.md) 或 [Private](../../../../visual-basic/language-reference/modifiers/private.md)\)，也就是您於 `Dim` 陳述式中所使用的修飾詞。  如需詳細資訊，請參閱[Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## 請參閱  
 [How to: Create a New Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)   
 [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)   
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)   
 [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)