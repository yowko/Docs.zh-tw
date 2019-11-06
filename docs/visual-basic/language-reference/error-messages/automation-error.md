---
title: Automation 錯誤
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: 25c3b71eb818223c58ab17d9be885033a5d4ded0
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197042"
---
# <a name="automation-error"></a>Automation 錯誤
執行方法，或取得或設定物件變數的屬性時發生錯誤。 錯誤由建立物件的應用程式所回報。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 檢查 `Err` 物件的屬性，判斷錯誤的來源和本質。  
  
2. 在存取陳述式之前使用 `On Error Resume Next` 陳述式，然後在存取陳述式之後立即檢查錯誤。  
  
## <a name="see-also"></a>請參閱

- [錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md)
- [告訴我們](/visualstudio/ide/feedback-options)
