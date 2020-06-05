---
title: Option Explicit 陳述式
ms.date: 07/20/2015
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
ms.openlocfilehash: a352df0323cfeca1ea0e206ae45c3f85a2cd7da3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404365"
---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit 陳述式 (Visual Basic)
強制明確宣告檔案中的所有變數，或允許變數的隱含宣告。  
  
## <a name="syntax"></a>語法  
  
```vb  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>組件  
 `On`  
 選擇性。 啟用 `Option Explicit` 檢查。 如果 `On` `Off` 未指定或，則預設值為 `On` 。  
  
 `Off`  
 選擇性。 停用 `Option Explicit` 檢查。  
  
## <a name="remarks"></a>備註  
 當 `Option Explicit On` 或 `Option Explicit` 出現在檔案中時，您必須使用或語句來明確宣告所有變數 `Dim` `ReDim` 。 如果您嘗試使用未宣告的變數名稱，則會在編譯時期發生錯誤。 `Option Explicit Off`語句允許隱含宣告變數。  
  
 如果使用的話， `Option Explicit` 語句必須出現在檔案中的任何其他原始程式碼語句之前。  
  
> [!NOTE]
> 將設定 `Option Explicit` 為 `Off` 通常不是很好的作法。 一或多個位置中的變數名稱可能有拼字錯誤，這會在程式執行時造成非預期的結果。  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>當 Option Explicit 語句不存在時  
 如果原始程式碼不包含 `Option Explicit` 語句，則會使用 [編譯] 頁面上的 [ **Option Explicit** ] 設定[（[專案設計工具] （Visual Basic）](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) 。 如果使用命令列編譯器，則會使用[-optionexplicit](../../reference/command-line-compiler/optionexplicit.md)編譯器選項。  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>若要在 IDE 中設定 Option Explicit  
  
1. 在 [**方案總管**中，選取專案。 按一下 [專案]**** 功能表上的 [屬性]****。  
  
2. 按一下 [編譯]**** 索引標籤。  
  
3. 在 [**選項明確**] 方塊中設定值。  
  
 當您建立新的專案時，[**編譯**] 索引標籤上的 [ **option explicit** ] 設定會設定為 [ **VB 預設值**] 對話方塊中的 [ **option explicit** ] 設定。 若要存取 [ **VB 預設值**] 對話方塊，請在 [**工具**] 功能表上按一下 [**選項**]。 在 [選項]**** 對話方塊中，展開 [專案和方案]****，然後按一下 [VB 預設值]****。 **VB 預設值**中的初始預設設定為 `On` 。  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>若要在命令列上設定 Option Explicit  
  
- 在**vbc**命令中包含[-optionexplicit](../../reference/command-line-compiler/optionexplicit.md)編譯器選項。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Option Explicit` 語句來強制執行所有變數的明確宣告。 嘗試使用未宣告的變數會在編譯時期導致錯誤。  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a>另請參閱

- [Dim 陳述式](dim-statement.md)
- [ReDim 陳述式](redim-statement.md)
- [Option Compare 陳述式](option-compare-statement.md)
- [Long](option-strict-statement.md)
- [-optioncompare](../../reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../reference/command-line-compiler/optionexplicit.md)
- [-optionstrict](../../reference/command-line-compiler/optionstrict.md)
- [選項對話方塊、專案、Visual Basic 預設值](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
