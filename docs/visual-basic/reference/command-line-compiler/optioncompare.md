---
title: "/optioncompare |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optioncompare
dev_langs:
- VB
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: 17
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
ms.openlocfilehash: 53dee5bb50e20204725f031e3e04f5c37c5b3f96
ms.lasthandoff: 03/13/2017

---
# <a name="optioncompare"></a>/optioncompare
指定如何進行字串比較。  
  
## <a name="syntax"></a>語法  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a>備註  
 您可以指定`/optioncompare`中有兩種形式︰`/optioncompare:binary`使用二進位字串比較和`/optioncompare:text`使用文字字串比較。 根據預設，編譯器會使用`/optioncompare:binary`。  
  
 Microsoft Windows 中所使用的字碼頁會決定二進位排序次序。 一般的二進位排序順序如下所示︰  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 文字為基礎的字串比較是以不區分大小寫文字排序順序取決於您的系統地區設定為依據。 一般文字排序順序如下所示︰  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a>在 Visual Studio IDE 中設定 /optioncompare  
  
1.  在 **方案總管**中選取專案。 在**專案**] 功能表上，按一下 [**屬性**。 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  按一下 [編譯]**** 索引標籤。  
  
3.  修改中的值**選項比較**方塊。  
  
### <a name="to-set-optioncompare-programmatically"></a>以程式設計方式設定 /optioncompare  
  
-   請參閱[Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 P`rojFile.vb` ，並使用二進位字串比較。  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [選項對話方塊、專案、Visual Basic 預設值](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
