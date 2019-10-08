---
title: -out （Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 6b005ac26e3fffad350cb4ce52f7757c9fff2ac1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005340"
---
# <a name="-out-visual-basic"></a>-out （Visual Basic）
指定輸出檔案的名稱。  
  
## <a name="syntax"></a>語法  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`filename`|必要項。 編譯器所建立之輸出檔的名稱。 如果檔案名包含空格，請將名稱括在引號（""）中。|  
  
## <a name="remarks"></a>備註  
 指定要建立之檔案的完整名稱和副檔名。 如果不這麼做，.exe 檔案會從包含 `Sub Main` 程式的原始程式碼檔中取得其名稱，而 .dll 檔案會從第一個原始程式碼檔案取得其名稱。  
  
 如果您指定不含 .exe 或 .dll 副檔名的檔案名，編譯器會自動為您加入延伸模組，視為 `-target` 編譯器選項所指定的值而定。  
  
|在 Visual Studio 的整合式開發環境中設定|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [應用程式] 索引標籤。<br />3.修改 [**元件名稱**] 方塊中的值。|  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `T2.vb`，並建立輸出檔 `T2.exe`。  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target （Visual Basic）](../../../visual-basic/reference/command-line-compiler/target.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
