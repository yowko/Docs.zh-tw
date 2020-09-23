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
ms.openlocfilehash: ce1f24f25ea58cb6ddc2f5c582b6103d8f18d922
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085161"
---
# <a name="-removeintchecks"></a>-removeintchecks

開啟或關閉整數作業的溢位錯誤檢查。  
  
## <a name="syntax"></a>語法  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`+` &#124; `-`|選擇性。 `-removeintchecks-`選項會讓編譯器檢查所有的整數計算是否有溢位錯誤。 預設值為 `-removeintchecks-`。<br /><br /> 指定 `-removeintchecks` 或 `-removeintchecks+` 防止錯誤檢查，而且可以更快速地進行整數計算。 但是，如果沒有錯誤檢查，而且資料類型的容量溢位，則可能會儲存不正確的結果，而不會引發錯誤。|  
  
|在 Visual Studio 整合式開發環境中設定-removeintchecks|  
|---|  
|1. 在 **方案總管**中選取專案。 按一下 [專案] 功能表上的 [屬性]。 <br />2. 按一下 [ **編譯** ] 索引標籤。<br />3. 按一下 [ **Advanced** ] 按鈕。<br />4. 修改 [ **移除整數溢位檢查** ] 方塊的值。|  
  
## <a name="example"></a>範例  

 下列程式碼會編譯 `Test.vb` 並關閉整數溢位錯誤檢查。  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
