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
ms.openlocfilehash: ec4722cb7088819dae95ca1b7cbc1469d957a7aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400470"
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
|`+` &#124; `-`|選擇性。 `-removeintchecks-`選項會使編譯器檢查溢位錯誤的所有整數計算。 預設值為 `-removeintchecks-`。<br /><br /> 指定 `-removeintchecks` 或 `-removeintchecks+` 可防止錯誤檢查，並可讓整數計算更快。 不過，如果沒有錯誤檢查，而且資料類型容量溢位，則可能會儲存不正確的結果，而不會引發錯誤。|  
  
|在 Visual Studio 的整合式開發環境中設定-removeintchecks|  
|---|  
|1. 在**方案總管**中選取專案。 按一下 [專案]**** 功能表上的 [屬性]****。 <br />2. 按一下 [**編譯**] 索引標籤。<br />3. 按一下 [ **Advanced** ] 按鈕。<br />4. 修改 [**移除整數溢位檢查**] 核取方塊的值。|  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `Test.vb` 並關閉整數溢位-錯誤檢查。  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
