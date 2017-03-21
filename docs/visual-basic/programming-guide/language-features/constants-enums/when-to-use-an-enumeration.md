---
title: "何時使用列舉型別 (Visual Basic) |Microsoft 文件"
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
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: f22102a2e1e7eafd7fcf4db1f46af2cc622eba70
ms.lasthandoff: 03/13/2017

---
# <a name="when-to-use-an-enumeration-visual-basic"></a>何時使用列舉 (Visual Basic)
列舉型別能夠讓您輕鬆與集合相關的常數。 列舉，或`Enum`，是一組值的符號名稱。 列舉型別會被視為資料類型，您可以使用它們來建立使用常數之集合的變數和屬性。  
  
## <a name="when-to-use-an-enumeration"></a>何時使用列舉類型  
 每當程序會接受一組有限的變數，請考慮使用列舉型別。 列舉型別可讓更清楚且更容易閱讀的程式碼，特別是當使用有意義的名稱。  
  
 使用列舉型別的優點包括︰  
  
-   減少因調換或輸錯數字的錯誤。  
  
-   可讓您輕鬆地在未來變更的值。  
  
-   讓程式碼更方便閱讀，這表示它是比較不可能的錯誤會蔓延到它。  
  
-   可確保往後相容性。 列舉型別，程式碼就比較不可能失敗，如果有人在未來變更為成員名稱的對應值。  
  
## <a name="naming-enumerations"></a>命名的列舉型別  
 使用列舉型別成員的命名慣例。 當[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]遇到列舉成員名稱可能會擲回例外狀況，如果其他參考的型別程式庫包含相同的名稱。 使用唯一的前置詞來識別您的應用程式或元件的值。  
  
 當參考列舉型別的成員，您必須限定成員名稱的列舉型別名稱，或是使用`Imports`陳述式。 如需詳細資訊，請參閱[列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)。  
  
## <a name="predefined-enumerations"></a>預先定義的列舉型別  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供了數個預先定義的列舉型別，例如`FirstDayOfWeek`和`MsgBoxResul`t，以幫助您的程式碼。 針對這些項目的清單，請參閱[常數和列舉型別](../../../../visual-basic/language-reference/constants-and-enumerations.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何︰ 宣告列舉類型](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [如何︰ 參考列舉成員](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [如何︰ 逐一查看在 Visual Basic 中列舉類型](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [如何︰ 決定與列舉值關聯的字串](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [Enum 陳述式](../../../../visual-basic/language-reference/statements/enum-statement.md)   
 [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)
