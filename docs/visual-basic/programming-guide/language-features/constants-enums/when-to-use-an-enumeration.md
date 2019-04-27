---
title: 何時使用列舉 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: ff2d8c324aee8bbccef050c020e5392368b05b1c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907305"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>何時使用列舉 (Visual Basic)
列舉型別能夠讓您輕鬆使用相關常數組。 列舉，或`Enum`，是一組值的符號名稱。 列舉型別會被視為資料類型，您可以使用它們來建立變數和屬性集之常數的使用。  
  
## <a name="when-to-use-an-enumeration"></a>何時使用列舉類型  
 每當程序會接受一組有限的變數，請考慮使用列舉型別。 列舉型別進行更清楚且更容易閱讀的程式碼，尤其是使用有意義的名稱。  
  
 使用列舉型別的優點包括：  
  
-   減少調換，或輸入數字的錯誤所造成的錯誤。  
  
-   可讓您輕鬆地在未來變更的值。  
  
-   讓程式碼更方便閱讀，這表示它不太可能的錯誤會蔓延到其中。  
  
-   可確保往後相容性。 列舉型別，與您的程式碼是比較不可能失敗，如果有人在未來變更為成員名稱的對應值。  
  
## <a name="naming-enumerations"></a>命名的列舉型別  
 列舉成員，請使用命名慣例。 當 Visual Basic 會遇到的列舉型別成員名稱時，如果其他參考的型別程式庫包含相同的名稱可能會擲回例外狀況。 使用唯一的前置詞來識別您的應用程式或元件的值。  
  
 當參考的列舉型別成員，您必須限定成員名稱與列舉型別名稱，或是使用`Imports`陳述式。 如需詳細資訊，請參閱 <<c0> [ 列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)。  
  
## <a name="predefined-enumerations"></a>預先定義的列舉型別  
 Visual Basic 中提供數個預先定義的列舉型別，例如`FirstDayOfWeek`和`MsgBoxResult`，以協助您的程式碼。 如需相關清單請參閱 <<c0> [ 常數和列舉型別](../../../../visual-basic/language-reference/constants-and-enumerations.md)。  
  
## <a name="see-also"></a>另請參閱

- [如何：宣告列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [如何：參考列舉成員](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [列舉和名稱限定性條件](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [如何：逐一查看 Visual Basic 中列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [如何：決定與列舉值關聯的字串](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Enum 陳述式](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)
