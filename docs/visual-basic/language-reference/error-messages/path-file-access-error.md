---
title: 路徑檔案存取錯誤
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 83ce8615b173a6f5835347ebc561a793655ec8f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598579"
---
# <a name="pathfile-access-error"></a>路徑/檔案存取錯誤
檔案存取或磁碟存取作業時，作業系統無法建立路徑和檔案名稱之間的連接。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定已正確地格式化檔案規格。 檔案名稱可以包含完整 （絕對） 或相對路徑。 使用磁碟機名稱 （如果路徑在另一個磁碟機上） 開始的完整的路徑，並列出根檔案的明確路徑。 任何不完整的路徑是相對於目前的磁碟機和目錄。  
  
2.  請務必確認您未嘗試儲存檔案，來取代現有的唯讀檔案。 如果這種情況時，變更唯讀屬性的目標檔案，或使用不同的檔案名稱儲存檔案。  
  
3.  請確定您未嘗試開啟唯讀檔案中循序`Output`或`Append`模式。 如果這種情況，請開啟檔案的`Input`模式或變更檔案的唯讀屬性。  
  
4.  請確定您未嘗試變更 Visual Basic 專案中的資料庫或文件。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md)
