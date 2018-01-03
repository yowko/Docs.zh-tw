---
title: "Visual Basic 命名慣例"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 97f02fd85d4796d6799a8a5b40a9137eeb79a93f
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="visual-basic-naming-conventions"></a>Visual Basic 命名慣例
當您在 Visual Basic 應用程式命名項目時，該名稱的第一個字元必須是英數字元或底線。 不過請注意，以底線開頭的名稱不符合[語言獨立性以及與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md)（cls） 標準。  
  
 下列建議適用於命名。  
  
-   在開始以大寫字母，名稱中的每個個別單字`FindLastRecord`和`RedrawMyForm`。  
  
-   具有動詞的函式和方法名稱開頭與`InitNameArray`或`CloseDialog`。  
  
-   在開始類別、 結構、 模組和屬性名稱和名詞，`EmployeeName`或`CarAccessory`。  
  
-   介面名稱前置詞開頭的"I"，後面接著名詞或名詞片語，例如`IComponent`，或形容詞，例如描述介面的行為與`IPersistable`。 請勿使用底線，並且使用縮寫盡量少用，因為縮寫會造成混淆。  
  
-   事件處理常式名稱開頭描述類型的事件，後面接著名詞 」`EventHandler`"後置詞，如下所示"`MouseEventHandler`"。  
  
-   事件引數類別的名稱，包括 「`EventArgs`"後置詞。  
  
-   如果事件的概念 「 之前 」 或 「 之後 」，請使用後置字元中式或過去式，像是 「`ControlAdd`「 或 」`ControlAdded`"。  
  
-   長或常用的條款，請使用保留名稱長度很合理，因為的縮寫，例如"HTML"，而不是 「 超文字標記語言 」。 一般情況下，大於 32 個字元的變數名稱不容易讀取在設定為低解析度的監視器上。 此外，請確定您縮寫是整個應用程式一致。 隨機切換移入 「 HTML 」 和 「 超文字標記語言 」 之間的專案可能會造成混淆。  
  
-   避免使用內部範圍內外部範圍中的名稱相同的名稱。 如果存取錯誤的變數，可能會造成錯誤。 如果之變數與相同名稱的關鍵字之間發生衝突，您必須識別關鍵字前面使用適當的型別程式庫。 例如，如果您擁有名為`Date`，您可以使用內建`Date`函式，只是藉由呼叫<xref:System.DateTime.Date%2A?displayProperty=nameWithType>。  
  
## <a name="see-also"></a>請參閱  
 [程式碼中以關鍵字做為項目名稱](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 [Me、My、MyBase 和 MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Visual Basic 語言參考](../../../visual-basic/language-reference/index.md)
