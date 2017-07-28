---
title: "早期和晚期繫結 (Visual Basic)"
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
- early binding
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding, Visual Basic compiler
- binding, late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding
- late binding, Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 66a34580417fb8b4a814b237ec36ffe700b1b30a
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="early-and-late-binding-visual-basic"></a>早期和晚期繫結 (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 編譯器會在將物件指派給物件變數時，執行稱為 `binding` 的處理序。 將物件指派給宣告為特定物件型別的變數時，該物件即為「早期繫結」。 早期繫結物件讓編譯器能夠配置記憶體，並在應用程式執行之前執行其他最佳化。 例如，下列程式碼片段會將變數宣告為 <xref:System.IO.FileStream> 類型：  
  
 [!code-vb[VbVbalrOOP#90](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_1.vb)]  
  
 因為 <xref:System.IO.FileStream> 是特定的物件類型，所以指派給 `FS` 的執行個體就是早期繫結。  
  
 反之，將物件指派給宣告為 `Object` 型別的變數時，該物件即為「晚期繫結」。 此型別的物件可以保存對任何物件的參考，但缺少許多早期繫結物件的優點。 例如，下列程式碼片段會宣告一個物件變數來保存 `CreateObject` 函式所傳回的物件：  
  
 [!code-vb[VbVbalrOOP#91](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_2.vb)]  
  
## <a name="advantages-of-early-binding"></a>早期繫結的優點  
 您應該盡可能使用早期繫結物件，因為它們可讓編譯器進行重要的最佳化，以產生更有效率的應用程式。 早期繫結物件的速度很明顯地比晚期繫結物件還快，並藉由確實描述正在使用哪種物件，讓您的程式碼更容易閱讀和維護。 早期繫結的另一個優點是它會啟用像是自動完成程式碼和動態說明等有用功能，因為 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 整合式開發環境 (IDE) 可以完全判斷您在編輯程式碼時所使用的物件型別。 早期繫結可降低發生執行階段錯誤的次數和嚴重性，因為它讓編譯器能夠在編譯程式時報告錯誤。  
  
> [!NOTE]
>  晚期繫結只能用來存取宣告為 `Public` 的型別成員。 存取宣告為 `Friend` 或 `Protected Friend` 的成員會導致執行階段錯誤。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>   
 [物件存留期：物件的建立和終結](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)   
 [Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)

