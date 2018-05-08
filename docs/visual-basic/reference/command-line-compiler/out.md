---
title: -out (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 234071d043b2649e2438ed20fe044fb89cdb9bf8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-out-visual-basic"></a>-out (Visual Basic)
指定輸出檔案的名稱。  
  
## <a name="syntax"></a>語法  
  
```  
-out:filename  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`filename`|必要。 編譯器會建立輸出檔的名稱。 如果檔案名稱包含空格，將名稱括在引號 ("")。|  
  
## <a name="remarks"></a>備註  
 指定的完整名稱和要建立檔案的副檔名。 如果不這麼做，.exe 檔會從原始程式檔包含其名稱`Sub Main`程序和.dll 檔案會從第一個原始程式檔取得其名稱。  
  
 如果您指定檔案名稱沒有.exe 或.dll 副檔名，編譯器會自動延伸模組會為您加入，根據指定的值`-target`編譯器選項。  
  
|若要設定的逾時 Visual Studio 整合式的開發環境中|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [應用程式]  索引標籤。<br />3.修改中的值**組件名稱**方塊。|  
  
## <a name="example"></a>範例  
 下列程式碼編譯`T2.vb`並建立輸出檔`T2.exe`。  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-目標 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
