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
# <a name="expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a><span data-ttu-id="67024-102">運算式包含類型 '\<typename>'，其為受限制的類型且不可用來存取繼承自 'Object' 或 'ValueType' 的成員</span><span class="sxs-lookup"><span data-stu-id="67024-102">Expression has the type '\<typename>' which is a restricted type and cannot be used to access members inherited from 'Object' or 'ValueType'</span></span>
<span data-ttu-id="67024-103">運算式會評估為無法由 common language runtime （CLR）所封裝的類型，但會存取需要進行裝箱的成員。</span><span class="sxs-lookup"><span data-stu-id="67024-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="67024-104">*Boxing* 是指將類型轉換為 `Object` 或者，在某些情況下，轉換為 <xref:System.ValueType>時所需的處理。</span><span class="sxs-lookup"><span data-stu-id="67024-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="67024-105">Common language runtime 無法 box 某些結構類型，例如、 <xref:System.ArgIterator> <xref:System.RuntimeArgumentHandle> 和 <xref:System.TypedReference> 。</span><span class="sxs-lookup"><span data-stu-id="67024-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="67024-106">這個運算式會嘗試使用受限制的類型來呼叫繼承自或的方法 <xref:System.Object> <xref:System.ValueType> ，例如 <xref:System.Object.GetHashCode%2A> 或 <xref:System.Object.ToString%2A> 。</span><span class="sxs-lookup"><span data-stu-id="67024-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="67024-107">若要存取這個方法，Visual Basic 嘗試了造成此錯誤的隱含裝箱轉換。</span><span class="sxs-lookup"><span data-stu-id="67024-107">To access this method, Visual Basic has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="67024-108">**錯誤識別碼：** BC31393</span><span class="sxs-lookup"><span data-stu-id="67024-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="67024-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="67024-109">To correct this error</span></span>  
  
1. <span data-ttu-id="67024-110">找出評估至所指出類型的運算式。</span><span class="sxs-lookup"><span data-stu-id="67024-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2. <span data-ttu-id="67024-111">找出嘗試呼叫從或繼承之方法的語句部分 <xref:System.Object> <xref:System.ValueType> 。</span><span class="sxs-lookup"><span data-stu-id="67024-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3. <span data-ttu-id="67024-112">請重寫語句，以避免方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="67024-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67024-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67024-113">See also</span></span>

- [<span data-ttu-id="67024-114">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="67024-114">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
