---
title: "其他資料類型 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6bb86bb6d203aa4e6bdded27a4cb78a8155ddec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="miscellaneous-data-types-visual-basic"></a>其他資料類型 (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]提供數個不導向數字或字元資料型別。 相反地，它們可以處理特定資料這類是/否值、 日期/時間值和物件位址。  
  
 顯示並行所比較資料表[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]資料類型，請參閱[資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md)。  
  
## <a name="boolean-type"></a>布林型別  
 [布林資料型別](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)是解譯為不帶正負號的值`True`或`False`。 它的資料寬度取決於實作的平台。 如果是/否，或開啟/關閉變數可以包含只有兩個狀態例如 true/false 的值，將它宣告為`Boolean`。  
  
## <a name="date-type"></a>Date 類型  
 [日期資料型別](../../../../visual-basic/language-reference/data-types/date-data-type.md)是保存日期和時間資訊的 64 位元值。 每個增量代表 100 奈秒的經過時間 （上午 12:00） 起西曆日曆 1 年的 1 年 1 月。 如果變數可以包含值，日期、 時間值，或兩者，將它宣告為`Date`。  
  
## <a name="object-type"></a>物件類型  
 [物件資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)是指向您的應用程式或某些其他應用程式中的物件執行個體的 32 位元位址。 `Object`變數可以參考任何物件，辨識您的應用程式，或任何資料類型的資料。 同時包含這*實值類型*，例如`Integer`， `Boolean`，和結構的執行個體，和*參考型別*，這是執行個體的物件透過類別建立的例如`String`和<xref:System.Windows.Forms.Form>，以及陣列執行個體。  
  
 如果變數是儲存您不知道在編譯時期，類別的執行個體的指標，或可以指向不同的資料類型的資料，將它宣告為`Object`。  
  
 優點`Object`資料類型是，您可以使用它來儲存任何資料類型的資料。 缺點是會產生額外的作業，需要更多的執行時間，使得您的應用程式執行變慢。 如果您使用`Object`實值類型變數，您會產生*boxing*和*unboxing*。 如果您使用參考類型，就發生*晚期繫結*。  
  
## <a name="see-also"></a>另請參閱  
 [類型字元](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [基礎資料類型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [數值資料類型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [字元資料類型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [早期和晚期繫結](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
