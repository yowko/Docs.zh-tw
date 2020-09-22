---
title: '&amp; 運算子'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: 20c2e2088691e68221872cc1dfc5486413515a4d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867156"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="320dd-102">&amp; 運算子 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="320dd-102">&amp; Operator (Visual Basic)</span></span>

<span data-ttu-id="320dd-103">產生兩個運算式的字串串連。</span><span class="sxs-lookup"><span data-stu-id="320dd-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="320dd-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="320dd-104">Syntax</span></span>  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="320dd-105">組件</span><span class="sxs-lookup"><span data-stu-id="320dd-105">Parts</span></span>  

 `result`  
 <span data-ttu-id="320dd-106">必要。</span><span class="sxs-lookup"><span data-stu-id="320dd-106">Required.</span></span> <span data-ttu-id="320dd-107">任何 `String` 或 `Object` 變數。</span><span class="sxs-lookup"><span data-stu-id="320dd-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="320dd-108">必要。</span><span class="sxs-lookup"><span data-stu-id="320dd-108">Required.</span></span> <span data-ttu-id="320dd-109">具有擴展至之資料類型的任何運算式 `String` 。</span><span class="sxs-lookup"><span data-stu-id="320dd-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="320dd-110">必要。</span><span class="sxs-lookup"><span data-stu-id="320dd-110">Required.</span></span> <span data-ttu-id="320dd-111">具有擴展至之資料類型的任何運算式 `String` 。</span><span class="sxs-lookup"><span data-stu-id="320dd-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="320dd-112">備註</span><span class="sxs-lookup"><span data-stu-id="320dd-112">Remarks</span></span>  

 <span data-ttu-id="320dd-113">如果或的資料類型 `expression1` `expression2` 不是 `String` 擴展至，則 `String` 會轉換成 `String` 。</span><span class="sxs-lookup"><span data-stu-id="320dd-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="320dd-114">如果其中一種資料類型不會擴展至 `String` ，則編譯器會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="320dd-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="320dd-115">的資料類型 `result` 為 `String` 。</span><span class="sxs-lookup"><span data-stu-id="320dd-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="320dd-116">如果其中一或兩個運算式評估為 [Nothing](../nothing.md) 或值為 <xref:System.DBNull.Value?displayProperty=nameWithType> ，則會將它們視為字串，其值為 ""。</span><span class="sxs-lookup"><span data-stu-id="320dd-116">If one or both expressions evaluate to [Nothing](../nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="320dd-117">可以多載 `&` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="320dd-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="320dd-118">如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="320dd-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="320dd-119">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="320dd-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="320dd-120">連字號 ( # A0) 字元也可以用來將變數識別為類型 `Long` 。</span><span class="sxs-lookup"><span data-stu-id="320dd-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="320dd-121">如需詳細資訊，請參閱 [類型字元](../../programming-guide/language-features/data-types/type-characters.md)。</span><span class="sxs-lookup"><span data-stu-id="320dd-121">For more information, see [Type Characters](../../programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="320dd-122">範例</span><span class="sxs-lookup"><span data-stu-id="320dd-122">Example</span></span>  

 <span data-ttu-id="320dd-123">這個範例會使用 `&` 運算子來強制執行字串串連。</span><span class="sxs-lookup"><span data-stu-id="320dd-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="320dd-124">結果是字串值，表示兩個字串運算元的串連。</span><span class="sxs-lookup"><span data-stu-id="320dd-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="320dd-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="320dd-125">See also</span></span>

- [<span data-ttu-id="320dd-126">&= 運算子</span><span class="sxs-lookup"><span data-stu-id="320dd-126">&= Operator</span></span>](and-assignment-operator.md)
- [<span data-ttu-id="320dd-127">串連運算子</span><span class="sxs-lookup"><span data-stu-id="320dd-127">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="320dd-128">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="320dd-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="320dd-129">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="320dd-129">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="320dd-130">Visual Basic 中的串連運算子</span><span class="sxs-lookup"><span data-stu-id="320dd-130">Concatenation Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
