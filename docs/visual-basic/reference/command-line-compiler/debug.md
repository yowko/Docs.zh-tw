---
title: /debug (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
ms.openlocfilehash: 92ff9c5ea7352506c1949a77b4fb6291d63758d7
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50040327"
---
# <a name="-debug-visual-basic"></a>-偵錯 (Visual Basic)
可讓編譯器產生偵錯資訊，並將它放入輸出檔案。  
  
## <a name="syntax"></a>語法  
  
```  
-debug[+ | -]  
' -or-  
-debug:[full | pdbonly]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`+` &#124; `-`|選擇性。 指定`+`或`/debug`可讓編譯器產生偵錯資訊，並將它放在.pdb 檔案。 指定`-`有相同的效果等同於不指定`/debug`。|  
|`full` &#124; `pdbonly`|選擇性。 指定編譯器所產生的偵錯資訊類型。 如果您未指定`/debug:pdbonly`，預設值是`full`，可讓您將偵錯工具附加至執行中的程式。 `pdbonly`引數可讓啟動程式中偵錯工具，但它只會顯示組件語言程式碼執行的程式附加到偵錯工具時，偵錯原始程式碼。|  
  
## <a name="remarks"></a>備註  
 若要建立偵錯組建，請使用此選項。 如果您未指定`/debug`， `/debug+`，或`/debug:full`，您將無法偵錯程式的輸出檔案。  
  
 根據預設，偵錯資訊不會發出 (`/debug-`)。 若要發出偵錯資訊，請指定`/debug`或`/debug+`。  
  
 如需如何設定應用程式效能偵錯的資訊，請參閱[使映像偵錯更容易](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md)。  
  
|若要設定-偵錯 Visual Studio 整合式的開發環境|  
|---|  
|1.在方案總管 中選取專案之後，按一下 [專案]  功能表中 [屬性] 。 <br />2.按一下 [編譯] 索引標籤。<br />3.按一下 [進階編譯選項]。<br />4.修改中的值**產生偵錯資訊** 方塊中。|  
  
## <a name="example"></a>範例  
 下列範例會將偵錯資訊放入輸出檔案`App.exe`。  
  
```  
vbc -debug -out:app.exe test.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
