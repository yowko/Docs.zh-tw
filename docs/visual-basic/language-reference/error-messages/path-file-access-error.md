---
title: 路徑 - 檔案存取錯誤
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 70de8f9cb33ab3d889f4916ae3d5de48cd218092
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871197"
---
# <a name="pathfile-access-error"></a>路徑/檔案存取錯誤

在檔案存取或磁片存取作業期間，作業系統無法建立路徑與檔案名之間的連接。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請確認檔案規格的格式正確。 檔案名可以包含完整的 (絕對) 或相對路徑。 完整路徑的開頭為磁片磁碟機名稱 (如果路徑是在另一個磁片磁碟機上) ，並列出從根目錄到檔案的明確路徑。 任何未完整限定的路徑都是相對於目前磁片磁碟機和目錄。  
  
2. 請確定您未嘗試儲存會取代現有唯讀檔案的檔案。 如果是這種情況，請變更目標檔案的唯讀屬性，或以不同的檔案名儲存檔案。  
  
3. 請確定您未嘗試以連續 `Output` 模式或模式開啟唯讀檔案 `Append` 。 如果是這種情況，請以模式開啟檔案， `Input` 或變更檔案的唯讀屬性。  
  
4. 請確定您未嘗試變更資料庫或檔內的 Visual Basic 專案。  
  
## <a name="see-also"></a>另請參閱

- [錯誤類型](../../programming-guide/language-features/error-types.md)
