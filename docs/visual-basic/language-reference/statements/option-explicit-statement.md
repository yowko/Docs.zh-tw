---
title: "Option Explicit 陳述式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d39b3d7cf5096e3b263938d32e017eae5708e042
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit 陳述式 (Visual Basic)
會強制明確宣告在檔案中，所有變數，或允許隱含宣告的變數。  
  
## <a name="syntax"></a>語法  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>組件  
 `On`  
 選擇項。 可讓`Option Explicit`檢查。 如果`On`或`Off`未指定，預設值是`On`。  
  
 `Off`  
 選擇項。 停用`Option Explicit`檢查。  
  
## <a name="remarks"></a>備註  
 當`Option Explicit On`或`Option Explicit`會出現在檔案中，您必須使用明確宣告所有變數`Dim`或`ReDim`陳述式。 如果您嘗試使用未宣告的變數名稱，則會在編譯時期發生錯誤。 `Option Explicit Off`陳述式可讓隱含宣告的變數。  
  
 如果單獨使用，`Option Explicit`陳述式必須出現在任何其他來源的程式碼陳述式之前的檔案。  
  
> [!NOTE]
>  設定`Option Explicit`至`Off`通常不是個不錯的做法。 您無法拼錯的變數名稱在一個或多個位置，程式執行時，會導致非預期的結果。  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Option Explicit 陳述式時不存在  
 如果不包含原始碼`Option Explicit`陳述式， **Option Explicit**上設定[編譯的頁面上，專案設計工具 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)用。 使用命令列編譯器時，如果[/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)編譯器選項使用。  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>若要在 IDE 中設定 Option Explicit  
  
1.  在方案總管中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  按一下 [編譯] 索引標籤。  
  
3.  設定中的值**Option Explicit**方塊。  
  
 當您建立新的專案， **Option Explicit**上設定**編譯** 索引標籤設為**Option Explicit**中設定**VB 預設值** 對話方塊。 若要存取**VB 預設值**對話方塊**工具**功能表上，按一下 **選項**。 在**選項**對話方塊方塊中，展開 **專案和方案**，然後按一下  **VB 預設值**。 中的初始預設設定**VB 預設值**是`On`。  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>若要在命令列上設定 Option Explicit  
  
-   包含[/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)編譯器選項在**vbc**命令。  
  
## <a name="example"></a>範例  
 下列範例會使用`Option Explicit`強制明確宣告所有變數的陳述式。 嘗試使用未宣告的變數在編譯時期產生錯誤。  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [ReDim 陳述式](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [選項對話方塊、專案、Visual Basic 預設值](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
