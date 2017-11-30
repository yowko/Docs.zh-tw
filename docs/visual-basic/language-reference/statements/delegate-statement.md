---
title: "Delegate 陳述式"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e79a261f74cbc7aa067af63629e31bedf65d163
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-statement"></a>Delegate 陳述式
用來宣告委派。 委派是參考類型，這是指`Shared`方法的型別或物件的執行個體方法。 任何具有相符的參數和傳回型別程序可以用來建立這個委派類別的執行個體。 此程序可然後稍後會透過叫用委派執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`attrlist`|選擇項。 這個委派所套用的屬性清單。 以逗號分隔多個屬性。 您必須將[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)在角括號 ("`<`"和"`>`")。|  
|`accessmodifier`|選擇項。 指定哪些程式碼可以存取的委派。 可以是下列其中一項：<br /><br /> -   [公用](../../../visual-basic/language-reference/modifiers/public.md)。 任何可以存取宣告的委派之項目的程式碼可以存取它。<br />-   [受保護的](../../../visual-basic/language-reference/modifiers/protected.md)。 只有在委派的類別或衍生的類別中的程式碼可以存取它。<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)。 相同的組件中的程式碼可以存取的委派。<br />-   [私用](../../../visual-basic/language-reference/modifiers/private.md)。 宣告委派的項目內的程式碼可以存取它。<br /><br /> 您可以指定`Protected Friend`來啟用從委派類別，衍生的類別或相同組件內的程式碼存取。|  
|`Shadows`|選擇項。 表示此委派會重新宣告並隱藏相同具名的程式設計項目或基底類別中的多載項目集。 您可以使用任何其他類型遮蔽任何一種已宣告的項目。<br /><br /> 無法從遮蔽項目的衍生類別內使用遮蔽的項目，除了從無法存取遮蔽項目的位置以外。 例如，如果`Private`項目會遮蔽基底類別項目，並沒有存取權限的程式碼`Private`元素改為存取基底類別項目。|  
|`Sub`|選擇性，但請`Sub`或`Function`必須出現。 將此程序的委派宣告`Sub`沒有傳回值的程序。|  
|`Function`|選擇性，但請`Sub`或`Function`必須出現。 將此程序的委派宣告`Function`傳回值的程序。|  
|`name`|必要項。 將委派類型的名稱依照標準變數命名慣例。|  
|`typeparamlist`|選擇項。 此委派的型別參數的清單。 以逗號分隔多個類型參數。 （選擇性） 每個類型參數可以宣告變數使用`In`和`Out`泛型修飾詞。 您必須將[型別清單](../../../visual-basic/language-reference/statements/type-list.md)括號括住並將它與引入`Of`關鍵字。|  
|`parameterlist`|選擇項。 呼叫時，會傳遞至程序的參數清單。 您必須將[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)括號括住。|  
|`type`|如果您指定為必要項`Function`程序。 傳回值的資料類型。|  
  
## <a name="remarks"></a>備註  
 `Delegate`陳述式定義委派類別的參數和傳回型別。 任何具有相符參數和傳回型別程序可以用來建立這個委派類別的執行個體。 此程序可以然後稍後叫用委派執行個體，透過呼叫委派的`Invoke`方法。  
  
 在命名空間、 模組、 類別或結構的層級，但程序內不可以宣告委派。  
  
 每個委派類別會為傳遞的建構函式定義物件方法的規格。 對委派建構函式的引數必須是對方法的參考或 lambda 運算式。  
  
 若要指定對方法的參考，請使用下列語法：  
  
 `AddressOf` [`expression`.]`methodname`  
  
 `expression` 的編譯時期型別必須是類別或介面的名稱，而該類別或介面包含其簽章符合委派類別簽章的特定名稱方法。 `methodname` 可以是共用的方法或執行個體方法。 `methodname` 不是選擇性的，即使您為類別的預設方法建立了委派也一樣。  
  
 若要指定 lambda 運算式，請使用下列語法：  
  
 `Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`  
  
 函式的簽章必須符合委派型別的簽章。 如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
 如需委派的詳細資訊，請參閱[委派](../../../visual-basic/programming-guide/language-features/delegates/index.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`Delegate`陳述式來宣告委派，以便在兩個數字上運作，而傳回一個數字。 `DelegateTest`方法會採用這種類型的委派的執行個體，並使用它來操作的編號組。  
  
 [!code-vb[VbVbalrDelegates#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
 [委派](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [如何：使用泛型類別](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Visual Basic 中的泛型型別](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [共變數和反變數](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
