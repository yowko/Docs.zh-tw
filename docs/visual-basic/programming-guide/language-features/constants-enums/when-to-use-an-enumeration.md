---
title: 何時使用列舉類型
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: ba69249e16b8c0ee06d57d06d192874a283b295e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403533"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>何時使用列舉 (Visual Basic)
列舉提供了一種簡單的方式來處理相關的常數集合。 列舉（或 `Enum` ）是一組值的符號名稱。 列舉會視為資料類型，您可以使用它們來建立常數集，以便搭配變數和屬性使用。  
  
## <a name="when-to-use-an-enumeration"></a>何時使用列舉類型  
 每當程式接受一組有限的變數時，請考慮使用列舉。 列舉會產生更清楚且更容易閱讀的程式碼，特別是在使用有意義的名稱時。  
  
 使用列舉的優點包括：  
  
- 減少因轉置或錯誤的數位而造成的錯誤。  
  
- 可讓您在未來輕鬆變更值。  
  
- 讓程式碼更容易閱讀，這表示錯誤不太可能會蔓延到其中。  
  
- 確保向前相容性。 使用列舉時，如果未來有人變更對應至成員名稱的值，您的程式碼較不可能失敗。  
  
## <a name="naming-enumerations"></a>命名列舉  
 使用列舉成員的命名慣例。 當 Visual Basic 遇到列舉成員名稱時，如果其他參考的類型程式庫包含相同的名稱，則可能會擲回例外狀況（exception）。 使用唯一的前置詞，以識別來自您應用程式或元件的值。  
  
 當參考列舉的成員時，您必須以列舉名稱限定成員名稱，否則請使用 `Imports` 語句。 如需詳細資訊，請參閱列舉[和名稱限定](enumerations-and-name-qualification.md)性。  
  
## <a name="predefined-enumerations"></a>預先定義的列舉  
 Visual Basic 提供許多預先定義的列舉（例如 `FirstDayOfWeek` 和 `MsgBoxResult` ），以協助您的程式碼。 如需這些[常數和](../../../language-reference/constants-and-enumerations.md)列舉的清單，請參閱。  
  
## <a name="see-also"></a>另請參閱

- [如何：宣告列舉類型](how-to-declare-enumerations.md)
- [如何：參考列舉類型成員](how-to-refer-to-an-enumeration-member.md)
- [列舉和名稱限定性條件](enumerations-and-name-qualification.md)
- [如何：在 Visual Basic 中逐一查看列舉類型](how-to-iterate-through-an-enumeration.md)
- [如何：決定與列舉值相關聯的字串](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [End 陳述式](../../../language-reference/statements/enum-statement.md)
- [常數和列舉](../../../language-reference/constants-and-enumerations.md)
