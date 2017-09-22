---
title: "如何：在 Visual Basic 中建立目錄"
ms.custom: 
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
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
caps.latest.revision: 19
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1a45a785916b480dcee6e36fd295390266eaa0a0
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# How to: Create a Directory in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

使用 `My.Computer.FileSystem` 物件的 `CreateDirectory` 方法建立目錄。  
  
 如果資料夾已存在，則不會擲回例外狀況。  
  
### 若要建立目錄  
  
-   使用 `CreateDirectory` 方法，指定要建立目錄之位置的完整路徑。  這個範例會在 `C:\Documents and Settings\All Users\Documents` 中建立目錄 `NewDirectory`。  
  
     [!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]  
  
## 穩固程式設計  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   目錄名稱錯誤。  例如，它包含不合法的字元或只是泛空白字元 \(<xref:System.ArgumentException>\)。  
  
-   所要建立之目錄的父目錄是唯讀的 \(<xref:System.IO.IOException>\)。  
  
-   目錄名稱是 `Nothing` \(<xref:System.ArgumentNullException>\)。  
  
-   目錄名稱太長 \(<xref:System.IO.PathTooLongException>\)。  
  
-   目錄名稱是冒號 ":" \(<xref:System.NotSupportedException>\)。  
  
-   使用者沒有建立目錄的權限 \(<xref:System.UnauthorizedAccessException>\)。  
  
-   使用者在部分信任情況下缺乏必要的權限 \(<xref:System.Security.SecurityException>\)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>   
 [建立、刪除和移動檔案和目錄](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)

