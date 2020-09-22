---
title: DirectCast 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 7b070b8eba240440821f7984a9336c2ecaf61706
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867082"
---
# <a name="directcast-operator-visual-basic"></a>DirectCast 運算子 (Visual Basic)

引進型別轉換作業（以繼承或實作為基礎）。  
  
## <a name="remarks"></a>備註  

 `DirectCast` 不會使用 Visual Basic 執行時間 helper 常式進行轉換，因此它可以提供比 `CType` 轉換成和轉換資料類型時更好的效能 `Object` 。  
  
 您可以使用 `DirectCast` 類似于使用 [CType 函數](../functions/ctype-function.md) 和 [TryCast 運算子](trycast-operator.md) 關鍵字的關鍵字。 您會提供運算式做為第一個引數，以及將它轉換為第二個引數的類型。 `DirectCast` 需要兩個引數的資料類型之間的繼承或實現關聯性。 這表示一個類型必須繼承自另一個型別或從中執行。  
  
## <a name="errors-and-failures"></a>錯誤和失敗  

 `DirectCast` 如果偵測到沒有繼承或實現關聯性存在，則會產生編譯器錯誤。 但是缺少編譯器錯誤並不保證成功轉換。 如果所需的轉換是縮小，則在執行時間可能會失敗。 如果發生這種情況，則執行時間會擲回 <xref:System.InvalidCastException> 錯誤。  
  
## <a name="conversion-keywords"></a>轉換關鍵字  

 類型轉換關鍵字的比較如下所示。  
  
|關鍵字|資料類型|引數關聯性|運行時失敗|  
|---|---|---|---|  
|[CType Function](../functions/ctype-function.md)|任何資料類型|必須在兩個資料類型之間定義擴展或縮小轉換|拋出 <xref:System.InvalidCastException>|  
|`DirectCast`|任何資料類型|一種類型必須繼承自或執行其他類型|拋出 <xref:System.InvalidCastException>|  
|[TryCast 運算子](trycast-operator.md)|僅限參考型別|一種類型必須繼承自或執行其他類型|不傳回[任何](../nothing.md)專案|  
  
## <a name="example"></a>範例  

 下列範例示範兩個的用法 `DirectCast` ，一個在執行時間失敗，另一個則成功。  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 在上述範例中，的執行時間類型 `q` 為 `Double` 。 `CType` 成功 `Double` ，因為可以轉換成 `Integer` 。 不過，第一次 `DirectCast` 在執行時間失敗，因為的執行時間型別 `Double` 與之間沒有繼承關聯性 `Integer` ，即使轉換存在也一樣。 第二個是 `DirectCast` 成功的，因為它會從型別轉換 <xref:System.Windows.Forms.Form> 成型別 <xref:System.Windows.Forms.Control> ，從中 <xref:System.Windows.Forms.Form> 繼承。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [隱含和明確轉換](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
