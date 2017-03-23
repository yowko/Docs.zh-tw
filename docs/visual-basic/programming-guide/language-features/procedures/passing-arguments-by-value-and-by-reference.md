---
title: "傳遞引數以傳值或傳址 (Visual Basic) |Microsoft 文件"
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
- ByRef keyword, passing arguments by reference
- Visual Basic code, procedures
- passing arguments, by value or by reference
- ByVal keyword, passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing, by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
caps.latest.revision: 23
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
ms.openlocfilehash: 56d1ceba14020ca7f3dc750c2318efd3e9586af0
ms.lasthandoff: 03/13/2017

---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>以傳值和傳址方式傳遞引數 (Visual Basic)
在[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，您可以將引數傳遞至程序*值*或*傳*。 這稱為*傳遞機制*，它決定程序是否可以修改呼叫程式碼中的引數的程式設計項目。 程序宣告判斷每個參數的傳遞機制，藉由指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字。  
  
## <a name="distinctions"></a>差異  
 在將引數傳遞至程序，請注意數個彼此互動的不同差異︰  
  
-   基礎的程式設計項目是否為可修改  
  
-   引數本身是否為可修改  
  
-   傳值或傳址是否傳遞引數  
  
-   引數資料型別是否為實值類型或參考型別  
  
 如需詳細資訊，請參閱[修改之間的差異和不可修改引數](./differences-between-modifiable-and-nonmodifiable-arguments.md)和[差異之間傳遞引數的值和傳址](./differences-between-passing-an-argument-by-value-and-by-reference.md)。  
  
## <a name="choice-of-passing-mechanism"></a>選擇的傳遞機制  
 您應該選擇每個引數仔細的傳遞機制。  
  
-   **保護**。 在兩種傳遞機制之間選擇，最重要的準則是呼叫變更變數的風險。 傳遞引數的好處`ByRef`是程序可以傳回呼叫程式碼，透過該引數的值。 傳遞引數的好處`ByVal`是它可以避免變數被更改程序。  
  
-   **效能**。 雖然傳遞機制會影響您的程式碼的效能，差別在於通常並不顯著。 唯一的例外是傳遞實值型別`ByVal`。 在此情況下，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]複製整個資料內容的引數。 因此，例如結構是大型值型別，它可能會更有效率，將它傳遞`ByRef`。  
  
     參考類型的資料指標是複製 （四個位元組 32 位元平台，在 64 位元平台上的 8 個位元組）。 因此，您可以將型別的引數傳遞`String`或`Object`值而不會損害效能。  
  
## <a name="determination-of-the-passing-mechanism"></a>判斷的傳遞機制  
 程序宣告會指定每個參數的傳遞機制。 呼叫程式碼無法覆寫`ByVal`機制。  
  
 如果參數以宣告`ByRef`，呼叫程式碼可以強制機制`ByVal`引數名稱括在括號內呼叫。 如需詳細資訊，請參閱[如何︰ 強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)。  
  
 在預設[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]是以傳值方式傳遞引數。  
  
## <a name="when-to-pass-an-argument-by-value"></a>傳值方式傳遞引數的時機  
  
-   如果引數呼叫的程式碼項目是不可修改的項目，將對應的參數宣告[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。 程式碼不可以變更不可修改的元素的值。  
  
-   如果對應的項目是可修改，但您不想要能夠變更其值的程序，將參數宣告`ByVal`。 呼叫程式碼可以變更可修改的項目，以傳值方式傳遞的值。  
  
## <a name="when-to-pass-an-argument-by-reference"></a>傳址方式傳遞引數的時機  
  
-   如果程序確實需要變更對應的項目，在呼叫程式碼中，宣告對應參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。  
  
-   如果正確執行的程式碼相依於程序來變更呼叫的程式碼對應的項目，將參數宣告`ByRef`。 如果您傳遞的值，或如果呼叫程式碼會覆寫`ByRef`傳遞機制，透過以括號括住引數的程序呼叫可能會產生非預期的結果。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例會說明何時以傳值方式傳遞引數以及何時參考傳遞給它們。 程序`Calculate`同時具有`ByVal`和`ByRef`參數。 指定利率， `rate`，和總金額， `debt`，程序的工作是計算的新值`debt`也就是套用利率的原始值的結果`debt`。 因為`debt`是`ByRef`參數，呼叫對應的程式碼中的引數的值會反映新總計`debt`。 參數`rate`是`ByVal`參數因為`Calculate`不應該變更其值。  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbcnProcedures #&74;](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [如何︰ 將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)   
 [如何︰ 變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md)   
 [如何︰ 防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)   
 [如何︰ 強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)   
 [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)   
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
