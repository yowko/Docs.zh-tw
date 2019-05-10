---
title: HOW TO：控制變數 (Visual Basic) 的可用性
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
ms.openlocfilehash: 419f3eed30a5d4b35bcb9dde5242b9092ee9cb79
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610492"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>HOW TO：控制變數 (Visual Basic) 的可用性
指定控制變數的可用性及其*存取層級*。 存取層級會判斷哪些程式碼有權讀取或寫入變數。  
  
- *成員變數*（定義在模組層級和任何程序之外） 預設為公用存取，這表示可以看到它們的任何程式碼可以存取它們。 您可以藉由指定的存取修飾詞來變更此設定。  
  
- *本機變數*（程序內所定義的） 名義上具有公用存取，但其程序內的程式碼可以存取它們。 您無法變更存取層級的區域變數，但您可以變更包含它的程序的存取層級。  
  
 如需詳細資訊，請參閱 <<c0> [ 存取 Visual Basic 中的層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="private-and-public-access"></a>私用和公用存取  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>若要存取只能從其模組、 類別或結構中的變數  
  
1. 地方[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)內模組、 類別或結構，但在任何程序之外的變數。  
  
2. 包含[私人](../../../../visual-basic/language-reference/modifiers/private.md)中的關鍵字`Dim`陳述式。  
  
     您可以讀取或寫入變數，從模組、 類別或結構內的任何位置，而不是從其外部。  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>若要從任何可以看到它的程式碼存取變數  
  
1. 成員變數，將`Dim`變數內模組、 類別或結構，但以外的任何程序的陳述式。  
  
2. 包含[公開金鑰](../../../../visual-basic/language-reference/modifiers/public.md)中的關鍵字`Dim`陳述式。  
  
     您可以讀取或寫入變數的交互操作的任何程式碼與您的組件。  
  
 -或-  
  
1. 本機變數中，放置`Dim`程序內變數的陳述式。  
  
2. 不包含`Public`中的關鍵字`Dim`陳述式。  
  
     您可以讀取或寫入變數，從程序中的任何位置，而不是從其外部。  
  
## <a name="protected-and-friend-access"></a>受保護和 Friend 存取權限  
 您可以限制變數對其類別和衍生的類別，或其組件的存取層級。 您也可以指定這些限制，可讓您從程式碼的存取相同的組件中的任何其他位置或任何衍生類別中的聯集。 您指定這個聯集結合`Protected`和`Friend`相同宣告中的關鍵字。  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>若要在其類別和任何衍生的類別內只能從存取變數  
  
1. 位置`Dim`陳述式的類別，但任何程序之外的變數。  
  
2. 包含[Protected](../../../../visual-basic/language-reference/modifiers/protected.md)中的關鍵字`Dim`陳述式。  
  
     您可以讀取或寫入變數，從任何地方在類別中，以及從任何類別衍生，而不是從衍生鏈結中的任何類別外部。  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>若要只能從相同的組件中存取變數  
  
1. 位置`Dim`變數內模組、 類別或結構，但以外的任何程序的陳述式。  
  
2. 包含[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)中的關鍵字`Dim`陳述式。  
  
     您可以讀取或寫入變數，從模組、 類別或結構內的任何位置，以及從任何程式碼位於相同的組件，而不是從外部組件。  
  
## <a name="example"></a>範例  
 下列範例顯示的變數宣告`Public`， `Protected`， `Friend`， `Protected Friend`，和`Private`存取層級。 請注意，當`Dim`陳述式會指定存取層級，您不需要包含`Dim`關鍵字。  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 更嚴格變數的存取層級，它使用較小的機會，惡意程式碼不適當。  
  
## <a name="see-also"></a>另請參閱

- [在 Visual Basic 中的存取層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Public](../../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../../visual-basic/language-reference/modifiers/private.md)
