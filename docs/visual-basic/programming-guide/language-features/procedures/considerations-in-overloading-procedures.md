---
title: "考量多載化程序 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- signatures, ParamArray arguments
- ParamArray keyword, parameter arrays
- ParamArray keyword, arguments and signatures
- function overloading, implicit overloads for ParamArray
- ParamArray keyword, signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures, overloading
- parameters, lists
- function overloading, typeless programming
- typeless programming
- function overloading, restrictions
- arguments [Visual Basic], optional
- optional arguments, overloading
- signatures, procedure
- parameter lists
- parameter arrays, overloading arguments
- Visual Basic code, parameter lists
- procedure overloading, considerations
- Option Explicit statement
- restrictions, overloading procedures
- procedures, parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
caps.latest.revision: 26
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: aa20cf367fba157f88afd861a4799540dcdecde1
ms.lasthandoff: 03/13/2017

---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>多載化程序的考慮因素 (Visual Basic)
當您多載程序時，您必須使用不同*簽章*每個多載版本。 這通常表示每個版本都必須指定不同的參數清單。 如需詳細資訊，請參閱 「 不同簽章 」 中[程序多載](./procedure-overloading.md)。  
  
 您可以多載`Function`程序`Sub`程序，並且反之亦然，提供它們具有不同的簽章。 兩個多載不能不同只在於一個具有傳回值，其他則否。  
  
 您可以如同您多載程序中，多載屬性和相同的限制。 不過，您無法多載程序與屬性，反之亦然。  
  
## <a name="alternatives-to-overloaded-versions"></a>多載版本的替代方案  
 是選擇性的引數的存在或其數目為變數時，特別是，有時候必須多載版本的替代方案。  
  
 請記住，選擇性引數不一定支援所有的語言，並會限制使用參數陣列[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。 如果您正在撰寫可能以任何有幾種不同語言所撰寫的程式碼呼叫的程序，多載版本就可以提供最大的彈性。  
  
### <a name="overloads-and-optional-arguments"></a>多載和選擇性引數  
 當呼叫程式碼可以選擇性地提供，或略過一或多個引數時，您可以定義多個多載的版本，或使用選擇性參數。  
  
#### <a name="when-to-use-overloaded-versions"></a>使用多載的版本的時機  
 您可以考慮在下列情況下定義一系列的多載版本︰  
  
-   程序程式碼中的邏輯是根據呼叫的程式碼是否提供選擇性引數明顯不同。  
  
-   程序程式碼無法可靠地測試是否呼叫程式碼已提供選擇性引數。 這種情況，例如，如果沒有任何可做為預設值，呼叫程式碼可能不需要提供。  
  
#### <a name="when-to-use-optional-parameters"></a>當使用選擇性參數  
 您可能偏好在下列情況下的一個或多個選擇性參數︰  
  
-   若要將參數設定為預設值是唯一必要的動作時呼叫的程式碼並不提供選擇性引數。 在這種情況下中的程序程式碼可能較不複雜，如果您定義的其中一個或多個單一版本`Optional`參數。  
  
 如需詳細資訊，請參閱[選擇性參數](./optional-parameters.md)。  
  
### <a name="overloads-and-paramarrays"></a>多載和參數陣列  
 當呼叫程式碼可以傳遞可變引數數目時，您可以定義多個多載的版本，或使用參數陣列。  
  
#### <a name="when-to-use-overloaded-versions"></a>使用多載的版本的時機  
 您可以考慮在下列情況下定義一系列的多載版本︰  
  
-   您知道，呼叫程式碼永遠不會傳遞多個少量的值給參數陣列。  
  
-   程序程式碼中的邏輯是根據呼叫的程式碼傳遞的值數目明顯不同。  
  
-   呼叫程式碼可以傳遞不同的資料類型的值。  
  
#### <a name="when-to-use-a-parameter-array"></a>何時使用參數陣列  
 您最好由`ParamArray`參數，在下列情況︰  
  
-   您不能預測多少值呼叫的程式碼可以傳遞給參數陣列，並可能很多。  
  
-   程序邏輯可用於逐一查看所有呼叫的程式碼傳遞，執行本質相同之作業上的每個值的值。  
  
 如需詳細資訊，請參閱[參數陣列](./parameter-arrays.md)。  
  
## <a name="implicit-overloads-for-optional-parameters"></a>選擇性參數的隱含多載  
 程序時使用[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)參數相當於兩個多載的程序，一個選擇性參數，另一個則不。 您無法多載程序，使用對應至其中的參數清單。 下列宣告可說明這點。  
  
 [!code-vb[VbVbcnProcedures #&58;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]  
  
 [!code-vb[VbVbcnProcedures #&60;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures #&61;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]  
  
 對於具有多個選擇性參數的程序，沒有一組邏輯類似於上述範例所到達的隱含多載。  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>參數陣列參數的隱含多載  
 編譯器會考慮使用的程序[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數具有無限個多載，不同於其他什麼呼叫程式碼會傳遞到參數陣列，如下所示︰  
  
-   當呼叫程式碼不會提供的引數的其中一個多載`ParamArray`  
  
-   當呼叫程式碼提供的一維陣列的其中一個多載`ParamArray`項目型別  
  
-   對每一個正整數，其中一個多載時呼叫的程式碼提供該數目的引數，每個`ParamArray`項目型別  
  
 下列宣告會說明這些隱含多載。  
  
 [!code-vb[VbVbcnProcedures #&68;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]  
  
 [!code-vb[VbVbcnProcedures #&70;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]  
  
 您無法多載，這樣的程序的參數清單，會採用參數陣列的一維陣列。 不過，您可以使用其他隱含多載的簽章。 下列宣告可說明這點。  
  
 [!code-vb[VbVbcnProcedures #&71;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>另一種多載的無類型程式設計  
 如果您想要允許不同的資料型別傳遞至參數呼叫的程式碼，另一個方法是無型別程式設計。 您可以設定型別檢查切換到`Off`與[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)或[/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項。 然後您不需要宣告參數的資料型別。 不過，這個方法有下列缺點相較於多載︰  
  
-   無類型程式設計產生效率較低的執行程式碼。  
  
-   此程序必須測試它預期傳遞的每一個資料型別。  
  
-   編譯器無法通知發生錯誤，如果呼叫程式碼會將此程序不支援的資料類型。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [疑難排解程序](./troubleshooting-procedures.md)   
 [如何︰ 定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)   
 [如何︰ 呼叫多載程序](./how-to-call-an-overloaded-procedure.md)   
 [如何︰ 多載使用選擇性參數的程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [如何︰ 多載使用不定數目參數的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [多載解析](./overload-resolution.md)   
 [多載](../../../../visual-basic/language-reference/modifiers/overloads.md)
