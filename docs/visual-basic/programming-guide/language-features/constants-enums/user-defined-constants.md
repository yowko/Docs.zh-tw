---
title: 使用者定義的常數
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: 351bdb6963e278341c13e53ef19aea0876010aa9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095638"
---
# <a name="user-defined-constants-visual-basic"></a>使用者定義常數 (Visual Basic)

常數是有意義的名稱，用來取代未變更的數位或字串。 如同它的名稱所示，常數用來儲存應用程式執行過程中維持不變的值。 您可以使用由您處理的控制項或元件所定義的常數，也可以建立自己的常數。 您自行建立的常數會以 *使用者定義*的方式描述。  
  
 您可以 `Const` 使用語句來宣告常數，並使用您用來建立變數名稱的相同指導方針。 如果 `Option Strict` 為 `On` ，則您必須明確宣告常數型別。  
  
## <a name="const-statement-usage"></a>Const 語句使用方式  

 `Const`語句可以表示數學或日期/時間數量：  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 它也可以定義 `String` 常數：  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 等號 ( ) 右邊的運算式 `=` 通常是數位或常值字串，但也可以是會產生數位或字串 (的運算式，但該運算式不能包含) 函數的呼叫。 您甚至可以根據先前定義的常數來定義常數：  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a>使用者定義常數的範圍  

 `Const`語句的範圍與在相同位置中宣告之變數的範圍相同。 您可以利用下列任何一種方式來指定範圍：  
  
- 若要建立只存在於程式內的常數，請在該程式中宣告它。  
  
- 若要建立類別內的所有程式都可使用的常數，而不是在該模組以外的任何程式碼中，請在類別的宣告區段中宣告它。  
  
- 若要建立可供元件的所有成員使用的常數，而不是元件外部用戶端的常數，請 `Friend` 在類別的宣告區段中使用關鍵字來宣告。  
  
- 若要在整個應用程式中建立可用的常數，請 `Public` 在類別的宣告區段中使用關鍵字來宣告。  
  
 如需詳細資訊，請參閱 [如何：宣告常數](how-to-declare-a-constant.md)。  
  
### <a name="avoiding-circular-references"></a>避免迴圈參考  

 因為常數可以根據其他常數來定義，所以可能會在兩個或多個常數之間不慎建立 *迴圈*或迴圈參考。 當您有兩個或多個公用常數時，就會發生迴圈，如下列範例所示：  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 如果發生迴圈，Visual Basic 會產生編譯器錯誤。  
  
## <a name="see-also"></a>另請參閱

- [Const 陳述式](../../../language-reference/statements/const-statement.md)
- [常數和常值資料類型](constant-and-literal-data-types.md)
- [常數和列舉](index.md)
- [常數和列舉](../../../language-reference/constants-and-enumerations.md)
- [列舉的概觀](enumerations-overview.md)
- [常數的概觀](constants-overview.md)
- [如何：宣告列舉類型](how-to-declare-enumerations.md)
- [列舉和名稱限定性條件](enumerations-and-name-qualification.md)
- [Long](../../../language-reference/statements/option-strict-statement.md)
