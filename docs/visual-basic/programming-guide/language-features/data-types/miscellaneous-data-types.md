---
title: 其他資料類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: 4808d87322d5b21b70ec38e2eb31b2b204938745
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821761"
---
# <a name="miscellaneous-data-types-visual-basic"></a>其他資料類型 (Visual Basic)
Visual Basic 提供幾種資料類型不是目標數字或字元。 相反地，它們會處理特殊資料這類是/否值，日期/時間值和物件位址。  
  
 資料表中顯示的 Visual Basic 資料類型的並排顯示比較，請參閱[資料型別](../../../../visual-basic/language-reference/data-types/index.md)。  
  
## <a name="boolean-type"></a>布林值類型  
 [布林資料型別](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)是不帶正負號的值，會解譯為其中一個`True`或`False`。 它的資料寬度取決於實作的平台。 如果是/否或是開/關，變數可以包含只有兩個狀態例如 true/false 的值，將它宣告為`Boolean`。  
  
## <a name="date-type"></a>日期類型  
 [日期資料型別](../../../../visual-basic/language-reference/data-types/date-data-type.md)是 64 位元值，會保留日期和時間資訊。 每個增量會代表西曆日曆 1 年的 1 年 1 月開始 （上午 12:00） 之後的經過時間的 100 奈秒。 如果變數可以包含日期值、 時間值，或兩者，將它宣告為`Date`。  
  
## <a name="object-type"></a>物件類型  
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)是指向您的應用程式或其他一些應用程式中的物件執行個體的 32 位元位址。 `Object`變數可以參考任何物件辨識出您的應用程式，或任何資料類型的資料。 這同時包含*實值型別*，這類`Integer`， `Boolean`，和結構的執行個體，並*參考型別*，這是執行個體，例如建立類別的物件`String`和<xref:System.Windows.Forms.Form>，和陣列執行個體。  
  
 如果變數會儲存在編譯時期不知道類別的執行個體的指標，或者它可以指向各種資料類型的資料，將它宣告為`Object`。  
  
 利用`Object`資料型別時，您可以使用它來儲存任何資料類型的資料。 缺點是會產生額外的作業需要更多的執行時間，讓您的應用程式執行速度變慢。 如果您使用`Object`實值型別變數，您需要支付*boxing*並*unboxing*。 如果您使用參考型別，會產生*晚期繫結*。  
  
## <a name="see-also"></a>另請參閱

- [類型字元](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [基礎資料類型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [數值資料類型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [字元資料類型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [早期和晚期繫結](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
