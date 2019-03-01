---
title: 參考和 Imports 陳述式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: f3396eb3e758dc456d86de80246de24349680f2e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973037"
---
# <a name="references-and-the-imports-statement-visual-basic"></a>參考和 Imports 陳述式 (Visual Basic)
您可以對外部物件可以使用您的專案選擇**加入參考**命令**專案**功能表。 在 Visual Basic 中的參考可以指向組件，就像型別程式庫，但包含更多資訊。  
  
## <a name="the-imports-statement"></a>Imports 陳述式  
 組件包含一或多個命名空間。 當您新增組件的參考時，您也可以新增`Imports`陳述式來控制模組內的組件的命名空間的可見性的模組。 `Imports`陳述式提供的範圍的內容，可讓您使用只需要提供唯一的參考命名空間的一部分。  
  
 `Imports`陳述式的語法如下：  
  
 `Imports [Aliasname =] Namespace`  
  
 `Aliasname` 是指您可以使用程式碼中參考匯入的命名空間的簡短名稱。 `Namespace` 透過定義在專案中，或透過先前的專案參考是可透過其中一個命名空間`Imports`陳述式。  
  
 模組可能包含任意數目的`Imports`陳述式。 它們必須出現在任何之後`Option`陳述式，如果有的話，但任何其他程式碼之前。  
  
> [!NOTE]
>  請勿混淆的專案參考`Imports`陳述式或`Declare`陳述式。 專案參考的組件中的物件等外部物件可讓 Visual Basic 專案。 `Imports`陳述式可用來簡化存取專案的參考，但並不會提供這些物件的存取權。 `Declare`陳述式用來宣告外部程序動態連結程式庫 (DLL) 中的參考。  
  
## <a name="using-aliases-with-the-imports-statement"></a>使用 Imports 陳述式的別名  
 `Imports`陳述式就可以更輕鬆地存取方法的類別不需要明確地輸入完整的名稱的參考。 別名可讓您將容易使用的名稱指派給命名空間的一個部分而已。 比方說，歸位/換行會導致一段文字，以在多行上顯示的順序會是一部分<xref:Microsoft.VisualBasic.ControlChars>中的模組<xref:Microsoft.VisualBasic?displayProperty=nameWithType>命名空間。 若要在程式中不含別名中使用這個常數，您需要輸入下列程式碼：  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 `Imports` 陳述式都必須緊接著任何的前幾行`Option`模組中的陳述式。 下列程式碼片段示範如何匯入並指派至別名<xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType>模組：  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 未來參考此命名空間可以是非常簡短的：  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 如果`Imports`陳述式不包含別名名稱，匯入的命名空間內定義的項目可用在不需完整的模組。 如果指定的別名名稱，則它必須用作辨識符號包含在該命名空間的名稱。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [.NET 中的組件](../../../standard/assembly/index.md)
- [如何：使用命令列建立和使用組件](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
- [Imports 陳述式 (.NET 命名空間和類型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
