---
title: 指定給事件記錄檔的名稱無效
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 2b9c934272d0f3392c845dcd2f0062a98dc50c7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940669"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a>指定給事件記錄檔的名稱無效
指定給事件記錄檔的名稱無效。 這通常是名稱中有無效的字元、檔案名稱空白或檔案名稱太長的結果。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 如果指定的名稱超過八個字元，請確定該名稱未與其他事件記錄檔的名稱相衝突。 判斷此名稱是否唯一時，只會評估前八個字元。  
  
- 如果提供路徑，請確定已正確地剖析該路徑。  
  
- 檢查名稱中沒有無效的字元。 不能在檔案名稱中使用的字元包括 `<`、 `>`、 `:`、 `"`、 `/`、 `\`和 `|`。  
  
## <a name="see-also"></a>另請參閱

- [如何：剖析檔案路徑](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [如何：重新命名檔案](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
