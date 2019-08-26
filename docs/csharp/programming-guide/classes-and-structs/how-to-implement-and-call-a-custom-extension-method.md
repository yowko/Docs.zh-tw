---
title: 作法：實作和呼叫自訂擴充方法 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 26ad1d2251388237e186d1ba0e885fd7def66467
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596876"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="04fe4-102">作法：實作和呼叫自訂擴充方法 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="04fe4-102">How to: Implement and Call a Custom Extension Method (C# Programming Guide)</span></span>
<span data-ttu-id="04fe4-103">本主題示範如何針對任何 .NET 類型實作您自己的延伸模組方法。</span><span class="sxs-lookup"><span data-stu-id="04fe4-103">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="04fe4-104">用戶端程式碼可以使用您的擴充方法，方法是將參考新增至包含這些方法的 DLL，然後新增 [using](../../language-reference/keywords/using-directive.md) 指示詞，以指定會在其中定義擴充方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="04fe4-104">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="04fe4-105">定義和呼叫擴充方法</span><span class="sxs-lookup"><span data-stu-id="04fe4-105">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="04fe4-106">定義靜態[類別](./static-classes-and-static-class-members.md)以包含擴充方法。</span><span class="sxs-lookup"><span data-stu-id="04fe4-106">Define a static [class](./static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="04fe4-107">此類別對用戶端程式碼而言必須是可見的。</span><span class="sxs-lookup"><span data-stu-id="04fe4-107">The class must be visible to client code.</span></span> <span data-ttu-id="04fe4-108">如需存取範圍規則的詳細資訊，請參閱[存取修飾詞](./access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="04fe4-108">For more information about accessibility rules, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="04fe4-109">將擴充方法實作為其可見度至少等同於包含類別的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="04fe4-109">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="04fe4-110">方法的第一個參數會指定方法的作業類型，前面必須加上 [this](../../language-reference/keywords/this.md) 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="04fe4-110">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="04fe4-111">在呼叫程式碼中，新增 `using` 指示詞以指定包含擴充方法類別的[命名空間](../../language-reference/keywords/namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="04fe4-111">In the calling code, add a `using` directive to specify the [namespace](../../language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="04fe4-112">將方法當做是類型上的執行個體方法進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="04fe4-112">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="04fe4-113">請注意，呼叫程式碼未指定第一個參數，因為它代表要套用運算子的類型，而且編譯器已知物件類型。</span><span class="sxs-lookup"><span data-stu-id="04fe4-113">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="04fe4-114">您只需要針對參數 2 到 `n` 提供引數。</span><span class="sxs-lookup"><span data-stu-id="04fe4-114">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04fe4-115">範例</span><span class="sxs-lookup"><span data-stu-id="04fe4-115">Example</span></span>  
 <span data-ttu-id="04fe4-116">下列範例會在 `CustomExtensions.StringExtension` 類別中實作名為 `WordCount` 的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="04fe4-116">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="04fe4-117">此方法會用於指定為第一個方法參數的 <xref:System.String> 類別。</span><span class="sxs-lookup"><span data-stu-id="04fe4-117">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="04fe4-118">`CustomExtensions` 命名空間會匯入應用程式命名空間，並在 `Main` 方法內呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="04fe4-118">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="04fe4-119">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="04fe4-119">.NET Framework Security</span></span>  
 <span data-ttu-id="04fe4-120">擴充方法沒有特定安全性弱點。</span><span class="sxs-lookup"><span data-stu-id="04fe4-120">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="04fe4-121">它們無法用於模擬類型上的現有方法，因為所有名稱衝突已使用類型自行定義的執行個體或靜態方法解決。</span><span class="sxs-lookup"><span data-stu-id="04fe4-121">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="04fe4-122">擴充方法無法存取擴充類別中的任何私用資料。</span><span class="sxs-lookup"><span data-stu-id="04fe4-122">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04fe4-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04fe4-123">See also</span></span>

- [<span data-ttu-id="04fe4-124">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="04fe4-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="04fe4-125">擴充方法</span><span class="sxs-lookup"><span data-stu-id="04fe4-125">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="04fe4-126">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="04fe4-126">LINQ (Language-Integrated Query)</span></span>](../../linq/linq-in-csharp.md)
- [<span data-ttu-id="04fe4-127">靜態類別和靜態類別成員</span><span class="sxs-lookup"><span data-stu-id="04fe4-127">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="04fe4-128">protected</span><span class="sxs-lookup"><span data-stu-id="04fe4-128">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="04fe4-129">internal</span><span class="sxs-lookup"><span data-stu-id="04fe4-129">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="04fe4-130">public</span><span class="sxs-lookup"><span data-stu-id="04fe4-130">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="04fe4-131">this</span><span class="sxs-lookup"><span data-stu-id="04fe4-131">this</span></span>](../../language-reference/keywords/this.md)
- [<span data-ttu-id="04fe4-132">namespace</span><span class="sxs-lookup"><span data-stu-id="04fe4-132">namespace</span></span>](../../language-reference/keywords/namespace.md)
