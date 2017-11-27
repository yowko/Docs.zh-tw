---
title: "運算式具有類型 &#39;&lt;typename&gt;&#39; 這是受限制的類型，且無法用來存取成員繼承自 &#39; 物件 &#39; 或 &#39;ValueType &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords: BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a30742bd46ccd1a3e5a688ebd2621e2c8a3d50e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a><span data-ttu-id="4caf1-102">運算式具有類型 &#39;&lt;typename&gt;&#39; 這是受限制的類型，且無法用來存取成員繼承自 &#39; 物件 &#39; 或 &#39;ValueType &#39;</span><span class="sxs-lookup"><span data-stu-id="4caf1-102">Expression has the type &#39;&lt;typename&gt;&#39; which is a restricted type and cannot be used to access members inherited from &#39;Object&#39; or &#39;ValueType&#39;</span></span>
<span data-ttu-id="4caf1-103">運算式評估為 common language runtime (CLR) 無法 box 處理的類型，但是會存取需要進行 boxing 的成員。</span><span class="sxs-lookup"><span data-stu-id="4caf1-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="4caf1-104">*Boxing* 是指將類型轉換為 `Object` 或者，在某些情況下，轉換為 <xref:System.ValueType>時所需的處理。</span><span class="sxs-lookup"><span data-stu-id="4caf1-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="4caf1-105">Common language runtime 無法 box 處理某些結構類型，例如<xref:System.ArgIterator>， <xref:System.RuntimeArgumentHandle>，和<xref:System.TypedReference>。</span><span class="sxs-lookup"><span data-stu-id="4caf1-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="4caf1-106">這個運算式會嘗試使用受限的類型呼叫的方法繼承自<xref:System.Object>或<xref:System.ValueType>，例如<xref:System.Object.GetHashCode%2A>或<xref:System.Object.ToString%2A>。</span><span class="sxs-lookup"><span data-stu-id="4caf1-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="4caf1-107">若要存取此方法，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]嘗試會造成這個錯誤的隱含 boxing 轉換。</span><span class="sxs-lookup"><span data-stu-id="4caf1-107">To access this method, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="4caf1-108">**錯誤 ID:** BC31393</span><span class="sxs-lookup"><span data-stu-id="4caf1-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4caf1-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="4caf1-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="4caf1-110">找出評估至所指出類型的運算式。</span><span class="sxs-lookup"><span data-stu-id="4caf1-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2.  <span data-ttu-id="4caf1-111">找出您嘗試呼叫的方法繼承自的陳述式的一部分<xref:System.Object>或<xref:System.ValueType>。</span><span class="sxs-lookup"><span data-stu-id="4caf1-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3.  <span data-ttu-id="4caf1-112">請重寫陳述式，避免在方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="4caf1-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4caf1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4caf1-113">See Also</span></span>  
 [<span data-ttu-id="4caf1-114">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="4caf1-114">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
