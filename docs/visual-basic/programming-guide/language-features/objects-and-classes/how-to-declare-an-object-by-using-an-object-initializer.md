---
title: 如何：使用物件初始設定式宣告物件
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: ae04d338b61027c3917ad3a7f62ff40f0a95e53e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347129"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a><span data-ttu-id="707fc-102">如何：使用物件初始設定式宣告物件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="707fc-102">How to: Declare an Object by Using an Object Initializer (Visual Basic)</span></span>
<span data-ttu-id="707fc-103">物件初始化運算式可讓您在單一語句中宣告及具現化類別的實例。</span><span class="sxs-lookup"><span data-stu-id="707fc-103">Object initializers enable you to declare and instantiate an instance of a class in a single statement.</span></span> <span data-ttu-id="707fc-104">此外，您可以同時初始化實例的一個或多個成員，而不叫用參數化的函式。</span><span class="sxs-lookup"><span data-stu-id="707fc-104">In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.</span></span>  
  
 <span data-ttu-id="707fc-105">當您使用物件初始化運算式建立命名類型的實例時，會呼叫類別的無參數的函式，然後依照您指定的順序初始化指定的成員。</span><span class="sxs-lookup"><span data-stu-id="707fc-105">When you use an object initializer to create an instance of a named type, the parameterless constructor for the class is called, followed by initialization of designated members in the order you specify.</span></span>  
  
 <span data-ttu-id="707fc-106">下列程式顯示如何以三種不同的方式建立 `Student` 類別的實例。</span><span class="sxs-lookup"><span data-stu-id="707fc-106">The following procedure shows how to create an instance of a `Student` class in three different ways.</span></span> <span data-ttu-id="707fc-107">類別具有 [名字]、[姓氏] 和 [class year] 屬性等等。</span><span class="sxs-lookup"><span data-stu-id="707fc-107">The class has first name, last name, and class year properties, among others.</span></span> <span data-ttu-id="707fc-108">這三個宣告都會建立 `Student`的新實例，且屬性 `First` 設定為 "Michael"、屬性 `Last` 設定為 "Tucker"，而所有其他成員設定為預設值。</span><span class="sxs-lookup"><span data-stu-id="707fc-108">Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values.</span></span> <span data-ttu-id="707fc-109">程式中每個宣告的結果相當於下列範例，這不會使用物件初始化運算式。</span><span class="sxs-lookup"><span data-stu-id="707fc-109">The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 <span data-ttu-id="707fc-110">如需 `Student` 類別的執行方式，請參閱[如何：建立專案清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)。</span><span class="sxs-lookup"><span data-stu-id="707fc-110">For an implementation of the `Student` class, see [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="707fc-111">您可以從該主題複製程式碼來設定類別，並建立要使用的 `Student` 物件清單。</span><span class="sxs-lookup"><span data-stu-id="707fc-111">You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.</span></span>  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a><span data-ttu-id="707fc-112">若要使用物件初始化運算式建立已命名類別的物件</span><span class="sxs-lookup"><span data-stu-id="707fc-112">To create an object of a named class by using an object initializer</span></span>  
  
1. <span data-ttu-id="707fc-113">開始宣告，就像您計畫使用的是一個函數。</span><span class="sxs-lookup"><span data-stu-id="707fc-113">Begin the declaration as if you planned to use a constructor.</span></span>  
  
     `Dim student1 As New Student`  
  
2. <span data-ttu-id="707fc-114">輸入關鍵字 `With`，後面接著以大括弧括住的初始化清單。</span><span class="sxs-lookup"><span data-stu-id="707fc-114">Type the keyword `With`, followed by an initialization list in braces.</span></span>  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. <span data-ttu-id="707fc-115">在初始化清單中，包含您要初始化的每個屬性，並為其指派初始值。</span><span class="sxs-lookup"><span data-stu-id="707fc-115">In the initialization list, include each property that you want to initialize and assign an initial value to it.</span></span> <span data-ttu-id="707fc-116">屬性的名稱前面會加上句點。</span><span class="sxs-lookup"><span data-stu-id="707fc-116">The name of the property is preceded by a period.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     <span data-ttu-id="707fc-117">您可以初始化類別的一個或多個成員。</span><span class="sxs-lookup"><span data-stu-id="707fc-117">You can initialize one or more members of the class.</span></span>  
  
4. <span data-ttu-id="707fc-118">或者，您可以宣告類別的新實例，然後為它指派值。</span><span class="sxs-lookup"><span data-stu-id="707fc-118">Alternatively, you can declare a new instance of the class and then assign a value to it.</span></span> <span data-ttu-id="707fc-119">首先，宣告 `Student`的實例：</span><span class="sxs-lookup"><span data-stu-id="707fc-119">First, declare an instance of `Student`:</span></span>  
  
     `Dim student2 As Student`  
  
5. <span data-ttu-id="707fc-120">開始以一般方式建立 `Student` 實例。</span><span class="sxs-lookup"><span data-stu-id="707fc-120">Begin the creation of an instance of `Student` in the normal way.</span></span>  
  
     `Dim student2 As Student = New Student`  
  
6. <span data-ttu-id="707fc-121">輸入 `With`，然後按物件初始化運算式，將新實例的一個或多個成員初始化。</span><span class="sxs-lookup"><span data-stu-id="707fc-121">Type `With` and then an object initializer to initialize one or more members of the new instance.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. <span data-ttu-id="707fc-122">您可以藉由省略 `As Student`，來簡化上一個步驟中的定義。</span><span class="sxs-lookup"><span data-stu-id="707fc-122">You can simplify the definition in the previous step by omitting `As Student`.</span></span> <span data-ttu-id="707fc-123">如果您這樣做，編譯器會使用區欄位型別推斷來判斷 `student3` 是 `Student` 的實例。</span><span class="sxs-lookup"><span data-stu-id="707fc-123">If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     <span data-ttu-id="707fc-124">如需詳細資訊，請參閱[區欄位型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="707fc-124">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="707fc-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="707fc-125">See also</span></span>

- [<span data-ttu-id="707fc-126">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="707fc-126">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="707fc-127">如何：建立項目清單</span><span class="sxs-lookup"><span data-stu-id="707fc-127">How to: Create a List of Items</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [<span data-ttu-id="707fc-128">物件初始設定式：具名和匿名類型</span><span class="sxs-lookup"><span data-stu-id="707fc-128">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="707fc-129">匿名類型</span><span class="sxs-lookup"><span data-stu-id="707fc-129">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
