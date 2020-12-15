---
title: '如何執行和呼叫自訂擴充方法-c # 程式設計手冊'
description: 瞭解如何針對任何 .NET 類型執行擴充方法。 用戶端程式代碼可以藉由加入 DLL 的參考並新增 using 指示詞，來使用您的方法。
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 4ae48a05d451a3276b3a0f2ee4d6c633ce7db306
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513002"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="bf925-104">如何執行和呼叫自訂擴充方法 (c # 程式設計手冊) </span><span class="sxs-lookup"><span data-stu-id="bf925-104">How to implement and call a custom extension method (C# Programming Guide)</span></span>

<span data-ttu-id="bf925-105">本主題示範如何針對任何 .NET 類型實作您自己的延伸模組方法。</span><span class="sxs-lookup"><span data-stu-id="bf925-105">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="bf925-106">用戶端程式碼可以使用您的擴充方法，方法是將參考新增至包含這些方法的 DLL，然後新增 [using](../../language-reference/keywords/using-directive.md) 指示詞，以指定會在其中定義擴充方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="bf925-106">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="bf925-107">定義和呼叫擴充方法</span><span class="sxs-lookup"><span data-stu-id="bf925-107">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="bf925-108">定義靜態[類別](./static-classes-and-static-class-members.md)以包含擴充方法。</span><span class="sxs-lookup"><span data-stu-id="bf925-108">Define a static [class](./static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="bf925-109">此類別對用戶端程式碼而言必須是可見的。</span><span class="sxs-lookup"><span data-stu-id="bf925-109">The class must be visible to client code.</span></span> <span data-ttu-id="bf925-110">如需存取範圍規則的詳細資訊，請參閱[存取修飾詞](./access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="bf925-110">For more information about accessibility rules, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="bf925-111">將擴充方法實作為其可見度至少等同於包含類別的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="bf925-111">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="bf925-112">方法的第一個參數會指定方法的作業類型，前面必須加上 [this](../../language-reference/keywords/this.md) 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="bf925-112">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="bf925-113">在呼叫程式碼中，新增 `using` 指示詞以指定包含擴充方法類別的[命名空間](../../language-reference/keywords/namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="bf925-113">In the calling code, add a `using` directive to specify the [namespace](../../language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="bf925-114">將方法當做是類型上的執行個體方法進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="bf925-114">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="bf925-115">請注意，呼叫程式碼未指定第一個參數，因為它代表要套用運算子的類型，而且編譯器已知物件類型。</span><span class="sxs-lookup"><span data-stu-id="bf925-115">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="bf925-116">您只需要針對參數 2 到 `n` 提供引數。</span><span class="sxs-lookup"><span data-stu-id="bf925-116">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf925-117">範例</span><span class="sxs-lookup"><span data-stu-id="bf925-117">Example</span></span>  

 <span data-ttu-id="bf925-118">下列範例會在 `CustomExtensions.StringExtension` 類別中實作名為 `WordCount` 的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="bf925-118">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="bf925-119">此方法會用於指定為第一個方法參數的 <xref:System.String> 類別。</span><span class="sxs-lookup"><span data-stu-id="bf925-119">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="bf925-120">`CustomExtensions` 命名空間會匯入應用程式命名空間，並在 `Main` 方法內呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="bf925-120">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-security"></a><span data-ttu-id="bf925-121">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="bf925-121">.NET Security</span></span>  

 <span data-ttu-id="bf925-122">擴充方法沒有特定安全性弱點。</span><span class="sxs-lookup"><span data-stu-id="bf925-122">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="bf925-123">它們無法用於模擬類型上的現有方法，因為所有名稱衝突已使用類型自行定義的執行個體或靜態方法解決。</span><span class="sxs-lookup"><span data-stu-id="bf925-123">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="bf925-124">擴充方法無法存取擴充類別中的任何私用資料。</span><span class="sxs-lookup"><span data-stu-id="bf925-124">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf925-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="bf925-125">See also</span></span>

- [<span data-ttu-id="bf925-126">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bf925-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bf925-127">擴充方法</span><span class="sxs-lookup"><span data-stu-id="bf925-127">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="bf925-128">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="bf925-128">LINQ (Language-Integrated Query)</span></span>](../../linq/linq-in-csharp.md)
- [<span data-ttu-id="bf925-129">靜態類別和靜態類別成員</span><span class="sxs-lookup"><span data-stu-id="bf925-129">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="bf925-130">protected</span><span class="sxs-lookup"><span data-stu-id="bf925-130">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="bf925-131">internal</span><span class="sxs-lookup"><span data-stu-id="bf925-131">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="bf925-132">public</span><span class="sxs-lookup"><span data-stu-id="bf925-132">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="bf925-133">this</span><span class="sxs-lookup"><span data-stu-id="bf925-133">this</span></span>](../../language-reference/keywords/this.md)
- [<span data-ttu-id="bf925-134">命名 空間</span><span class="sxs-lookup"><span data-stu-id="bf925-134">namespace</span></span>](../../language-reference/keywords/namespace.md)
