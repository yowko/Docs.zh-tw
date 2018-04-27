---
title: Visual Basic 中的程序
ms.custom: ''
ms.date: 04/28/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], structured code
- Visual Basic code, procedures
- procedures [Visual Basic], types of
- structured code [Visual Basic], procedures
- procedures
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 92cb2dd3f356acf89cbe62b5f3f5dc81fce271fc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="procedures-in-visual-basic"></a>Visual Basic 中的程序
A*程序*是 Visual Basic 陳述式的宣告陳述式括住的區塊 (`Function`， `Sub`， `Operator`， `Get`， `Set`) 和符合`End`宣告。 在 Visual Basic 中的所有可執行陳述式必須是某些程序內。  
  
## <a name="calling-a-procedure"></a>呼叫程序  
 您可以從程式碼中的其他位置叫用程序。 這稱為「程序呼叫」。 當程序完成執行時，會將控制權交還給叫用程序的程式碼，稱為「呼叫程式碼」。 呼叫程式碼是陳述式或陳述式內的運算式，可依名稱指定程序，並將控制權轉移給它。  
  
## <a name="returning-from-a-procedure"></a>從程序交還  
 程序會在完成執行時將控制權交還給呼叫程式碼。 它可以使用 [Return 陳述式](../../../../visual-basic/language-reference/statements/return-statement.md)、程序的適當 [Exit 陳述式](../../../../visual-basic/language-reference/statements/exit-statement.md)或程序的 [End \<關鍵字> 陳述式](../../../../visual-basic/language-reference/statements/end-keyword-statement.md)來進行這項操作。 控制權會在下列程序呼叫時間點之後接著傳遞給呼叫程式碼。  
  
-   若使用 `Return` 陳述式，控制權會立即交還給呼叫程式碼。 `Return` 陳述式後面的陳述式不會執行。 同一個程序中可以有多個 `Return` 陳述式。  
  
-   若使用 `Exit Sub` 或 `Exit Function` 陳述式，控制權會立即交還給呼叫程式碼。 `Exit` 陳述式後面的陳述式不會執行。 同一個程序中可以有多個 `Exit` 陳述式，也可以混合 `Return` 和 `Exit` 陳述式。  
  
-   如果程序沒有 `Return` 或 `Exit` 陳述式，則會以程序主體最後一個陳述式後面的 `End Sub`、`End Function`、`End Get` 或 `End Set` 陳述式結束。 `End` 陳述式會將控制權立即交還給呼叫程式碼。 一個程序中只能有一個 `End` 陳述式。  
  
## <a name="parameters-and-arguments"></a>參數和引數  
 在大部分情況下，程序會在每次呼叫時針對不同的資料執行。 您可以將這項資訊當作程序呼叫的一部分傳遞給程序。 程序會定義零或多個「參數」，每個參數代表預期會收到的值。 程序定義中的每個參數會對應至程序呼叫中的「引數」。 引數代表您傳遞給指定程序呼叫中對應參數的值。  
  
## <a name="types-of-procedures"></a>程序類型  
 Visual Basic 會使用幾種類型的程序：  
  
-   [Sub 程序](./sub-procedures.md)會執行動作，但不會傳回值給呼叫程式碼。  
  
-   事件處理程序是為了回應使用者動作或程式中某個項目所引發之事件所執行的 `Sub` 程序。  
  
-   [Function 程序](./function-procedures.md)會傳回值給呼叫程式碼。 該程序可在傳回前執行其他動作。

    某些以 C# 撰寫的函式會傳回「參考傳回值」。 函式呼叫者可以修改傳回值，而且這項修改會反映在所呼叫物件的狀態中。 從 Visual Basic 2017 開始，Visual Basic 程式碼可以使用參考傳回值，但無法以傳址方式傳回值。 如需詳細資訊，請參閱[參考傳回值](ref-return-values.md)。
  
-   [屬性程序](./property-procedures.md)會傳回並指派物件或模組上的屬性值。  
  
-   當一或多個運算元是新定義的類別或結構時，[運算子程序](./operator-procedures.md)會定義標準運算式的行為。  
  
-   [Visual Basic 中的泛型程序](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)除了其一般參數之外，還會定義一或多個「型別參數」，讓呼叫程式碼可在每次呼叫時傳遞特定資料類型。  
  
## <a name="procedures-and-structured-code"></a>程序和結構化程式碼  
 應用程式中所有的可執行程式碼行都必須在某個程序內，例如 `Main`、`calculate` 或 `Button1_Click`。 如果您將大型程序細分成較小的程序，您的應用程式會更容易閱讀。  
  
 程序很適合用來執行重複或共用的工作，例如常用的計算、文字和控制項操作，以及資料庫作業。 您可以從程式碼的許多不同位置呼叫程序，因此您可以將程序作為應用程式的建置組塊使用。  
  
 使用程序建構您的程式碼提供下列優點：  
  
-   程序可讓您將程式分成不連續的邏輯單元。 比起不使用程序對整個程式進行偵錯，偵錯個別單元會更輕鬆。  
  
-   開發用於一個平台的程序之後，您可以在其他程式中使用這些程序，通常只需要微幅修改或完全不需要修改。 這可協助您避免程式碼重複。  
  
## <a name="see-also"></a>另請參閱  
 [如何：建立程序](./how-to-create-a-procedure.md)  
 [Sub 程序](./sub-procedures.md)  
 [函式程序](./function-procedures.md)  
 [屬性程序](./property-procedures.md)  
 [運算子程序](./operator-procedures.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [遞迴程序](./recursive-procedures.md)  
 [程序多載化](./procedure-overloading.md)  
 [在 Visual Basic 中的泛型程序](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
