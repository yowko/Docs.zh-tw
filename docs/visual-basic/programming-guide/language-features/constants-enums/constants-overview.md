---
title: 常數的概觀 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 0c866f3d03d26bd882d5a6596d40d1dc639da011
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934773"
---
# <a name="constants-overview-visual-basic"></a>常數的概觀 (Visual Basic)
常數是有意義的名稱, 用來取代不會變更的數位或字串。 如同名稱所示, 常數會儲存應用程式執行時保持不變的值。 您可以大幅改善程式碼的可讀性, 並讓您更輕鬆地使用常數進行維護。 在程式碼中使用它們, 其中包含重新出現的值, 或取決於不容易記住或沒有明顯意義的特定數位。  
  
## <a name="how-to-create-and-use-constants"></a>如何建立和使用常數  
 Visual Basic 包含許多預先定義的常數, 主要是用來列印和顯示。 您也可以使用`Const`語句來建立自己的常數, 如同建立變數名稱所用的相同方針。 如果`Option Strict` 為`On`, 則您必須明確宣告常數類型。  
  
 常數的範圍, 這是一組可以參考它而不限定其名稱的程式碼, 與相同位置中宣告的變數相同。 若要建立存在於特定程式範圍內的常數, 請在該程式內宣告。 若要建立可在整個應用程式中使用的常數, 請在`Public`類別的宣告區段中使用關鍵字進行宣告。  
  
> [!NOTE]
> 雖然常數有點類似變數, 但是您無法修改它們, 或將新值指派給它們, 就像您可以變數一樣。  
  
 您在程式碼中使用的常數可以由您所使用之控制項或元件的物件模型來定義, 也可以是使用者定義的 (也就是您自行建立的)。  
  
## <a name="compile-time-and-run-time-constants"></a>編譯時間和執行時間常數  
 編譯時間常數會在程式碼編譯時計算, 而執行時間常數則只能在應用程式執行時計算。 每次執行應用程式時, 編譯時間常數將會有相同的值, 而執行時間常數可能會每次都變更。 如陣列界限、case 運算式或列舉值初始化運算式等案例, 則需要編譯時間常數。  
  
## <a name="in-this-section"></a>本節內容  
  
|定義|詞彙|  
|---|---|  
|[如何：宣告常數](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|說明如何使用`Const`語句來宣告常數並設定其值; 藉由宣告常數, 您可以將有意義的名稱指派給值。|  
|[使用者定義的常數](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|描述如何建立您自己的常數, 包括範圍的資訊, 以及如何避免迴圈參考。|  
|[常數和常值資料類型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|提供當關閉時`Option Explicit` , Visual Basic 編譯器如何初始化常數的相關資訊。|  
|[如何：將相關的常數值群組在一起](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|示範如何將相關的常數值群組在一起。|  
  
## <a name="reference"></a>參考資料  
  
|定義|詞彙|  
|---|---|  
|[常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)|列出 Visual Basic 預先定義的常數。|  
|[Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md)|`Const`描述語句及其用法。|  
|[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|`Option Strict`描述語句及其用法。|  
  
## <a name="see-also"></a>另請參閱

- [列舉的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [如何：初始化 Visual Basic 中的陣列變數](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
