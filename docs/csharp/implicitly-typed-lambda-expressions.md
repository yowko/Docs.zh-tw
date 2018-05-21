---
title: 隱含型別 Lambda 運算式
description: 了解您為何無法使用隱含型別變數宣告來宣告 Lambda 運算式。
ms.date: 06/20/2016
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: f06c55f51c30c941d6d507ac8e2edd95c5152742
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="8e6c3-103">隱含型別 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="8e6c3-103">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="8e6c3-104">我將不會使用 `var` 來宣告此運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="8e6c3-104">I'm not using `var` to declare this expression tree.</span></span> <span data-ttu-id="8e6c3-105">您無法使用隱含型別變數宣告來宣告 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="8e6c3-105">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="8e6c3-106">它會導致編譯器發生循環邏輯問題。</span><span class="sxs-lookup"><span data-stu-id="8e6c3-106">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="8e6c3-107">`var` 宣告會告知編譯器從指派運算子右邊的運算式類型中，查明變數的類型。</span><span class="sxs-lookup"><span data-stu-id="8e6c3-107">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="8e6c3-108">Lambda 運算式沒有編譯時期類型，但可轉換成任何相符的委派或運算式類型。</span><span class="sxs-lookup"><span data-stu-id="8e6c3-108">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="8e6c3-109">當您將 Lambda 運算式指派給委派或運算式類型的變數時，也就是告知編譯器嘗試將 Lambda 運算式轉換成符合 [指派給] 變數簽章的運算式或委派。</span><span class="sxs-lookup"><span data-stu-id="8e6c3-109">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="8e6c3-110">編譯器必須嘗試使指派右邊的項目符合指派左邊的類型。</span><span class="sxs-lookup"><span data-stu-id="8e6c3-110">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span> 

<span data-ttu-id="8e6c3-111">指派兩邊都無法告知編譯器檢視指派運算子另一邊的物件，並查看我的類型是否相符。</span><span class="sxs-lookup"><span data-stu-id="8e6c3-111">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="8e6c3-112">您可以閱讀[這篇文章](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF 下載)，以取得更多有關 C# 語言為什麼會指定該行為的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="8e6c3-112">You can get even more details on why the C# language specifies that behavior by reading [this article](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF Download)</span></span>


