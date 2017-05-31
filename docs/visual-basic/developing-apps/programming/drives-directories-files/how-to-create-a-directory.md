---
title: "如何：在 Visual Basic 中建立目錄 | Microsoft Docs"
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 81afe64204fda468f452f86171b15080f9c3d948
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-create-a-directory-in-visual-basic"></a>如何：在 Visual Basic 中建立目錄
使用 `My.Computer.FileSystem` 物件的 `CreateDirectory` 方法來建立目錄。  
  
 如果目錄已經存在，則不會擲回例外狀況。  
  
### <a name="to-create-a-directory"></a>建立目錄  
  
-   指定應該建立目錄之位置的完整路徑，以使用 `CreateDirectory` 方法。 這個範例會在 `C:\Documents and Settings\All Users\Documents` 中建立 `NewDirectory` 目錄。  
  
     [!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   目錄名稱的格式不正確。 例如，它包含不合法的字元，或只有空白字元 (<xref:System.ArgumentException>)。  
  
-   要建立之目錄的父目錄為唯讀 (<xref:System.IO.IOException>)。  
  
-   目錄名稱為 `Nothing` (<xref:System.ArgumentNullException>)。  
  
-   路徑名稱太長 (<xref:System.IO.PathTooLongException>)。  
  
-   路徑包含冒號 ":" (<xref:System.NotSupportedException>)。  
  
-   使用者沒有建立目錄的權限 (<xref:System.UnauthorizedAccessException>)。  
  
-   使用者在部分信任情況下沒有權限 (<xref:System.Security.SecurityException>)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>   
 [建立、刪除和移動檔案和目錄](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
