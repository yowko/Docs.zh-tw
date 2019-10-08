---
title: /debug (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
ms.openlocfilehash: c2fbe5aa6f0b9ac8c99c9b9ec5cdf0a7d9764ab8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002401"
---
# <a name="-debug-visual-basic"></a>-debug （Visual Basic）
使編譯器產生調試資訊，並將它放在輸出檔中。  
  
## <a name="syntax"></a>語法  
  
```console 
-debug[+ | -]  
```

或

```console  
-debug:[full | pdbonly]  
```
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`+` &#124; `-`|選擇性。 指定 `+` 或 `/debug` 會導致編譯器產生調試資訊，並將它放在 .pdb 檔案中。 指定 `-` 與未指定 `/debug` 的效果相同。|  
|`full` &#124; `pdbonly`|選擇性。 指定編譯器所產生的偵錯資訊類型。 如果您未指定 `/debug:pdbonly`，則預設值為 `full`，可讓您將偵錯工具附加至執行中的程式。 @No__t-0 引數可在偵錯工具中啟動程式時允許原始程式碼的偵錯工具，但只有在執行中的程式附加至偵錯工具時，才會顯示元件語言代碼。|  
  
## <a name="remarks"></a>備註  
 若要建立偵錯組建，請使用此選項。 如果您未指定 `/debug`、`/debug+` 或 `/debug:full`，您將無法對程式的輸出檔進行 debug。  
  
 根據預設，不會發出偵錯工具資訊（`/debug-`）。 若要發出調試資訊，請指定 `/debug` 或 `/debug+`。  
  
 如需如何設定應用程式效能偵錯的資訊，請參閱[使映像偵錯更容易](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md)。  
  
|在 Visual Studio 的整合式開發環境中設定-debug|  
|---|  
|1.在方案總管中選取專案之後，按一下 [專案] 功能表中 [屬性]。 <br />2.按一下 [編譯] 索引標籤。<br />3.按一下 [進階編譯選項]。<br />4.修改 [**產生調試資訊**] 方塊中的值。|  
  
## <a name="example"></a>範例  
 下列範例會將調試資訊放在輸出檔 `App.exe`。  
  
```console  
vbc -debug -out:app.exe test.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
