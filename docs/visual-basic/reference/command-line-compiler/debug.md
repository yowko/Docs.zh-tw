---
title: "/debug (Visual Basic) |Microsoft 文件"
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
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
caps.latest.revision: 18
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
ms.openlocfilehash: 7384e69f066022e861a4277f418df3f4d094c3be
ms.lasthandoff: 03/13/2017

---
# <a name="debug-visual-basic"></a>/debug (Visual Basic)
讓編譯器產生偵錯資訊，並將它放入輸出檔案。  
  
## <a name="syntax"></a>語法  
  
```  
/debug[+ | -]  
' -or-  
/debug:[full | pdbonly]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`+` &#124; `-`|選擇項。 指定`+`或`/debug`會使編譯器產生偵錯資訊，並將它放置於.pdb 檔。 指定`-`具有相同的效果不指定`/debug`。|  
|`full` &#124; `pdbonly`|選擇項。 指定編譯器所產生的偵錯資訊類型。 如果您未指定`/debug:pdbonly`，預設值是`full`，可讓您將偵錯工具附加至正在執行的程式。 `pdbonly`引數可讓程式啟動偵錯工具，但執行的程式附加到偵錯工具時，才會顯示組件語言的程式碼時，偵錯原始程式碼。|  
  
## <a name="remarks"></a>備註  
 若要建立偵錯組建中使用此選項。 如果您未指定`/debug`， `/debug+`，或`/debug:full`，您將無法偵錯程式的輸出檔。  
  
 根據預設，偵錯資訊不會發出 (`/debug-`)。 若要發出偵錯資訊，請指定`/debug`或`/debug+`。  
  
 如需如何設定應用程式效能偵錯的資訊，請參閱[使映像偵錯更容易](http://msdn.microsoft.com/library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3)。  
  
|在 Visual Studio 中設定 /debug 整合式開發環境|  
|---|  
|1.在方案總管 ****中選取專案之後，按一下 [專案] **** 功能表中 [屬性] ****。 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.按一下 [編譯]**** 索引標籤。<br />3.按一下 **進階編譯選項**。<br />4.修改中的值**產生偵錯資訊**方塊。|  
  
## <a name="example"></a>範例  
 下列範例會將偵錯資訊放入輸出檔`App.exe`。  
  
```  
vbc /debug /out:app.exe test.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
