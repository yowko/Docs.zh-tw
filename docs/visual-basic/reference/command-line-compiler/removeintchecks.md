---
title: "/removeintchecks |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
dev_langs:
- VB
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8e50200b8755ccc6b1c173024856955f5075b67e
ms.lasthandoff: 03/13/2017

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
|`+` &#124; `-`|選擇項。 `/removeintchecks-`選項會使編譯器檢查所有的整數計算的溢位錯誤。 預設為 `/removeintchecks-`。<br /><br /> 指定`/removeintchecks`或`/removeintchecks+`防止錯誤檢查，並能更快的整數計算。 不過，如果沒有錯誤檢查，以及如果資料型別容量溢位，可能會不正確的結果儲存而不會引發錯誤。|  
  
|在 Visual Studio 中設定 /removeintchecks 整合式開發環境|  
|---|  
|1.在 **方案總管**中選取專案。 在**專案**] 功能表上，按一下 [**屬性**。 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.按一下 [編譯]**** 索引標籤。<br />3.按一下 [ **進階** ] 按鈕。<br />4.修改的值**移除整數的溢位檢查**方塊。|  
  
## <a name="example"></a>範例  
 下列程式碼編譯`Test.vb`並關閉整數溢位錯誤檢查。  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
