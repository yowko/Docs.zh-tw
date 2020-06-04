---
title: 運算式包含類型 '<typename>'，其為受限制的類型且不可用來存取繼承自 'Object' 或 'ValueType' 的成員
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 0eb30488312cc7519f39a6b819aea15489f2f70a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409516"
---
# <a name="expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a>運算式包含類型 '\<typename>'，其為受限制的類型且不可用來存取繼承自 'Object' 或 'ValueType' 的成員
運算式會評估為無法由 common language runtime （CLR）所封裝的類型，但會存取需要進行裝箱的成員。  
  
 *Boxing* 是指將類型轉換為 `Object` 或者，在某些情況下，轉換為 <xref:System.ValueType>時所需的處理。 Common language runtime 無法 box 某些結構類型，例如、 <xref:System.ArgIterator> <xref:System.RuntimeArgumentHandle> 和 <xref:System.TypedReference> 。  
  
 這個運算式會嘗試使用受限制的類型來呼叫繼承自或的方法 <xref:System.Object> <xref:System.ValueType> ，例如 <xref:System.Object.GetHashCode%2A> 或 <xref:System.Object.ToString%2A> 。 若要存取這個方法，Visual Basic 嘗試了造成此錯誤的隱含裝箱轉換。  
  
 **錯誤識別碼：** BC31393  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 找出評估至所指出類型的運算式。  
  
2. 找出嘗試呼叫從或繼承之方法的語句部分 <xref:System.Object> <xref:System.ValueType> 。  
  
3. 請重寫語句，以避免方法呼叫。  
  
## <a name="see-also"></a>另請參閱

- [隱含和明確轉換](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
