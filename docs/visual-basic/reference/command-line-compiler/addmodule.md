---
title: "/addmodule |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 949962905ec933dc42301bf8c21654e73dbe2f70
ms.lasthandoff: 03/13/2017

---
# <a name="addmodule"></a>/addmodule
讓編譯器將所指定檔案的類型資訊全部提供給您目前編譯的專案。  
  
## <a name="syntax"></a>語法  
  
```  
/addmodule:fileList  
```  
  
## <a name="arguments"></a>引數  
 `fileList`  
 必要項。 檔案所含的中繼資料，但不是包含組件資訊清單的逗號分隔清單。 應該以引號括住包含空格的檔案名稱 ("")。  
  
## <a name="remarks"></a>備註  
 所列出的檔案`fileList`參數必須與建立`/target:module`選項，或以其他編譯器相當於`/target:module`。  
  
 加上的所有模組`/addmodule`必須位於相同的目錄和輸出檔在執行階段。 也就是說，您可以在任何目錄指定模組在編譯時期，但該模組在執行階段時，必須在應用程式目錄。 如果不是，您收到<xref:System.TypeLoadException>錯誤。</xref:System.TypeLoadException>  
  
 如果您指定 （隱含或明確） 任何[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)以外的其他選項`/target:module`與`/addmodule`，傳遞至檔案`/addmodule`成為專案的組件的一部分。 組件，才可執行的輸出檔，都有一個或多個檔案加入`/addmodule`。  
  
 使用[/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)從包含組件檔案匯入中繼資料。  
  
> [!NOTE]
>  `/addmodule`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。  
  
## <a name="example"></a>範例  
 下列程式碼會建立模組。  
  
 [!code-vb[VbVbalrCompiler #&47;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 下列程式碼會匯入模組的型別。  
  
 [!code-vb[VbVbalrCompiler #&48;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 當您執行`t1`，它會輸出`802`。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
