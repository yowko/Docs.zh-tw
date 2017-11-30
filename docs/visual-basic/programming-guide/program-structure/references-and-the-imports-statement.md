---
title: "參考和 Imports 陳述式 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 739934b65241a7846b5323d5e75446832d83e5d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="references-and-the-imports-statement-visual-basic"></a>參考和 Imports 陳述式 (Visual Basic)
您可以使用外部物件至您的專案選擇**加入參考**命令**專案**功能表。 在參考[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]可以指向組件，就像型別程式庫，但包含更多資訊。  
  
## <a name="the-imports-statement"></a>Imports 陳述式  
 組件包含一或多個命名空間。 當您將組件的參考時，您也可以加入`Imports`陳述式來控制在模組中的組件的命名空間的可見性的模組。 `Imports`陳述式提供的範圍的內容，可讓您使用只需要提供唯一的參考命名空間的一部分。  
  
 `Imports`陳述式具有下列語法：  
  
 `Imports` [`|``Aliasname` =] `Namespace`  
  
 `Aliasname`是指您可以使用程式碼中參考匯入的命名空間的簡短名稱。 `Namespace`透過定義在專案中，或透過先前的專案參考是透過使用命名空間`Imports`陳述式。  
  
 模組可能包含任意數目的`Imports`陳述式。 它們必須出現在任何之後`Option`陳述式，如果有的話，但任何其他程式碼之前。  
  
> [!NOTE]
>  請勿混淆的專案參考`Imports`陳述式或`Declare`陳述式。 專案參考的組件中的物件等外部物件可讓以[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]專案。 `Imports`陳述式用來簡化存取專案的參考，但不提供這些物件的存取權。 `Declare`陳述式用來宣告外部程序動態連結程式庫 (DLL) 中的參考。  
  
## <a name="using-aliases-with-the-imports-statement"></a>Imports 陳述式搭配使用別名  
 `Imports`陳述式可以讓您更輕鬆地存取方法的類別不必明確地輸入參照的完整的名稱。 別名可讓您指派比較易記的名稱命名空間的一部分。 比方說，歸位/換會導致一段文字，以在多行上顯示的順序是一部分<xref:Microsoft.VisualBasic.ControlChars>中的模組<xref:Microsoft.VisualBasic?displayProperty=nameWithType>命名空間。 若要在程式中不含別名中使用這個常數，您必須輸入下列程式碼：  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 `Imports`陳述式都必須緊接著任何前行`Option`模組中的陳述式。 下列程式碼片段示範如何匯入並指派別名<xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType>模組：  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 未來參考此命名空間可以是非常簡短的：  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 如果`Imports`陳述式不包含的別名名稱，在匯入的命名空間中定義的項目可以用於無限制的模組。 如果指定的別名名稱，就必須採用與限定詞的名稱包含在該命名空間內。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.ControlChars>  
 <xref:Microsoft.VisualBasic>  
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [如何：使用命令列建立和使用組件](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [Imports 陳述式 (.NET 命名空間和類型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
