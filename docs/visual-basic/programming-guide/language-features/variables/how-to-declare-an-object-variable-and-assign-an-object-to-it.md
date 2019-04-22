---
title: HOW TO：宣告物件變數，並在 Visual Basic 中將物件指派給它
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: fb6411efc190dce335422369a8d2bbff564b9523
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819667"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>HOW TO：宣告物件變數，並在 Visual Basic 中將物件指派給它
宣告的變數[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)藉由指定`As Object`中[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)。 將物件指派給這類變數的藉由將物件放在等號 (`=`) 在指派陳述式或初始化子句中。  
  
## <a name="example"></a>範例  
 下列範例會宣告`Object`變數並指派給它的目前執行個體。  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 您可以結合的宣告和指派變數初始化為其宣告的一部分。 下列範例相當於上述的範例。  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   <xref:System> 命名空間的參考。  
  
-   類別、 結構或模組要放入`Dim`陳述式。  
  
-   中要放的指派陳述式的程序。  
  
## <a name="see-also"></a>另請參閱

- [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [物件變數宣告](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
