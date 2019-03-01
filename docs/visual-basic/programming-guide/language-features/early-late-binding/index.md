---
title: 早期和晚期繫結 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
  - 'early binding [Visual Basic]'
  - 'objects [Visual Basic], late-bound'
  - 'objects [Visual Basic], early-bound'
  - 'objects [Visual Basic], late bound'
  - 'early binding [Visual Basic], Visual Basic compiler'
  - 'binding [Visual Basic], late and early'
  - 'objects [Visual Basic], early bound'
  - 'Visual Basic compiler, early and late binding'
  - 'late binding [Visual Basic]'
  - 'late binding [Visual Basic], Visual Basic compiler'
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
---
# <a name="early-and-late-binding-visual-basic"></a>早期和晚期繫結 (Visual Basic)
Visual Basic 編譯器會執行這個程序稱為`binding`當物件指派給物件變數。 將物件指派給宣告為特定物件型別的變數時，該物件即為「早期繫結」。 早期繫結物件讓編譯器能夠配置記憶體，並在應用程式執行之前執行其他最佳化。 例如，下列程式碼片段會將變數宣告為 <xref:System.IO.FileStream> 類型：  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 因為 <xref:System.IO.FileStream> 是特定的物件類型，所以指派給 `FS` 的執行個體就是早期繫結。  
  
 反之，將物件指派給宣告為 `Object` 型別的變數時，該物件即為「晚期繫結」。 此型別的物件可以保存對任何物件的參考，但缺少許多早期繫結物件的優點。 例如，下列程式碼片段會宣告一個物件變數來保存 `CreateObject` 函式所傳回的物件：  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a>早期繫結的優點  
 您應該盡可能使用早期繫結物件，因為它們可讓編譯器進行重要的最佳化，以產生更有效率的應用程式。 早期繫結物件的速度很明顯地比晚期繫結物件還快，並藉由確實描述正在使用哪種物件，讓您的程式碼更容易閱讀和維護。 早期繫結的另一個優點是它因為 Visual Studio 整合式的開發環境 (IDE) 可判斷完全哪些物件型別您正在使用您在編輯時，才讓實用功能，例如自動程式碼完成和動態說明程式碼。 早期繫結可降低發生執行階段錯誤的次數和嚴重性，因為它讓編譯器能夠在編譯程式時報告錯誤。  
  
> [!NOTE]
>  晚期繫結只能用來存取宣告為 `Public` 的型別成員。 存取宣告為 `Friend` 或 `Protected Friend` 的成員會導致執行階段錯誤。  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [物件存留期：如何建立和終結物件](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
