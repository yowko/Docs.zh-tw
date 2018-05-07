---
title: 常數的概觀 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 2ec43254013df5444048b5197489c55217d5328a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="constants-overview-visual-basic"></a>常數的概觀 (Visual Basic)
常數是有意義的名稱來取代數字或字串，不會變更。 常數用來儲存值，正如其名，維持不變，整個應用程式執行。 您可以大幅改善您的程式碼的可讀性，並更輕鬆地維護藉由使用常數。 在包含的值會重複出現的程式碼中使用它們，或相依於某些很難記住，或沒有明顯意義的數字。  
  
## <a name="how-to-create-and-use-constants"></a>如何建立和使用常數  
 Visual Basic 包含許多預先定義的常數，主要用於列印或顯示。 您也可以建立自己的常數與`Const`陳述式中，使用相同的指導方針，您會建立變數的名稱。 如果`Option Strict`是`On`，您必須明確宣告的常數類型。  
  
 常數的範圍，這是可以參考它而不需要限定其名稱的所有程式碼組，等同於在相同的位置所宣告的變數。 若要建立有特定的程序的範圍內的常數，請在該程序內宣告。 若要建立一個常數，代表可在整個應用程式，會將它宣告使用`Public`類別的宣告區段中的關鍵字。  
  
> [!NOTE]
>  雖然常數有點類似於變數，您無法加以修改，或為其指派新值到變數。  
  
 您在程式碼中使用的常數可以定義控制項或元件使用的物件模型，或它們可以是使用者定義 （也就是您自己建立）。  
  
## <a name="compile-time-and-run-time-constants"></a>編譯時間和執行階段常數  
 在程式碼會編譯，執行階段常數只計算，在執行應用程式時的時間計算編譯時間常數。 每次執行應用程式，而每次可能會變更執行階段常數時，編譯時期常數會具有相同的值。 編譯時期常數所需的情況下，例如陣列界限、 case 運算式或列舉值的初始設定式。  
  
## <a name="in-this-section"></a>本節內容  
  
|定義|詞彙|  
|---|---|  
|[如何：宣告常數](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|說明如何使用`Const`陳述式來宣告常數，並設定其值; 宣告為常數，您必須指派有意義的名稱的值。|  
|[使用者定義的常數](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|描述如何建立您自己的常數，包括設定範圍的詳細資訊，以及如何避免循環參考。|  
|[常數和常值資料類型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|提供 Visual Basic 編譯器如何初始化常數的相關資訊時`Option Explicit`已關閉。|  
|[如何：將關聯的常數值群組在一起](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|示範如何以群組相關的常數值。|  
  
## <a name="reference"></a>參考資料  
  
|定義|詞彙|  
|---|---|  
|[常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)|列出預先定義的 Visual Basic 的常數。|  
|[Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md)|描述`Const`陳述式和其使用。|  
|[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|描述`Option Strict`陳述式和其使用。|  
  
## <a name="see-also"></a>另請參閱  
 [列舉的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [如何：在 Visual Basic 中初始化陣列變數](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
