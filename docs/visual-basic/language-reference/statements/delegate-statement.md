---
title: "Delegate Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Delegate"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "delegate keyword"
  - "Delegate statement"
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# Delegate Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

用來宣告委派 \(Delegate\)。  委派是一種參考型別，它會參考型別的 `Shared` 方法或物件的執行個體方法 \(Instance Method\)。  任何具有相符參數和傳回型別的程序都可以用來建立這個委派類別的執行個體。  接著可透過委派執行個體來叫用程序。  
  
## 語法  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`attrlist`|選擇項。  套用至這個委派的屬性 \(Attribute\) 清單。  多個屬性之間以逗號 \(,\) 分隔。  您必須將[Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md)置於角括弧中 \("`<`" 和 "`>`"\)。|  
|`accessmodifier`|選擇項。  指定哪些程式碼可以存取委派。  可以是下列其中一項：<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)。  可存取項目 \(宣告委派\) 的任何程式碼都可存取它。<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)。  只有委派的類別或衍生類別內的程式碼可存取它。<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)。  只有相同組件內的程式碼可存取委派。<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)。  只有宣告委派之項目內的程式碼可存取它。<br /><br /> 您可以指定 `Protected Friend`，以便從委派的類別、衍生類別或相同組件內的程式碼進行存取。|  
|`Shadows`|選擇項。  表示此委派會重新宣告並隱藏基底類別中相同具名的程式設計項目，這個項目即為多載項目集。  您可以用任意一種宣告項目遮蔽其他宣告項目。<br /><br /> 無法在遮蔽項目的衍生類別內存取受遮蔽項目 \(Shadowed Element\)，除非是從無法存取主導遮蔽項目 \(Shadowing Element\) 的類別內。  例如，如果 `Private` 項目會遮蔽基底類別項目，則無權存取 `Private` 項目的程式碼會改為存取基底類別項目。|  
|`Sub`|選擇項，但必須出現 `Sub` 或 `Function`。  將這個程序宣告為不傳回值的委派 `Sub` 程序。|  
|`Function`|選擇項，但必須出現 `Sub` 或 `Function`。  將這個程序宣告為傳回值的委派 `Function` 程序。|  
|`name`|必要項。  委派型別的名稱；依照標準變數命名規範來命名。|  
|`typeparamlist`|選擇項。  這個委派的型別參數清單。  參數之間以逗號 \(,\) 來分隔。  每個型別參數都可以使用 `In` 和 `Out` 泛型修飾詞宣告為 Variant。  必須以括號括住 [Type List](../../../visual-basic/language-reference/statements/type-list.md)，並以 `Of` 關鍵字引入它。|  
|`parameterlist`|選擇項。  呼叫程序時傳遞給該程序的參數清單。  必須以括號括住 [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)。|  
|`type`|如果指定 `Function` 程序，則是必要項。  傳回值的資料型別。|  
  
## 備註  
 `Delegate` 陳述式會定義委派類別的參數和傳回型別。  任何具有相符參數和傳回型別的程序都可以用來建立這個委派類別的執行個體。  接著可透過委派執行個體來叫用程序，方式是呼叫委派的 `Invoke` 方法。  
  
 可在命名空間 \(Namespace\)、模組、類別或結構層級上宣告委派，但無法在程序之內宣告。  
  
 每個委派類別會定義傳遞物件方法規格的建構函式 \(Constructor\)。  委派建構函式的引數必須是方法的參考或 Lambda 運算式。  
  
 若要指定方法的參考，請使用下列語法：  
  
 `AddressOf` \[`expression`.\]`methodname`  
  
 `expression` 在編譯時期的型別必須是包含指定名稱 \(其簽章符合委派類別的簽章\) 方法的類別或介面的名稱。  `methodname` 可以是共用方法或執行個體方法。  即使您為類別的預設方法建立委派，`methodname` 還是必要項。  
  
 若要指定 Lambda 運算式，請使用下列語法：  
  
 `Function` \(\[`parm` As `type`, `parm2` As `type2`, ...\]\) `expression`  
  
 函式的簽章必須符合委派型別的簽章。  如需 Lambda 運算式的詳細資訊，請參閱 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 如需委派的詳細資訊，請參閱[Delegates](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)。  
  
## 範例  
 下列範例使用 `Delegate` 陳述式來宣告委派，以便在兩個數字上操作並傳回一個數字。  `DelegateTest` 方法會採用這個型別的委派執行個體，並用它在成對的數字上作業。  
  
 [!code-vb[VbVbalrDelegates#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]  
  
## 請參閱  
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)   
 [Delegates](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [如何：使用泛型類別](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Visual Basic 中的泛型類型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [共變數和反變數](../Topic/Covariance%20and%20Contravariance%20\(C%23%20and%20Visual%20Basic\).md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)