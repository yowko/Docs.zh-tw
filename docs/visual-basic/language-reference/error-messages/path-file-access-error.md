---
title: "路徑檔案存取錯誤 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID75
dev_langs:
- VB
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ac730bac76540331206daebe600445ca54cc15a9
ms.lasthandoff: 03/13/2017

---
# <a name="pathfile-access-error"></a>路徑/檔案存取錯誤
在檔案存取或磁碟存取作業時，作業系統無法建立路徑和檔案名稱之間的連接。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定已正確格式化檔案規格。 檔案名稱可以包含完整 （絕對） 或相對路徑。 使用磁碟機名稱 （如果路徑是另一個磁碟機上） 開始的完整的路徑，並列出檔案從根的明確路徑。 任何不完整的路徑是相對於目前的磁碟機和目錄。  
  
2.  請確定您沒有不嘗試儲存檔案，來取代現有的唯讀檔案。 這種情況，如果變更唯讀屬性的目標檔案，或使用不同的檔案名稱儲存檔案。  
  
3.  請確定您未嘗試開啟唯讀檔案中循序`Output`或`Append`模式。 如果這種情況，在檔案開啟`Input`模式或變更檔案的唯讀屬性。  
  
4.  請確定您未嘗試變更[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]資料庫或文件中的專案。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md)
