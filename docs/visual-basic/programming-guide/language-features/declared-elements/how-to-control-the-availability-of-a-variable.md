---
title: 如何：控制變數的可用性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
ms.openlocfilehash: 27ee5d3405ea24c0754cffa85e9b89b2ac561e42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652164"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>如何：控制變數的可用性 (Visual Basic)
指定控制變數的可用性其*存取層級*。 存取層級決定何種程式碼有權讀取或寫入的變數。  
  
-   *成員變數*（定義在模組層級以及任何程序之外） 預設為公用存取，這表示可以看到它們的任何程式碼可以存取它們。 您可以指定存取修飾詞來變更。  
  
-   *本機變數*（定義在程序） 名義具有公用存取，雖然其程序內的程式碼可以存取它們。 您無法變更存取層級的區域變數，但您可以變更包含它的程序的存取層級。  
  
 如需詳細資訊，請參閱[存取 Visual Basic 中的層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="private-and-public-access"></a>私人和公用存取  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>若要存取只會從其模組、 類別或結構中的變數  
  
1.  位置[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)變數內模組、 類別或結構，但以外的任何程序。  
  
2.  包含[私人](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字`Dim`陳述式。  
  
     您可以讀取或寫入變數從模組、 類別或結構中的任何位置，而不是從外部。  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>若要存取的任何程式碼，可以看到變數  
  
1.  為成員變數，請將`Dim`變數內模組、 類別或結構，但以外的任何程序陳述式。  
  
2.  包含[公用](../../../../visual-basic/language-reference/modifiers/public.md)關鍵字`Dim`陳述式。  
  
     您可以讀取或寫入至變數從相互操作的任何程式碼與組件。  
  
 -或-  
  
1.  為區域變數，請將`Dim`陳述式的程序內的變數。  
  
2.  不包含`Public`關鍵字`Dim`陳述式。  
  
     您可以讀取或寫入變數，從程序中的任何位置，而不是從外部。  
  
## <a name="protected-and-friend-access"></a>保護和 Friend 存取權限  
 您可以限制變數對其類別和任何衍生的類別，或其組件的存取層級。 您也可以指定這些限制，讓存取的程式碼，在任何衍生類別中或在相同的組件中的任何其他地方的聯集。 您指定這個聯集結合`Protected`和`Friend`相同宣告中的關鍵字。  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>若要只能從其類別和任何衍生的類別中存取變數  
  
1.  位置`Dim`陳述式的類別內部，但任何程序之外的變數。  
  
2.  包含[保護](../../../../visual-basic/language-reference/modifiers/protected.md)關鍵字`Dim`陳述式。  
  
     您可以讀取或寫入變數，從類別內的任何位置，以及從任何類別衍生，而不是從外部衍生鏈結中的任何類別。  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>若要在相同的組件內只能從存取變數  
  
1.  位置`Dim`變數內模組、 類別或結構，但以外的任何程序陳述式。  
  
2.  包含[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)關鍵字`Dim`陳述式。  
  
     您可以讀取或寫入變數從模組、 類別或結構中的任何位置，以及從任何程式碼相同的組件，而不是從外部組件。  
  
## <a name="example"></a>範例  
 下列範例顯示的變數宣告`Public`， `Protected`， `Friend`， `Protected Friend`，和`Private`存取層級。 請注意，當`Dim`陳述式指定的存取層級，您不需要包含`Dim`關鍵字。  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 更嚴格的變數的存取層級，小惡意程式碼的機會使用它。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中的存取層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Public](../../../../visual-basic/language-reference/modifiers/public.md)  
 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [Private](../../../../visual-basic/language-reference/modifiers/private.md)
