---
title: /removeintchecks
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e765f0007eea8e196b1a1b3b55b969c5b074b52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="removeintchecks"></a>/removeintchecks
開啟溢位錯誤檢查適用於整數作業開啟或關閉。  
  
## <a name="syntax"></a>語法  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`+` &#124; `-`|選擇項。 `/removeintchecks-`選項讓編譯器將檢查所有整數計算的溢位錯誤。 預設為 `/removeintchecks-`。<br /><br /> 指定`/removeintchecks`或`/removeintchecks+`會阻止錯誤檢查，而且可以進行更快速的整數計算。 不過，如果沒有錯誤檢查，和不正確的結果而不會引發錯誤，如果資料型別容量溢位，可能會儲存。|  
  
|在 Visual Studio 中設定 /removeintchecks 整合式開發環境|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.按一下 [編譯] 索引標籤。<br />3.按一下 [ **進階** ] 按鈕。<br />4.值修改為**移除整數溢位檢查**方塊。|  
  
## <a name="example"></a>範例  
 下列程式碼編譯`Test.vb`並關閉整數溢位錯誤檢查。  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
