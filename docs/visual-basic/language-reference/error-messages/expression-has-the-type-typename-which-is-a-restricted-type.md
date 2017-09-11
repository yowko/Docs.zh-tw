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
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b89f7e83bf596c52296a090563d0dd0403ace548
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a><span data-ttu-id="5e31c-102">運算式具有類型 '&lt;typename&gt;' 的受限制的型別，而且不能用來存取繼承自 'Object' 或 'ValueType' 的成員</span><span class="sxs-lookup"><span data-stu-id="5e31c-102">Expression has the type &#39;&lt;typename&gt;&#39; which is a restricted type and cannot be used to access members inherited from &#39;Object&#39; or &#39;ValueType&#39;</span></span>
<span data-ttu-id="5e31c-103">運算式會評估無法 boxed common language runtime (CLR) 型別，但是存取需要進行 boxing 的成員。</span><span class="sxs-lookup"><span data-stu-id="5e31c-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="5e31c-104">*Boxing*是指需要轉換的型別處理`Object`或在某些情況下，為<xref:System.ValueType>。</xref:System.ValueType></span><span class="sxs-lookup"><span data-stu-id="5e31c-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="5e31c-105">Common language runtime 無法方塊某些結構類型，例如<xref:System.ArgIterator>， <xref:System.RuntimeArgumentHandle>，和<xref:System.TypedReference>.</xref:System.TypedReference> </xref:System.RuntimeArgumentHandle> </xref:System.ArgIterator></span><span class="sxs-lookup"><span data-stu-id="5e31c-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="5e31c-106">這個運算式會嘗試使用受限制的型別呼叫方法，繼承自<xref:System.Object>或<xref:System.ValueType>，例如<xref:System.Object.GetHashCode%2A>或<xref:System.Object.ToString%2A>.</xref:System.Object.ToString%2A> </xref:System.Object.GetHashCode%2A> </xref:System.ValueType> </xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="5e31c-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="5e31c-107">若要存取此方法，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]嘗試會造成此錯誤的隱含 boxing 轉換。</span><span class="sxs-lookup"><span data-stu-id="5e31c-107">To access this method, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="5e31c-108">**錯誤識別碼︰** BC31393</span><span class="sxs-lookup"><span data-stu-id="5e31c-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5e31c-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="5e31c-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="5e31c-110">找出評估至所指出類型的運算式。</span><span class="sxs-lookup"><span data-stu-id="5e31c-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2.  <span data-ttu-id="5e31c-111">找出您嘗試呼叫的方法繼承自<xref:System.Object>或<xref:System.ValueType>.</xref:System.ValueType></xref:System.Object>的陳述式的組件</span><span class="sxs-lookup"><span data-stu-id="5e31c-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3.  <span data-ttu-id="5e31c-112">請重寫陳述式，避免在方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="5e31c-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e31c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e31c-113">See Also</span></span>  
 [<span data-ttu-id="5e31c-114">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="5e31c-114">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
