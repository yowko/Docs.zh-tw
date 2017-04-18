---
title: "/main |Microsoft 文件"
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
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
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
ms.openlocfilehash: dded7621845141896f353d69ab757010c825b975
ms.lasthandoff: 03/13/2017

---
# <a name="main"></a>/main
指定類別或模組，其中包含`Sub Main`程序。  
  
## <a name="syntax"></a>語法  
  
```  
/main:location  
```  
  
## <a name="arguments"></a>引數  
 `location`  
 必要項。 類別或模組，其中包含完整限定性條件`Sub Main`在程式啟動時要呼叫的程序。 這可能是在表單中**/main:module**或**/main:namespace.module**。  
  
## <a name="remarks"></a>備註  
 當您建立可執行檔或 Windows 可執行程式時，請使用此選項。 如果**/main**省略選項，編譯器會搜尋有效的共用`Sub Main`所有公用類別和模組中。  
  
 請參閱[Main 程序，在 Visual Basic 中](../../../visual-basic/programming-guide/program-structure/main-procedure.md)的各種形式的討論`Main`程序。  
  
 當`location`是繼承自類別<xref:System.Windows.Forms.Form>，編譯器會提供預設值`Main`如果類別沒有啟動應用程式的程序`Main`程序。</xref:System.Windows.Forms.Form> 這可讓您在命令列在開發環境中所建立的程式碼編譯。  
  
 [!code-vb[VbVbalrCompiler #&16;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### <a name="to-set-main-in-the-visual-studio-integrated-development-environment"></a>在 Visual Studio 中設定 /main 整合式開發環境  
  
1.  在 **方案總管**中選取專案。 在**專案**] 功能表上，按一下 [**屬性**。  
  
     如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  按一下 [應用程式] **** 索引標籤。  
  
3.  請確定**啟用應用程式架構**未核取核取方塊。  
  
4.  修改中的值**啟始物件**方塊。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`T2.vb`和`T3.vb`，並指定，`Sub Main`程序將位於`Test2`類別。  
  
```  
vbc t2.vb t3.vb /main:Test2  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [NIB: Hello，World Visual Basic 版本](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c)   
 [在 Visual Basic 中的 main 程序](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
