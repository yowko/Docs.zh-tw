---
title: "其他資料類型 (Visual Basic) |Microsoft 文件"
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
- Object data type, data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: 22
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
ms.openlocfilehash: 2de377fa9dfd7ec13cdbb9b700f8485b0c0e2106
ms.lasthandoff: 03/13/2017

---
# <a name="miscellaneous-data-types-visual-basic"></a>其他資料類型 (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供數個不導向數字或字元資料型別。 相反地，它們會處理特定資料例如是/否值、 日期/時間值和物件位址。  
  
 顯示由並排比較資料表[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]資料類型，請參閱[資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md)。  
  
## <a name="boolean-type"></a>布林型別  
 [布林資料型別](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)是不帶正負號的值會解譯為`True`或`False`。 資料寬度取決於實作平台。 如果是/否或是開/關變數可以包含只有兩個狀態值 true/false 時，例如，將它宣告為`Boolean`。  
  
## <a name="date-type"></a>日期類型  
 [日期資料型別](../../../../visual-basic/language-reference/data-types/date-data-type.md)是保存日期和時間資訊的 64 位元值。 每個增量 100 奈秒的時間 （上午 12:00） 開始之後的西曆的 1 年月 1。 如果變數可以包含日期值、 時間值，或兩者，將它宣告為`Date`。  
  
## <a name="object-type"></a>物件類型  
 [Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md)是指向您的應用程式或其他應用程式中的物件執行個體的 32 位元位址。 `Object`變數可以參考您的應用程式可辨識的任何物件或任何資料類型的資料。 這同時包含*實值型別*，例如`Integer`， `Boolean`，和結構的執行個體，和*參考型別*，例如從類別建立物件的執行個體`String`和<xref:System.Windows.Forms.Form>，和陣列執行個體。</xref:System.Windows.Forms.Form>  
  
 如果變數是儲存您不知道在編譯時期，類別的執行個體的指標，或可以指向各種資料類型的資料，將它宣告為`Object`。  
  
 利用`Object`資料型別是，可以用它來儲存任何資料類型的資料。 缺點是，您需支付額外的作業，可以執行更多的時間，使得應用程式執行變慢。 如果您使用`Object`實值型別變數，則會產生*boxing*和*unboxing*。 如果您使用參考類型，則會產生*晚期繫結*。  
  
## <a name="see-also"></a>另請參閱  
 [類型字元](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [基本資料型別](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [數值資料類型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)   
 [字元資料類型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)   
 [資料類型疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [早期和晚期繫結](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
