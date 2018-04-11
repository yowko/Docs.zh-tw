---
title: 不正確的檔案模式
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a540135727eb97f4df5027e2ded7271e21bb4648
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-mode"></a>不正確的檔案模式
管理檔案內容中使用的陳述式必須是適當的模式開啟檔案。 可能的原因包括：  
  
-   A`FilePutObject`或`FileGetObject`陳述式指定循序檔案。  
  
-   A`Print`陳述式指定以外的存取模式開啟的檔案`Output`或`Append`。  
  
-   `Input`陳述式指定以外的存取模式開啟的檔案`Input`  
  
-   嘗試寫入唯讀檔案。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請確定`FilePutObject`和`FileGetObject`檔案開啟為僅參考`Random`或`Binary`存取。  
  
-   請確定`Print`指定其中一個開啟的檔案`Output`或`Append`存取模式。 如果不是，將資料放在檔案中，使用不同的陳述式，或重新開啟適當的模式中的檔案。  
  
-   請確定`Input`指定檔案，開啟以供`Input`。 否則，請使用不同的陳述式將資料放在檔案或重新開啟適當的模式中的檔案。  
  
-   如果您要寫入唯讀檔案，變更檔案的讀取/寫入狀態，或請勿嘗試寫入其中。  
  
-   使用 `My.Computer.FileSystem` 物件中可用的功能。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.FileSystem>  
 [疑難排解：讀取和寫入文字檔](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
