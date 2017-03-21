---
title: "如何︰ 呼叫傳回的值 (Visual Basic) 的程序 |Microsoft 文件"
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
- procedure calls, returning values
- Visual Basic code, procedures
- procedures, calling
- procedures, returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: 15
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
ms.openlocfilehash: df6bb1ed8acf5f86a290d67fec9c053cfe5245d2
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>如何：呼叫傳回值的程序 (Visual Basic)
A`Function`值傳回給呼叫程式碼。 它可以呼叫其名稱和引數包括在指派陳述式或運算式的右側。  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>若要呼叫的函式程序，在運算式中  
  
1.  使用`Function`程序的名稱相同的方式，您會使用變數。 您可以使用`Function`程序呼叫，您可以在運算式中使用變數或常數的任何地方。  
  
2.  請依照下列程序名稱以括號括住的引數清單。 如果不有任何引數，您可以省略括號。 不過，使用括號會讓您的程式碼容易閱讀。  
  
3.  將引數放在括號，以逗號分隔的引數清單。 確定您提供的相同順序的引數，`Function`程序定義對應的參數。  
  
     或者，您可以依名稱傳遞一個或多個引數。 如需詳細資訊，請參閱[傳遞引數依位置和名稱](./passing-arguments-by-position-and-by-name.md)。  
  
4.  從程序傳回的值加入運算式中只做為值的變數或常數。  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>在指派陳述式中呼叫函式程序  
  
1.  使用`Function`之後等程序名稱 (`=`) 登入指派陳述式。  
  
2.  請依照下列程序名稱以括號括住的引數清單。 如果不有任何引數，您可以省略括號。 不過，使用括號會讓您的程式碼容易閱讀。  
  
3.  將引數放在括號，以逗號分隔的引數清單。 確定您提供的相同順序的引數，`Function`程序定義對應的參數，除非您依名稱傳遞它們。  
  
4.  從程序傳回的值儲存在變數或屬性指派陳述式的左邊。  
  
## <a name="example"></a>範例  
 下列範例會呼叫[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<xref:Microsoft.VisualBasic.Interaction.Environ%2A>擷取作業系統環境變數的值。</xref:Microsoft.VisualBasic.Interaction.Environ%2A> 第一列呼叫`Environ`內第二個運算式，列在中呼叫它在指派陳述式。 `Environ`使用變數名稱做為其唯一引數。 會傳回呼叫程式碼變數的值。  
  
 [!code-vb[VbVbcnProcedures #&7;](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Function 程序](./function-procedures.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [如何︰ 建立程序傳回值](./how-to-create-a-procedure-that-returns-a-value.md)   
 [如何︰ 從程序傳回值](./how-to-return-a-value-from-a-procedure.md)   
 [如何：呼叫不傳回值的程序](./how-to-call-a-procedure-that-does-not-return-a-value.md)
