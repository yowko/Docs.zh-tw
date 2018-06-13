---
title: 編譯器所產生的例外狀況 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: a1746a492685cf25869bd06935bfd056de257fea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331437"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="f652e-102">編譯器所產生的例外狀況 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="f652e-102">Compiler-Generated Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="f652e-103">基本作業失敗時，.NET Framework 的 Common Language Runtime (CLR) 會自動擲回一些例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f652e-103">Some exceptions are thrown automatically by the .NET Framework's common language runtime (CLR) when basic operations fail.</span></span> <span data-ttu-id="f652e-104">下表列出這些例外狀況和其錯誤條件。</span><span class="sxs-lookup"><span data-stu-id="f652e-104">These exceptions and their error conditions are listed in the following table.</span></span>  
  
|<span data-ttu-id="f652e-105">例外</span><span class="sxs-lookup"><span data-stu-id="f652e-105">Exception</span></span>|<span data-ttu-id="f652e-106">描述</span><span class="sxs-lookup"><span data-stu-id="f652e-106">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|<span data-ttu-id="f652e-107">在算術運算期間所發生的例外狀況 (例如 <xref:System.DivideByZeroException> 和 <xref:System.OverflowException>) 的基底類別。</span><span class="sxs-lookup"><span data-stu-id="f652e-107">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|  
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="f652e-108">陣列因項目的實際類型與陣列的實際類型不相容而無法儲存指定的項目時擲回。</span><span class="sxs-lookup"><span data-stu-id="f652e-108">Thrown when an array cannot store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|  
|<xref:System.DivideByZeroException>|<span data-ttu-id="f652e-109">嘗試將整數值除以零時擲回。</span><span class="sxs-lookup"><span data-stu-id="f652e-109">Thrown when an attempt is made to divide an integral value by zero.</span></span>|  
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="f652e-110">索引小於零或超出陣列界限時嘗試編製陣列的索引時擲回。</span><span class="sxs-lookup"><span data-stu-id="f652e-110">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|  
|<xref:System.InvalidCastException>|<span data-ttu-id="f652e-111">從基底類型到介面或衍生類型的明確轉換在執行階段失敗時擲回。</span><span class="sxs-lookup"><span data-stu-id="f652e-111">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|  
|<xref:System.NullReferenceException>|<span data-ttu-id="f652e-112">嘗試參考值為 [null](../../../csharp/language-reference/keywords/null.md) 的物件時擲回。</span><span class="sxs-lookup"><span data-stu-id="f652e-112">Thrown when you attempt to reference an object whose value is [null](../../../csharp/language-reference/keywords/null.md).</span></span>|  
|<xref:System.OutOfMemoryException>|<span data-ttu-id="f652e-113">嘗試使用 [new](../../../csharp/language-reference/keywords/new-operator.md) 運算子配置記憶體失敗時擲回。</span><span class="sxs-lookup"><span data-stu-id="f652e-113">Thrown when an attempt to allocate memory using the [new](../../../csharp/language-reference/keywords/new-operator.md) operator fails.</span></span> <span data-ttu-id="f652e-114">這表示 Common Language Runtime 的可用記憶體己用完。</span><span class="sxs-lookup"><span data-stu-id="f652e-114">This indicates that the memory available to the common language runtime has been exhausted.</span></span>|  
|<xref:System.OverflowException>|<span data-ttu-id="f652e-115">`checked` 內容中的算術運算溢位時擲回。</span><span class="sxs-lookup"><span data-stu-id="f652e-115">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|  
|<xref:System.StackOverflowException>|<span data-ttu-id="f652e-116">在因太多暫止方法呼叫而耗盡執行堆疊時擲回；通常表示非常深或無限遞迴。</span><span class="sxs-lookup"><span data-stu-id="f652e-116">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|  
|<xref:System.TypeInitializationException>|<span data-ttu-id="f652e-117">在靜態建構函式擲回例外狀況而且沒有相容的 `catch` 子句可攔截它時擲回。</span><span class="sxs-lookup"><span data-stu-id="f652e-117">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f652e-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="f652e-118">See Also</span></span>  
 [<span data-ttu-id="f652e-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f652e-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f652e-120">例外狀況和例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="f652e-120">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)  
 [<span data-ttu-id="f652e-121">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="f652e-121">Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/exception-handling.md)  
 [<span data-ttu-id="f652e-122">try-catch</span><span class="sxs-lookup"><span data-stu-id="f652e-122">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="f652e-123">try-finally</span><span class="sxs-lookup"><span data-stu-id="f652e-123">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)  
 [<span data-ttu-id="f652e-124">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="f652e-124">try-catch-finally</span></span>](../../../csharp/language-reference/keywords/try-catch-finally.md)
