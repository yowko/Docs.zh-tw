---
title: 無法完成作業，因為目標目錄在來源目錄底下
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: 253e7ff1d457827a2e1cb9f64eae4bfa971a3798
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645869"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a>無法完成作業，因為目標目錄在來源目錄底下
循環作業失敗。 循環作業會循環，因此無法完成。 例如，物件 A 可能會嘗試繼承自物件 B，而物件 B 又接著繼承自物件 A。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   繼承時，請確定沒有循環參考。  
  
## <a name="see-also"></a>另請參閱
- [錯誤類型](../../visual-basic/programming-guide/language-features/error-types.md)
- [偵錯基本概念：中斷點](https://msdn.microsoft.com/library/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
