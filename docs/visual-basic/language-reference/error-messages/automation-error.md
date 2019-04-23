---
title: Automation 錯誤
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: 8370f744b916ce4a797c808ed58c5fc9580e6278
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304307"
---
# <a name="automation-error"></a>Automation 錯誤
執行方法，或取得或設定物件變數的屬性時發生錯誤。 錯誤由建立物件的應用程式所回報。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 檢查 `Err` 物件的屬性，判斷錯誤的來源和本質。  
  
2. 在存取陳述式之前使用 `On Error Resume Next` 陳述式，然後在存取陳述式之後立即檢查錯誤。  
  
## <a name="see-also"></a>另請參閱

- [錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md)
- [告訴我們](/visualstudio/ide/talk-to-us)
