---
title: 不正確的檔案模式
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: d3d0ebd003f178567ec9e9b19d6baccb8bc15f60
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819979"
---
# <a name="bad-file-mode"></a>不正確的檔案模式
用於管理檔案內容的陳述式必須是適用於開啟檔案的模式。 可能的原因包括：  
  
-   A`FilePutObject`或`FileGetObject`陳述式指定循序檔案。  
  
-   A`Print`陳述式會指定檔案，而不開啟以供存取模式`Output`或`Append`。  
  
-   `Input`陳述式會指定檔案，而不開啟以供存取模式 `Input`  
  
-   嘗試寫入唯讀檔案。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請確定`FilePutObject`並`FileGetObject`只會參考到開啟的檔案`Random`或`Binary`存取。  
  
-   請確定`Print`指定的其中一個開啟的檔案`Output`或`Append`存取模式。 如果不是，將資料放在檔案中，使用不同的陳述式，或重新開啟適當的模式中的檔案。  
  
-   請確定`Input`指定檔案，開啟以供`Input`。 否則，請使用不同的陳述式來將資料放在檔案或重新開啟適當的模式中的檔案。  
  
-   如果您要寫入唯讀檔案，變更檔案的讀取/寫入狀態，或請勿嘗試將寫入其中。  
  
-   使用 `My.Computer.FileSystem` 物件中可用的功能。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileSystem>
- [疑難排解：讀取和寫入文字檔](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
