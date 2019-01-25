---
title: 路徑 / 檔案存取錯誤
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 53f021faa9e4ae69a71d825ca823e1180421afc6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522475"
---
# <a name="pathfile-access-error"></a>路徑/檔案存取錯誤
存取檔案或磁碟存取作業時，作業系統可能進行的路徑和檔案名稱之間的連線。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定已正確地格式化檔案規格。 檔案名稱可以包含完整 （絕對） 或相對路徑。 （如果路徑在另一個磁碟機上），磁碟機名稱開頭的完整的路徑，並列出該檔案從根的明確路徑。 任何不完整的路徑是相對於目前的磁碟機和目錄。  
  
2.  請確定您沒有不嘗試儲存檔案，其中會取代現有的唯讀檔案。 如果發生這種情況，變更唯讀屬性的目標檔案，或使用不同的檔案名稱儲存檔案。  
  
3.  請確定您未嘗試開啟唯讀檔案，在循序`Output`或`Append`模式。 如果發生這種情況，請開啟檔案的`Input`模式或變更檔案的唯讀屬性。  
  
4.  請確定您未嘗試變更 Visual Basic 專案中的資料庫或文件。  
  
## <a name="see-also"></a>另請參閱
- [錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md)
