---
title: 常數的概觀 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 34f3dee4edba58375c5c84b579e39a8a29ebc1bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737685"
---
# <a name="constants-overview-visual-basic"></a>常數的概觀 (Visual Basic)
常數是有意義的名稱來取代數字或字串，不會變更。 常數用來儲存值，如同名稱所暗示，維持不變執行作業的應用程式。 您可以大幅改善您的程式碼的可讀性，並輕鬆地維護藉由使用常數。 在包含的值會重複出現的程式碼中使用它們，或相依於某些很難記住，或沒有任何明顯的意義的數字。  
  
## <a name="how-to-create-and-use-constants"></a>如何建立和使用常數  
 Visual Basic 會包含許多預先定義的常數，主要用於列印與顯示。 您也可以建立自己的常數，與`Const`陳述式中，使用相同的指導方針，您會建立變數的名稱。 如果`Option Strict`是`On`，您必須明確宣告常數的類型。  
  
 常數的範圍內，也就是變數的可以參考未限定其名稱的所有程式碼的集合，是變數的在相同的位置所宣告相同。 若要建立特定的程序的範圍內存在的常數，請在該程序內宣告。 若要建立一個常數，代表可在整個應用程式，將它使用宣告`Public`類別的 「 宣告 」 區段中的關鍵字。  
  
> [!NOTE]
>  雖然常數有點類似於變數，您無法修改它們，或將新的值指派給它們，如同您變數。  
  
 您在您的程式碼中使用的常數可以定義控制項或元件使用的物件模型，或它們可以是使用者定義 （也就是您建立您自己）。  
  
## <a name="compile-time-and-run-time-constants"></a>編譯時期和執行階段常數  
 編譯時期常數是在程式碼會編譯，而應用程式執行時，您可以只將計算的執行階段常數時間來計算。 每次應用程式執行時，雖然執行階段常數可能會在每次變更時，編譯時間常數會有相同的值。 編譯時期常數不需要在陣列界限，case 運算式或列舉值的初始設定式的情況。  
  
## <a name="in-this-section"></a>本節內容  
  
|定義|詞彙|  
|---|---|  
|[如何：宣告常數](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|說明如何使用`Const`陳述式來宣告常數，並將它的值; 藉由宣告為常數，您必須指派有意義的名稱的值。|  
|[使用者定義的常數](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|描述如何建立您自己的常數，包括設定範圍的詳細資訊，以及如何避免循環參考。|  
|[常數和常值資料類型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|提供有關 Visual Basic 編譯器如何初始化常數時`Option Explicit`已關閉。|  
|[如何：群組關聯的常數值在一起](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|示範如何將群組相關的常數值。|  
  
## <a name="reference"></a>參考資料  
  
|定義|詞彙|  
|---|---|  
|[常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)|列出預先定義的 Visual basic 的常數。|  
|[Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md)|描述`Const`陳述式和它的用法。|  
|[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|描述`Option Strict`陳述式和它的用法。|  
  
## <a name="see-also"></a>另請參閱
- [列舉的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [如何：初始化陣列變數在 Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
