---
title: -removeintchecks
ms.date: 03/13/2018
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26485fe2ba3f5647266147744cbe53f978694a9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-removeintchecks"></a>-removeintchecks
開啟溢位錯誤檢查適用於整數作業開啟或關閉。  
  
## <a name="syntax"></a>語法  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`+` &#124; `-`|選擇性。 `-removeintchecks-`選項讓編譯器將檢查所有整數計算的溢位錯誤。 預設值為 `-removeintchecks-`。<br /><br /> 指定`-removeintchecks`或`-removeintchecks+`會阻止錯誤檢查，而且可以進行更快速的整數計算。 不過，如果沒有錯誤檢查，和不正確的結果而不會引發錯誤，如果資料型別容量溢位，可能會儲存。|  
  
|在 Visual Studio 整合式的開發環境中設定-removeintchecks|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [編譯] 索引標籤。<br />3.按一下 [ **進階** ] 按鈕。<br />4.值修改為**移除整數溢位檢查**方塊。|  
  
## <a name="example"></a>範例  
 下列程式碼編譯`Test.vb`並關閉整數溢位錯誤檢查。  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
