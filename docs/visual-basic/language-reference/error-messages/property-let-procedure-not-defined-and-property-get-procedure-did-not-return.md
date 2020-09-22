---
title: 未定義屬性 let 的程序，而屬性 get 的程序並未傳回物件
ms.date: 07/20/2015
f1_keywords:
- vbrID451
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
ms.openlocfilehash: fbeaa224ea9e095f86c37e571492d83bc98b4397
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871093"
---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a>未定義屬性 let 的程序，而屬性 get 的程序並未傳回物件

某些屬性、方法和作業只能套用至 `Collection` 物件。 您指定了集合專屬的作業或屬性，但物件不是集合。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 檢查物件或屬性名稱的拼寫，或確認物件是 `Collection` 物件。  
  
2. 查看 `Add` 用來將物件加入至集合的方法，以確定語法正確，且任何識別碼拼寫正確。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Collection>
