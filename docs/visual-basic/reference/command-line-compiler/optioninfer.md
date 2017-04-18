---
title: "/optioninfer |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optioninfer
dev_langs:
- VB
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 0c0b6d8361e2bd59837161d1135b100e66d40887
ms.lasthandoff: 03/13/2017

---
# <a name="optioninfer"></a>/optioninfer
可讓您在變數宣告中使用區域類型推斷。  
  
## <a name="syntax"></a>語法  
  
```  
/optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`+` &#124; `-`|選擇項。 指定 `/optioninfer+` 以啟用區域類型推斷，或是指定 `/optioninfer-` 以封鎖它。 未指定值的 `/optioninfer` 選項與 `/optioninfer+` 相同。 不存在 `/optioninfer` 參數時的預設值也是 `/optioninfer+`。 預設值是在 Vbc.rsp 回應檔中設定。|  
  
> [!NOTE]
>  您可以使用 `/noconfig` 選項來保留編譯器的內部預設值而不是 vbc.rsp 中所指定的預設值。 這個選項的編譯器預設值是 `/optioninfer-`。  
  
## <a name="remarks"></a>備註  
 如果原始程式碼檔案包含[Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)，陳述式會覆寫`/optioninfer`命令列編譯器設定。  
  
### <a name="to-set-optioninfer-in-the-visual-studio-ide"></a>在 Visual Studio IDE 中設定 /optioninfer  
  
1.  選取的專案中**方案總管 中**。 在**專案**] 功能表上，按一下 [**屬性**。 如需詳細資訊，請參閱[NIB︰ 使用專案設計工具管理專案屬性](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e)。  
  
2.  在**編譯**索引標籤上，修改中的值**Option infer**方塊。  
  
## <a name="example"></a>範例  
 下列程式碼會在已啟用區域類型推斷下編譯 `test.vb`。  
  
```  
vbc /optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Visual Basic 預設值，專案選項對話方塊](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)   
 [專案設計工具、編譯頁 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)   
 [/ 未設定](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
