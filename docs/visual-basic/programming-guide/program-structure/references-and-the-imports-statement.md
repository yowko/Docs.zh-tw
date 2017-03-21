---
title: "參考和 Imports 陳述式 (Visual Basic) |Microsoft 文件"
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
- assemblies [Visual Basic], namespaces
- references, assembly
- namespaces, assemblies
- referencing assemblies
- Imports statement, referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: 12
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
ms.openlocfilehash: 283a27e7703b31a9aeed8f7e4104e89b7ff78525
ms.lasthandoff: 03/13/2017

---
# <a name="references-and-the-imports-statement-visual-basic"></a>參考和 Imports 陳述式 (Visual Basic)
您可以使用外部物件至您的專案選擇**加入參考**命令**專案**功能表。 在參考[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]可以指向組件，就像但包含型別程式庫的詳細資訊。  
  
## <a name="the-imports-statement"></a>Imports 陳述式  
 組件包含一或多個命名空間。 當您將加入組件的參考時，您也可以加入`Imports`陳述式，以控制可見性的模組內的組件的命名空間的模組。 `Imports`陳述式提供的內容範圍設定，可讓您使用只需要提供唯一的參考命名空間的一部分。  
  
 `Imports`陳述式的語法如下︰  
  
 `Imports` [`|``Aliasname` =] `Namespace`  
  
 `Aliasname`指的是簡短名稱，您可以使用程式碼中參考匯入的命名空間。 `Namespace`透過在專案中，定義或先前的專案參考是命名空間，可透過`Imports`陳述式。  
  
 模組可能包含任意數目的`Imports`陳述式。 它們必須出現在任何之後`Option`陳述式，如果存在，但在任何其他程式碼之前。  
  
> [!NOTE]
>  請勿混淆的專案參考`Imports`陳述式或`Declare`陳述式。 專案參考的組件中的物件等外部物件可讓以[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]專案。 `Imports`陳述式用來簡化專案參考的存取，但並不提供這些物件的存取權。 `Declare`陳述式用來宣告外部程序中的動態連結程式庫 (DLL) 的參考。  
  
## <a name="using-aliases-with-the-imports-statement"></a>使用 Imports 陳述式的別名  
 `Imports`陳述式就可以更輕鬆地存取方法的類別而不必明確地輸入完整的參考名稱。 別名可讓您更易記的名稱為命名空間的一部分。 比方說，歸位/換會導致一段文字，以顯示多行的順序是一部分<xref:Microsoft.VisualBasic.ControlChars>中的模組<xref:Microsoft.VisualBasic?displayProperty=fullName>命名空間。</xref:Microsoft.VisualBasic?displayProperty=fullName> </xref:Microsoft.VisualBasic.ControlChars> 若要在程式中不含別名中使用這個常數，您必須輸入下列程式碼︰  
  
 [!code-vb[VbVbalrApplication #&3;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 `Imports`陳述式必須是第一個程式碼行，並緊接著任何`Option`模組中的陳述式。 下列程式碼片段示範如何匯入並指派別名<xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName>模組︰</xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName>  
  
 [!code-vb[VbVbalrApplication #&4;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 未來參考此命名空間可以是非常簡短︰  
  
 [!code-vb[VbVbalrApplication #&5;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 如果`Imports`陳述式不包含別名名稱，匯入的命名空間內定義的項目可以用於無限制的模組。 如果指定的別名名稱，則它必須當做限定詞，包含該命名空間內的名稱。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.ControlChars></xref:Microsoft.VisualBasic.ControlChars>   
 <xref:Microsoft.VisualBasic></xref:Microsoft.VisualBasic>   
 [NIB 如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [如何︰ 建立和使用組件︰ 使用命令列](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)   
 [Imports 陳述式 (.NET 命名空間和類型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
