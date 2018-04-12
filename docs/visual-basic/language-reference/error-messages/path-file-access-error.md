---
title: 路徑檔案存取錯誤
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c86d46c884617be152a5954426e9ddd6ef61651
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="pathfile-access-error"></a>路徑/檔案存取錯誤
檔案存取或磁碟存取作業時，作業系統無法建立路徑和檔案名稱之間的連接。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定已正確地格式化檔案規格。 檔案名稱可以包含完整 （絕對） 或相對路徑。 使用磁碟機名稱 （如果路徑在另一個磁碟機上） 開始的完整的路徑，並列出根檔案的明確路徑。 任何不完整的路徑是相對於目前的磁碟機和目錄。  
  
2.  請務必確認您未嘗試儲存檔案，來取代現有的唯讀檔案。 如果這種情況時，變更唯讀屬性的目標檔案，或使用不同的檔案名稱儲存檔案。  
  
3.  請確定您未嘗試開啟唯讀檔案中循序`Output`或`Append`模式。 如果這種情況，請開啟檔案的`Input`模式或變更檔案的唯讀屬性。  
  
4.  請確定您未嘗試變更[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]資料庫或文件中的專案。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md)
