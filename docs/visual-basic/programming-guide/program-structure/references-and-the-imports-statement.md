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
ms.openlocfilehash: 5b810af86f8659ffbe27d23d36aece408516a9bd
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972050"
---
# <a name="references-and-the-imports-statement-visual-basic"></a>參考和 Imports 陳述式 (Visual Basic)
您可以選擇 [**專案**] 功能表上的 [**加入參考**] 命令，讓外部物件可供專案使用。 Visual Basic 中的參考可以指向類似類型程式庫的元件，但會包含詳細資訊。  
  
## <a name="the-imports-statement"></a>Imports 語句  
 元件包含一或多個命名空間。 當您加入元件的參考時，您也可以將`Imports`語句加入模組中，以控制該元件在模組內的可見度。 `Imports`語句提供範圍內容，讓您只使用提供唯一參考所需的命名空間部分。  
  
 `Imports`語句具有下列語法：  
  
 `Imports [Aliasname =] Namespace`  
  
 `Aliasname`是指您可以在程式碼內用來參考已匯入之命名空間的簡短名稱。 `Namespace`是透過專案參考、專案內的定義，或透過上`Imports`一個語句提供的命名空間。  
  
 模組可以包含任意數目的`Imports`語句。 它們必須出現在任何`Option`語句之後（如果有的話），但在任何其他程式碼之前。  
  
> [!NOTE]
> 請勿混淆專案參考與`Imports`語句`Declare`或語句。 專案參考會使外部物件（例如元件中的物件）可用於 Visual Basic 專案。 `Imports`語句可用來簡化對專案參考的存取，但不會提供這些物件的存取權。 `Declare`語句是用來在動態連結程式庫（DLL）中宣告外部程式的參考。  
  
## <a name="using-aliases-with-the-imports-statement"></a>搭配 Imports 語句使用別名  
 `Imports`語句可讓您藉由排除明確輸入參考完整名稱的需求，更輕鬆地存取類別的方法。 別名可讓您將易記名稱指派給命名空間的一個部分。 例如，導致在多行上顯示單一文字片段的線路傳回/換行字元順序，就是<xref:Microsoft.VisualBasic.ControlChars> <xref:Microsoft.VisualBasic?displayProperty=nameWithType>命名空間中模組的一部分。 若要在沒有別名的程式中使用此常數，您必須輸入下列程式碼：  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 `Imports`語句必須一律是緊接在模組中任何`Option`語句之後的第一行。 下列程式碼片段顯示如何匯入並指派別名給<xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType>模組：  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 未來對此命名空間的參考可能會變得很短：  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 `Imports`如果語句不包含別名名稱，在匯入的命名空間內定義的專案就可以在模組中使用，而不需要限定。 如果指定別名名稱，則必須將它當做包含在該命名空間內之名稱的限定詞使用。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [Visual Basic 中的命名空間](namespaces.md)
- [.NET 中的組件](../../../standard/assembly/index.md)
- [Imports 陳述式 (.NET 命名空間和類型)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
