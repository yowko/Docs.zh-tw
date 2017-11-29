---
title: "Visual Basic 中的存取層級"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- members [Visual Basic], accessing in Visual Basic
- Friend access modifier
- access levels, declared elements
- access levels
- access modifiers
- Public access modifier
- Protected access modifier
- Protected Friend access modifier
- Private access modifier
- declared elements [Visual Basic], access level
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 87e43ac7e813cece1179bdaf24c86fa62adcb438
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="access-levels-in-visual-basic"></a>Visual Basic 中的存取層級
*存取層級*的宣告的項目存取它的範圍，也就是何種程式碼具有讀取或寫入其中的權限。 這決定您如何宣告項目本身，不僅可以也的項目容器的存取層級。 無法存取包含的項目中的程式碼無法存取任何其包含的項目，即使這些宣告為`Public`。 例如，`Public`變數中`Private`結構從存取類別的一部分，其中包含結構，而不是從該類別之外。  
  
## <a name="public"></a>Public  
 [公用](../../../../visual-basic/language-reference/modifiers/public.md)關鍵字宣告陳述式中的指定的項目可以在從程式碼在同一個專案中的任何位置、 其他參考該專案的專案和專案所建立的任何組件存取。 下列程式碼顯示範例`Public`宣告。  
  
```  
Public Class classForEverybody  
```  
  
 您可以使用`Public`只能在模組、 介面或命名空間層級。 這表示您可以宣告在原始程式檔或命名空間，或介面、 模組、 類別或結構，但不是在程序層級的公用項目。  
  
## <a name="protected"></a>Protected  
 [保護](../../../../visual-basic/language-reference/modifiers/protected.md)關鍵字宣告陳述式中的指定的項目可存取只會從相同的類別，或從衍生自這個類別的類別中。 下列程式碼顯示範例`Protected`宣告。  
  
```  
Protected Class classForMyHeirs  
```  
  
 您可以使用`Protected`只能在類別層級，而且只有當您宣告類別的成員。 這表示您可以宣告在類別中，但不是在原始程式檔或命名空間，或介面、 模組、 結構或程序內的層級的受保護項目。  
  
## <a name="friend"></a>Friend  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)宣告陳述式中的關鍵字會指定從可以存取的項目，在相同的組件內，而不是從外部組件。 下列程式碼顯示範例`Friend`宣告。  
  
```  
Friend stringForThisProject As String  
```  
  
 您可以使用`Friend`只能在模組、 介面或命名空間層級。 這表示您可以宣告 friend 項目層級的來源檔案或命名空間，或介面、 模組、 類別或結構，但不是在程序。  
  
## <a name="protected-friend"></a>Protected 的 Friend  
 `Protected`和`Friend`關鍵字宣告陳述式中同時指定衍生類別，或是從項目，可以存取相同組件，或兩者。 下列程式碼顯示範例`Protected Friend`宣告。  
  
```  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 您可以使用`Protected Friend`只能在類別層級，而且只有當您宣告類別的成員。 這表示您可以宣告為 protected 的 friend 項目在類別中，但不是在原始程式檔或命名空間，或介面、 模組、 結構或程序內的層級。  
  
## <a name="private"></a>Private  
 [私人](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字宣告陳述式中的指定項目可以存取只能從，在相同的模組、 類別或結構內。 下列程式碼顯示範例`Private`宣告。  
  
```  
Private numberForMeOnly As Integer  
```  
  
 您只能在模組層級使用 `Private`。 這表示您可以宣告私用的項目內模組、 類別或結構，但不是在原始程式檔或命名空間、 介面或程序中的層級。  
  
 在模組層級`Dim`陳述式不含任何存取層級關鍵字相當於`Private`宣告。 不過，您可能想要使用`Private`關鍵字，讓您的程式碼更容易閱讀及解譯。  
  
## <a name="access-modifiers"></a>存取修飾詞  
 指定存取層級的關鍵字稱為*存取修飾詞*。 下表比較的存取修飾詞。  
  
|存取修飾詞|授與存取層級|您可以宣告具有此存取層級項目|宣告內容中，您可以使用此修飾詞|  
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|  
|`Public`|不受限制的：<br /><br /> 可以看到公用項目中的任何程式碼可以存取它|介面<br /><br /> 模組<br /><br /> 類別<br /><br /> 結構<br /><br /> 結構成員<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|原始程式檔<br /><br /> 命名空間<br /><br /> 介面<br /><br /> 模組<br /><br /> 類別<br /><br /> 結構|  
|`Protected`|衍生：<br /><br /> 在類別宣告為受保護的項目或從其衍生的類別可以存取之項目的程式碼|介面<br /><br /> 類別<br /><br /> 結構<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|類別|  
|`Friend`|組件︰<br /><br /> 宣告 friend 項目可以存取它的組件中的程式碼|介面<br /><br /> 模組<br /><br /> 類別<br /><br /> 結構<br /><br /> 結構成員<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|原始程式檔<br /><br /> 命名空間<br /><br /> 介面<br /><br /> 模組<br /><br /> 類別<br /><br /> 結構|  
|`Protected` `Friend`|等位的`Protected`和`Friend`:<br /><br /> 在相同類別或為受保護的 friend 項目，或在任何衍生自的項目類別的類別中的相同組件中的程式碼後，即可存取|介面<br /><br /> 類別<br /><br /> 結構<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|類別|  
|`Private`|宣告內容：<br /><br /> 宣告私用的項目，包括所包含的型別內的程式碼可以存取之項目的型別中的程式碼|介面<br /><br /> 類別<br /><br /> 結構<br /><br /> 結構成員<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|模組<br /><br /> 類別<br /><br /> 結構|  
  
## <a name="see-also"></a>另請參閱  
 [Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)  
 [宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [在 Visual Basic 中的存留期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [如何：控制變數的可用性](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)  
 [變數](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
