---
title: '如何測試參考相等 (身分識別) -c # 程式設計手冊'
description: 瞭解如何 (身分識別) 測試參考是否相等。 請參閱程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 148f37b37639061e84cefafc5f057e6e7b54563f
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899148"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a><span data-ttu-id="36a34-104">如何測試參考相等 (身分識別)  (c # 程式設計手冊) </span><span class="sxs-lookup"><span data-stu-id="36a34-104">How to test for reference equality (Identity) (C# Programming Guide)</span></span>

<span data-ttu-id="36a34-105">不必實作任何自訂邏輯，就能支援您類型中的參考相等比較。</span><span class="sxs-lookup"><span data-stu-id="36a34-105">You do not have to implement any custom logic to support reference equality comparisons in your types.</span></span> <span data-ttu-id="36a34-106">此功能是透過靜態 <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> 方法提供給所有類型。</span><span class="sxs-lookup"><span data-stu-id="36a34-106">This functionality is provided for all types by the static <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="36a34-107">下列範例示範如何判斷兩個變數是否具有「參考相等」，這表示它們會參考記憶體中的相同物件。</span><span class="sxs-lookup"><span data-stu-id="36a34-107">The following example shows how to determine whether two variables have *reference equality*, which means that they refer to the same object in memory.</span></span>  
  
 <span data-ttu-id="36a34-108">範例中同時顯示為何 <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> 一律對實值類型傳回 `false`，以及為何不應使用 <xref:System.Object.ReferenceEquals%2A> 來判斷字串是否相等。</span><span class="sxs-lookup"><span data-stu-id="36a34-108">The example also shows why <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> always returns `false` for value types and why you should not use  <xref:System.Object.ReferenceEquals%2A> to determine string equality.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36a34-109">範例</span><span class="sxs-lookup"><span data-stu-id="36a34-109">Example</span></span>  

 [!code-csharp[TestingReferenceEquality](snippets/how-to-test-for-reference-equality-identity/Program.cs)]  
  
 <span data-ttu-id="36a34-110">實作 <xref:System.Object?displayProperty=nameWithType> 通用基底類別中的 `Equals` 也會執行參考相等檢查，但最好不要使用此功能，原因是如果類別恰好覆寫方法，結果可能不如預期。</span><span class="sxs-lookup"><span data-stu-id="36a34-110">The implementation of `Equals` in the <xref:System.Object?displayProperty=nameWithType> universal base class also performs a reference equality check, but it is best not to use this because, if a class happens to override the method, the results might not be what you expect.</span></span> <span data-ttu-id="36a34-111">`==` 和 `!=` 運算子也同樣如此。</span><span class="sxs-lookup"><span data-stu-id="36a34-111">The same is true for the `==` and `!=` operators.</span></span> <span data-ttu-id="36a34-112">當它們對參考型別進行操作時，`==` 和 `!=` 的預設行為是執行參考相等檢查。</span><span class="sxs-lookup"><span data-stu-id="36a34-112">When they are operating on reference types, the default behavior of `==` and `!=` is to perform a reference equality check.</span></span> <span data-ttu-id="36a34-113">然而，衍生的類別可以多載運算子，以執行值相等檢查。</span><span class="sxs-lookup"><span data-stu-id="36a34-113">However, derived classes can overload the operator to perform a value equality check.</span></span> <span data-ttu-id="36a34-114">為了將錯誤的可能性降到最低，建議您在需要判斷兩個物件是否具有參考相等時，最好一律使用 <xref:System.Object.ReferenceEquals%2A>。</span><span class="sxs-lookup"><span data-stu-id="36a34-114">To minimize the potential for error, it is best to always use <xref:System.Object.ReferenceEquals%2A> when you have to determine whether two objects have reference equality.</span></span>  
  
 <span data-ttu-id="36a34-115">相同的組件中的常數字串一律由執行階段暫留。</span><span class="sxs-lookup"><span data-stu-id="36a34-115">Constant strings within the same assembly are always interned by the runtime.</span></span> <span data-ttu-id="36a34-116">也就是說，會維護每個唯一的常值字串只有一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="36a34-116">That is, only one instance of each unique literal string is maintained.</span></span> <span data-ttu-id="36a34-117">不過，執行階段不保證暫留在執行階段建立的字串，也不保證暫留在不同組件中的兩個相等常數字串。</span><span class="sxs-lookup"><span data-stu-id="36a34-117">However, the runtime does not guarantee that strings created at runtime are interned, nor does it guarantee that two equal constant strings in different assemblies are interned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36a34-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36a34-118">See also</span></span>

- [<span data-ttu-id="36a34-119">相等比較</span><span class="sxs-lookup"><span data-stu-id="36a34-119">Equality Comparisons</span></span>](./equality-comparisons.md)
