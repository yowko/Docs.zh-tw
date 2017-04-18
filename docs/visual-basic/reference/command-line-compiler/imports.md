---
title: "/imports (Visual Basic) |Microsoft 文件"
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
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: 15
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
ms.openlocfilehash: 1dcbba442413dba63aef31fd40a511bad5e8217b
ms.lasthandoff: 03/13/2017

---
# <a name="imports-visual-basic"></a>/imports (Visual Basic)
從指定的組件，匯入命名空間。  
  
## <a name="syntax"></a>語法  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`namespaceList`|必要項。 要匯入的命名空間的逗號分隔清單。|  
  
## <a name="remarks"></a>備註  
 `/imports`選項會匯入目前的資料集的原始程式檔或任何參考組件內定義的命名空間。  
  
 使用指定的命名空間中的成員`/imports`編譯過程中所有原始程式檔都都可以使用。 使用[Imports 陳述式 （.NET 命名空間和類型）](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)單一原始程式檔中使用命名空間。  
  
|若要設定 Visual Studio 整合式的開發環境中匯入 /|  
|---|  
|1.在 **方案總管**中選取專案。 在**專案**] 功能表上，按一下 [**屬性**。 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.按一下 [**參考**] 索引標籤。<br />3.在旁邊的方塊中輸入命名空間名稱**加入使用者匯入** 按鈕。<br />4.按一下 [**加入使用者匯入**] 按鈕。|  
  
## <a name="example"></a>範例  
 下列程式碼編譯時`/imports:system`指定。  
  
 [!code-vb[VbVbalrCompiler #&21;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [參考和 Imports 陳述式](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
