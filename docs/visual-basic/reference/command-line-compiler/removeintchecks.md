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
ms.openlocfilehash: c086a031d5cef4563a6769e7683dcb1110b8fe49
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822722"
---
# <a name="-removeintchecks"></a>-removeintchecks
會檢查開啟或關閉的整數運算溢位錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`+` &#124; `-`|選擇性。 `-removeintchecks-`選項可讓編譯器檢查溢位錯誤的所有整數計算。 預設為 `-removeintchecks-`。<br /><br /> 指定`-removeintchecks`或`-removeintchecks+`可防止錯誤檢查，並能更快速的整數計算。 不過，如果沒有錯誤檢查，以及如果資料型別容量溢位，可能會不正確的結果儲存而不會引發錯誤。|  
  
|若要在 Visual Studio 整合式的開發環境中設定-removeintchecks|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [編譯] 索引標籤。<br />3.按一下 [ **進階** ] 按鈕。<br />4.修改的值**移除整數溢位檢查** 方塊中。|  
  
## <a name="example"></a>範例  
 下列程式碼編譯`Test.vb`並關閉整數溢位錯誤檢查。  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
