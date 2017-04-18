---
title: "常數的概觀 (Visual Basic) |Microsoft 文件"
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
- constants
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 8004045d233da0db017b26b350743ad9f8d61845
ms.lasthandoff: 03/13/2017

---
# <a name="constants-overview-visual-basic"></a>常數的概觀 (Visual Basic)
常數是有意義的名稱來取代數字或字串，不會變更。 常數用來儲存，正如其名，維持應用程式的執行過程中相同的值。 您可以大幅提高您的程式碼的可讀性，並使它更易於維護藉由使用常數。 在包含的值會重複出現的程式碼中使用它們，或這取決於某些很難記住或沒有明顯意義的數字。  
  
## <a name="how-to-create-and-use-constants"></a>如何建立和使用常數  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]包含許多預先定義的常數，主要用於列印或顯示。 您也可以建立自己的常數與`Const`陳述式中，使用相同的指導方針，您會建立變數的名稱。 如果`Option Strict`是`On`，您必須明確宣告常數的類型。  
  
 常數的範圍，也就是變數的可以參考它完全不需限定其名稱的所有程式碼，是變數的在相同的位置所宣告相同。 若要建立特定的程序的範圍內的常數，請在該程序宣告。 若要建立一個常數，代表可在整個應用程式，會將它宣告使用`Public`類別的宣告區段中的關鍵字。  
  
> [!NOTE]
>  雖然常數有點類似變數，您無法修改它們，或將新值指派給它們，如同您變數。  
  
 您在程式碼中使用的常數可以定義的物件模型的控制項或元件，或它們可以是使用者定義 （也就是您自己建立）。  
  
## <a name="compile-time-and-run-time-constants"></a>編譯時期和執行階段常數  
 編譯時期常數是在編譯程式碼，而執行階段常數僅計算，在執行應用程式的時間來計算。 編譯時期常數會每次應用程式執行時，雖然執行階段常數可能會變更每次有相同的值。 編譯時期常數是必要的例如陣列界限、 case 運算式或列舉值初始設定式。  
  
## <a name="in-this-section"></a>本章節內容  
  
|定義|詞彙|  
|---|---|  
|[如何：宣告常數](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|說明如何使用`Const`陳述式來宣告常數，並設定其值; 藉由宣告為常數，您必須指派有意義的名稱的值。|  
|[使用者定義的常數](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|描述如何建立您自己的常數，包括設定範圍的詳細資訊，以及如何避免循環參考。|  
|[常數和常值資料類型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|如何提供有關[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器初始化常數時`Option Explicit`已關閉。|  
|[如何：將關聯的常數值群組在一起](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|示範如何以群組相關的常數值。|  
  
## <a name="reference"></a>參考資料  
  
|定義|詞彙|  
|---|---|  
|[常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)|列出預先定義的常數[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。|  
|[Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md)|描述`Const`陳述式和它的用法。|  
|[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|描述`Option Strict`陳述式和它的用法。|  
  
## <a name="see-also"></a>另請參閱  
 [列舉類型的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [如何︰ 在 Visual Basic 中的將陣列變數初始化](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
