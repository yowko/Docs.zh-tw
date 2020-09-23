---
title: References 與 Imports 陳述式
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 13f250e1b015e5a821da83e557033bc878a8a3b8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097900"
---
# <a name="references-and-the-imports-statement-visual-basic"></a>參考和 Imports 陳述式 (Visual Basic)

您可以選擇 [**專案**] 功能表上的 [**加入參考**] 命令，讓您的專案使用外部物件。 Visual Basic 中的參考可指向元件，這類元件類似于類型程式庫，但會包含詳細資訊。  
  
## <a name="the-imports-statement"></a>Imports 語句  

 元件包括一或多個命名空間。 當您加入元件的參考時，您也可以將語句加入 `Imports` 至模組，以控制該元件之命名空間在模組內的可見度。 `Imports`語句提供範圍內容，可讓您只使用提供唯一參考所需的命名空間部分。  
  
 `Imports`語句具有下列語法：  
  
 `Imports [Aliasname =] Namespace`  
  
 `Aliasname` 參考簡短名稱，您可以在程式碼中用來參考匯入的命名空間。 `Namespace` 是可透過專案參考、專案中的定義，或透過上一個語句來取得的命名空間 `Imports` 。  
  
 模組可包含任意數目的 `Imports` 語句。 它們必須出現在任何 `Option` 語句（如果有的話）之後，但在其他任何程式碼之前。  
  
> [!NOTE]
> 請勿將專案參考與 `Imports` 語句或 `Declare` 語句混淆。 專案參考會將外部物件（例如元件中的物件）提供給 Visual Basic 專案。 `Imports`語句是用來簡化對專案參考的存取，但不提供這些物件的存取權。 `Declare`語句是用來在動態連結程式庫 (DLL) 中宣告外部程式的參考。  
  
## <a name="using-aliases-with-the-imports-statement"></a>使用別名搭配 Imports 語句  

 `Imports`語句可讓您輕鬆地存取類別的方法，而不需要明確地輸入參考的完整名稱。 別名可讓您將易記名稱指派給命名空間的其中一個部分。 例如，在多行上顯示單一文字片段的回車/換行字元，是 <xref:Microsoft.VisualBasic.ControlChars> 命名空間中模組的一部分 <xref:Microsoft.VisualBasic?displayProperty=nameWithType> 。 若要在沒有別名的程式中使用這個常數，您必須輸入下列程式碼：  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 `Imports` 語句一律必須是緊接在模組中任何語句之後的第一行 `Option` 。 下列程式碼片段顯示如何匯入並指派別名給 <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> 模組：  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 未來此命名空間的參考可能會變得很短：  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 如果 `Imports` 語句不包含別名名稱，則在匯入的命名空間內定義的元素可在模組中使用，而不需限定。 如果指定了別名名稱，則必須將其當做該命名空間內所含名稱的辨識符號使用。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [Visual Basic 中的命名空間](namespaces.md)
- [.NET 中的組件](../../../standard/assembly/index.md)
- [Imports 陳述式 (.NET 命名空間和類型)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
