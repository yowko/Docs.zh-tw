---
title: 屬性 '<propertyname>' 不會在所有程式碼路徑上傳回值
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 21a1c4dbab6e26cd1cb848e270bbda9a544c2a67
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400418"
---
# <a name="property-propertyname-doesnt-return-a-value-on-all-code-paths"></a>屬性 '\<propertyname>' 不會在所有程式碼路徑上傳回值
屬性 ' \<propertyname> ' 不會傳回所有程式碼路徑上的值。 使用結果時，Null 參考例外狀況可能在執行階段時發生。  
  
 屬性 `Get` 程式具有至少一個可能的路徑，而其程式碼不會傳回值。  
  
 您可以 `Get` 使用下列任何一種方式，從屬性程式傳回值：  
  
- 將值指派給屬性名稱，然後執行 `Exit Property` 語句。  
  
- 將值指派給屬性名稱，然後執行 `End Get` 語句。  
  
- 在[Return 語句](../statements/return-statement.md)中包含值。  
  
 如果控制項傳遞至 `Exit Property` 或 `End Get` ，而且您尚未將任何值指派給屬性名稱，則程式會傳回 `Get` 屬性之資料類型的預設值。 如需詳細資訊，請參閱[Function 語句](../statements/function-statement.md)中的「行為」。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼：** BC42107  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 檢查您的控制流程邏輯，並務必在導致傳回的每個語句之前指派一個值。  
  
     如果您一律使用語句，則保證每次從程式傳回的傳回值會比較容易 `Return` 。 如果您這樣做，前面的最後一個語句 `End Get` 應該是 `Return` 語句。  
  
## <a name="see-also"></a>另請參閱

- [屬性程序](../../programming-guide/language-features/procedures/property-procedures.md)
- [Property Statement](../statements/property-statement.md)
- [Get 陳述式](../statements/get-statement.md)
