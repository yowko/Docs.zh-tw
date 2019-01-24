---
title: 運算式包含類型&#39; &lt;typename&gt; &#39;其為受限制的類型且不能用來存取成員繼承自&#39;物件&#39;或&#39;ValueType&#39;
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: d44b9a29f0848508d8cd814e857d9b01819ce7ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535953"
---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a>運算式包含類型&#39; &lt;typename&gt; &#39;其為受限制的類型且不能用來存取成員繼承自&#39;物件&#39;或&#39;ValueType&#39;
運算式評估為 common language runtime (CLR) 無法 box 處理的類型，但是會存取需要 boxing 處理的成員。  
  
 *Boxing* 是指將類型轉換為 `Object` 或者，在某些情況下，轉換為 <xref:System.ValueType>時所需的處理。 Common language runtime 無法 box 處理某些結構類型，例如<xref:System.ArgIterator>， <xref:System.RuntimeArgumentHandle>，和<xref:System.TypedReference>。  
  
 這個運算式會嘗試使用受限制的型別呼叫方法，繼承自<xref:System.Object>或是<xref:System.ValueType>，例如<xref:System.Object.GetHashCode%2A>或<xref:System.Object.ToString%2A>。 若要存取此方法，Visual Basic 嘗試會導致此錯誤的隱含 boxing 轉換。  
  
 **錯誤 ID:** BC31393  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  找出評估至所指出類型的運算式。  
  
2.  找出您嘗試呼叫的方法繼承自的陳述式的一部分<xref:System.Object>或<xref:System.ValueType>。  
  
3.  請重寫陳述式，以避免在方法呼叫。  
  
## <a name="see-also"></a>另請參閱
- [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
