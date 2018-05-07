---
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: e7dbc4d5f06096978c4d93ea20677dcb60bc3fcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-optioninfer"></a>-optioninfer
可讓您在變數宣告中使用區域類型推斷。  
  
## <a name="syntax"></a>語法  
  
```  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`+` &#124; `-`|選擇性。 指定 `-optioninfer+` 以啟用區域類型推斷，或是指定 `-optioninfer-` 以封鎖它。 未指定值的 `-optioninfer` 選項與 `-optioninfer+` 相同。 不存在 `-optioninfer` 參數時的預設值也是 `-optioninfer+`。 預設值是在 Vbc.rsp 回應檔中設定。|  
  
> [!NOTE]
>  您可以使用 `-noconfig` 選項來保留編譯器的內部預設值而不是 vbc.rsp 中所指定的預設值。 這個選項的編譯器預設值是 `-optioninfer-`。  
  
## <a name="remarks"></a>備註  
 如果原始程式碼檔內含[Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)，陳述式會覆寫`-optioninfer`命令列編譯器設定。  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a>在 Visual Studio IDE 中設定-optioninfer  
  
1.  選取的專案中**方案總管 中**。 在 [專案] 功能表上，按一下 [屬性]。  
  
2.  在**編譯**索引標籤上，修改中的值**Option infer**方塊。  
  
## <a name="example"></a>範例  
 下列程式碼會在已啟用區域類型推斷下編譯 `test.vb`。  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [選項對話方塊、專案、Visual Basic 預設值](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [專案設計工具、編譯頁面 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
