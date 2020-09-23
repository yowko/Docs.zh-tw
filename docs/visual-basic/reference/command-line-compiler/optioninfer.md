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
ms.openlocfilehash: 3edb1f74ab63497aeda0d72847bce92ad315a1a5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098913"
---
# <a name="-optioninfer"></a>-optioninfer

可讓您在變數宣告中使用區域類型推斷。  
  
## <a name="syntax"></a>語法  
  
```console  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`+` &#124; `-`|選擇性。 指定 `-optioninfer+` 以啟用區域類型推斷，或是指定 `-optioninfer-` 以封鎖它。 未指定值的 `-optioninfer` 選項與 `-optioninfer+` 相同。 不存在 `-optioninfer` 參數時的預設值也是 `-optioninfer+`。 預設值是在 Vbc.rsp 回應檔中設定。|  
  
> [!NOTE]
> 您可以使用 `-noconfig` 選項來保留編譯器的內部預設值而不是 vbc.rsp 中所指定的預設值。 這個選項的編譯器預設值是 `-optioninfer-`。  
  
## <a name="remarks"></a>備註  

 如果原始程式碼檔包含 [Option 推斷語句](../../language-reference/statements/option-infer-statement.md)，則語句會覆寫 `-optioninfer` 命令列編譯器設定。  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a>若要在 Visual Studio IDE 中設定-optioninfer  
  
1. 在 **方案總管**中選取專案。 按一下 [專案] 功能表上的 [屬性]。  
  
2. 在 [ **編譯** ] 索引標籤上，修改 [ **選項推斷** ] 方塊中的值。  
  
## <a name="example"></a>範例  

 下列程式碼會在已啟用區域類型推斷下編譯 `test.vb`。  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [-optioncompare](optioncompare.md)
- [-optionexplicit](optionexplicit.md)
- [-optionstrict](optionstrict.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
- [Option Infer 陳述式](../../language-reference/statements/option-infer-statement.md)
- [區域型別推斷](../../programming-guide/language-features/variables/local-type-inference.md)
- [選項對話方塊、專案、Visual Basic 預設值](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [專案設計工具、編譯頁 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [-noconfig](noconfig.md)
- [從命令列建置](building-from-the-command-line.md)
