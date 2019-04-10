---
title: 使用權限遭拒 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID70
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
ms.openlocfilehash: ad75c556748bf5c0f9cef55310c4ffa7b01fd458
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318825"
---
# <a name="permission-denied-visual-basic"></a>使用權限遭拒 (Visual Basic)
已嘗試寫入防寫保護的磁碟，或存取鎖定的檔案。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 若要開啟防寫保護的檔案，變更檔案的寫入保護屬性。  
  
2. 請確定其他處理序不會鎖定檔案，並等候開啟檔案，直到其他處理序釋放它為止。  
  
3. 若要存取登錄，請檢查您的使用者權限包含這種類型的登錄存取權。  
  
## <a name="see-also"></a>另請參閱

- [錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md)
