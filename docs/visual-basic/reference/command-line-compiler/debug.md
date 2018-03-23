---
title: /debug (Visual Basic)
ms.date: 03/10/2018
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7430a3ac85a86ed5528af9ea830da530208749eb
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="-debug-visual-basic"></a>-偵錯 (Visual Basic)
讓編譯器產生偵錯資訊，並將它放入輸出檔案。  
  
## <a name="syntax"></a>語法  
  
```  
-debug[+ | -]  
' -or-  
-debug:[full | pdbonly]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`+` &#124; `-`|選擇性。 指定`+`或`/debug`會導致編譯器產生偵錯資訊，並將它放在.pdb 檔案中。 指定`-`具有相同的效果等同於不指定`/debug`。|  
|`full` &#124; `pdbonly`|選擇性。 指定編譯器所產生的偵錯資訊類型。 如果您未指定`/debug:pdbonly`，預設值是`full`，可讓您將偵錯工具附加至正在執行的程式。 `pdbonly`引數可讓程式啟動偵錯工具，但它只會顯示組件語言程式碼執行的程式已附加偵錯工具時，偵錯原始程式碼。|  
  
## <a name="remarks"></a>備註  
 若要建立偵錯組建，請使用此選項。 如果您未指定`/debug`， `/debug+`，或`/debug:full`，您將無法偵錯程式的輸出檔。  
  
 根據預設，偵錯資訊不會發出 (`/debug-`)。 若要發出偵錯資訊，請指定`/debug`或`/debug+`。  
  
 如需如何設定應用程式效能偵錯的資訊，請參閱[使映像偵錯更容易](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md)。  
  
|若要設定-偵錯 Visual Studio 整合式的開發環境中|  
|---|  
|1.在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。 <br />2.按一下 [編譯] 索引標籤。<br />3.按一下 [進階編譯選項]。<br />4.修改中的值**產生偵錯資訊**方塊。|  
  
## <a name="example"></a>範例  
 下列範例會將偵錯資訊置於輸出檔`App.exe`。  
  
```  
vbc -debug -out:app.exe test.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
