---
title: 路徑 - 檔案存取錯誤
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: dfe96cd6eaa673438849fe8f799d46fa2617bfdd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387253"
---
# <a name="pathfile-access-error"></a>路徑/檔案存取錯誤
在檔案存取或磁片存取作業期間，作業系統無法建立路徑與檔案名之間的連接。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請確定檔案規格的格式正確。 檔案名可以包含完整（絕對）或相對路徑。 完整路徑的開頭是磁片磁碟機名稱（如果路徑是在另一個磁片磁碟機上），並列出從根目錄到檔案的明確路徑。 任何不完整的路徑都是相對於目前的磁片磁碟機和目錄。  
  
2. 請確定您未嘗試儲存會取代現有唯讀檔案的檔案。 如果是這種情況，請變更目標檔案的唯讀屬性，或以不同的檔案名儲存檔案。  
  
3. 請確定您未嘗試以連續或模式開啟唯讀檔案 `Output` `Append` 。 如果是這種情況，請在模式中開啟檔案， `Input` 或變更檔案的唯讀屬性。  
  
4. 請確定您未嘗試變更資料庫或檔中的 Visual Basic 專案。  
  
## <a name="see-also"></a>另請參閱

- [錯誤類型](../../programming-guide/language-features/error-types.md)
