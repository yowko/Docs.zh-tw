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
ms.openlocfilehash: bea6ca24ea6da9000267e754d52fe0ca152f7d7f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005236"
---
# <a name="-removeintchecks"></a>-removeintchecks
開啟或關閉整數作業的錯誤檢查。  
  
## <a name="syntax"></a>語法  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`+` &#124; `-`|選擇性。 @No__t-0 選項會使編譯器檢查溢位錯誤的所有整數計算。 預設為 `-removeintchecks-`。<br /><br /> 指定 `-removeintchecks` 或 `-removeintchecks+` 可避免錯誤檢查，並可讓整數計算更快。 不過，如果沒有錯誤檢查，而且資料類型容量溢位，則可能會儲存不正確的結果，而不會引發錯誤。|  
  
|在 Visual Studio 的整合式開發環境中設定-removeintchecks|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [編譯] 索引標籤。<br />3.按一下 [ **進階** ] 按鈕。<br />4.修改 [**移除整數溢位檢查**] 核取方塊的值。|  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `Test.vb`，並關閉整數溢位-錯誤檢查。  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
