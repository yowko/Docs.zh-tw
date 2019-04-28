---
title: 未定義屬性 let 的程序，而屬性 get 的程序並未傳回物件
ms.date: 07/20/2015
f1_keywords:
- vbrID451
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
ms.openlocfilehash: 7da1de98132f47740e805ed34ff3890f0ba0f889
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920741"
---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a>未定義屬性 let 的程序，而屬性 get 的程序並未傳回物件
特定屬性、 方法和作業只能套用至`Collection`物件。 您指定的作業或是專為集合的屬性，但該物件不是集合。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 物件或屬性名稱的拼字檢查或確認物件是否`Collection`物件。  
  
2. 看看`Add`方法用來將物件加入至集合，以便能確定語法是否正確，以及任何識別項的拼字是否正確。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Collection>
