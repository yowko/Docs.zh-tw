---
title: TryCast 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: dc4807781f9e1aaf894016952911bd7b32c42948
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875321"
---
# <a name="trycast-operator-visual-basic"></a>TryCast 運算子 (Visual Basic)

引進不會擲回例外狀況的類型轉換作業。  
  
## <a name="remarks"></a>備註  

 如果嘗試的轉換失敗， `CType` 而且 `DirectCast` 兩者都會擲回 <xref:System.InvalidCastException> 錯誤。 這可能會對應用程式的效能造成負面影響。 `TryCast` 不會傳回 [任何](../nothing.md)專案，因此，您只需要針對傳回的結果進行測試，而不需要處理可能的例外狀況 `Nothing` 。  
  
 使用 `TryCast` 關鍵字的方式與使用 [CType 函數](../functions/ctype-function.md) 和 [DirectCast 運算子](directcast-operator.md) 關鍵字的方式相同。 您會提供運算式做為第一個引數，以及將它轉換為第二個引數的類型。 `TryCast` 只在參考型別上運作，例如類別和介面。 它需要兩個類型之間的繼承或實現關聯性。 這表示一個類型必須繼承自另一個型別或從中執行。  
  
## <a name="errors-and-failures"></a>錯誤和失敗  

 `TryCast` 如果偵測到沒有繼承或實現關聯性存在，則會產生編譯器錯誤。 但是缺少編譯器錯誤並不保證成功轉換。 如果所需的轉換是縮小，則在執行時間可能會失敗。 如果發生這種情況，則不會傳回 `TryCast` [任何內容](../nothing.md)。  
  
## <a name="conversion-keywords"></a>轉換關鍵字  

 類型轉換關鍵字的比較如下所示。  
  
|關鍵字|資料類型|引數關聯性|運行時失敗|  
|---|---|---|---|  
|[CType Function](../functions/ctype-function.md)|任何資料類型|必須在兩個資料類型之間定義擴展或縮小轉換|拋出 <xref:System.InvalidCastException>|  
|[DirectCast 運算子](directcast-operator.md)|任何資料類型|一種類型必須繼承自或執行其他類型|拋出 <xref:System.InvalidCastException>|  
|`TryCast`|僅限參考型別|一種類型必須繼承自或執行其他類型|不傳回[任何](../nothing.md)專案|  
  
## <a name="example"></a>範例  

 下列範例示範如何使用 `TryCast`。  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [隱含和明確轉換](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
