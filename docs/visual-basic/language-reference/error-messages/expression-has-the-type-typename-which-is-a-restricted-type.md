---
title: "運算式具有類型 &quot;&lt;typename&gt;&quot; 是受限制的類型以及不能用來存取成員繼承自 &quot;Object&quot; 或 &quot;ValueType&quot; |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc31393
- vbc31393
dev_langs:
- VB
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
caps.latest.revision: 6
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: aaedfd825889498159f92cbd1d615cc0064973d3
ms.lasthandoff: 03/13/2017

---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a>運算式具有類型 '&lt;typename&gt;' 的受限制的型別，而且不能用來存取繼承自 'Object' 或 'ValueType' 的成員
運算式會評估無法 boxed common language runtime (CLR) 型別，但是存取需要進行 boxing 的成員。  
  
 *Boxing*是指需要轉換的型別處理`Object`或在某些情況下，為<xref:System.ValueType>。</xref:System.ValueType> Common language runtime 無法方塊某些結構類型，例如<xref:System.ArgIterator>， <xref:System.RuntimeArgumentHandle>，和<xref:System.TypedReference>.</xref:System.TypedReference> </xref:System.RuntimeArgumentHandle> </xref:System.ArgIterator>  
  
 這個運算式會嘗試使用受限制的型別呼叫方法，繼承自<xref:System.Object>或<xref:System.ValueType>，例如<xref:System.Object.GetHashCode%2A>或<xref:System.Object.ToString%2A>.</xref:System.Object.ToString%2A> </xref:System.Object.GetHashCode%2A> </xref:System.ValueType> </xref:System.Object> 若要存取此方法，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]嘗試會造成此錯誤的隱含 boxing 轉換。  
  
 **錯誤識別碼︰** BC31393  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  找出評估至所指出類型的運算式。  
  
2.  找出您嘗試呼叫的方法繼承自<xref:System.Object>或<xref:System.ValueType>.</xref:System.ValueType></xref:System.Object>的陳述式的組件  
  
3.  請重寫陳述式，避免在方法呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
