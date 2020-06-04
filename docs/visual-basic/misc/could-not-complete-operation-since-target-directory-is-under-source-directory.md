---
title: 無法完成作業，因為目標目錄在來源目錄底下
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 46ec7ae452d4f8259d0f8ca3a896d1b29151ed61
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84376738"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a>無法完成作業，因為目標目錄在來源目錄底下
循環作業失敗。 循環作業會循環，因此無法完成。 例如，物件 A 可能會嘗試繼承自物件 B，而物件 B 又接著繼承自物件 A。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 繼承時，請確定沒有循環參考。  
  
## <a name="see-also"></a>另請參閱

- [錯誤類型](../programming-guide/language-features/error-types.md)
- [在 Visual Studio 偵錯工具中使用中斷點](/visualstudio/debugger/using-breakpoints)
