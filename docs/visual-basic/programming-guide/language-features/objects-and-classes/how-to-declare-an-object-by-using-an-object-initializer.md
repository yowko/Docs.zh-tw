---
title: 如何：使用物件初始設定式宣告物件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: 3a372ba91377b53c87c05976e416ca8ed55ccbbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649161"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a><span data-ttu-id="0d704-102">如何：使用物件初始設定式宣告物件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d704-102">How to: Declare an Object by Using an Object Initializer (Visual Basic)</span></span>
<span data-ttu-id="0d704-103">物件初始設定式可讓您宣告並具現化類別，以在單一陳述式的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d704-103">Object initializers enable you to declare and instantiate an instance of a class in a single statement.</span></span> <span data-ttu-id="0d704-104">此外，您可以在相同的時間初始化執行個體的一或多個的成員，而不叫用的參數化建構函式。</span><span class="sxs-lookup"><span data-stu-id="0d704-104">In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.</span></span>  
  
 <span data-ttu-id="0d704-105">當您使用物件初始設定式來建立具名型別的執行個體時，會呼叫類別的預設建構函式，後面接著初始化指定的成員，您所指定的順序。</span><span class="sxs-lookup"><span data-stu-id="0d704-105">When you use an object initializer to create an instance of a named type, the default constructor for the class is called, followed by initialization of designated members in the order you specify.</span></span>  
  
 <span data-ttu-id="0d704-106">下列程序示範如何建立執行個體`Student`三種不同方式的類別。</span><span class="sxs-lookup"><span data-stu-id="0d704-106">The following procedure shows how to create an instance of a `Student` class in three different ways.</span></span> <span data-ttu-id="0d704-107">類別有名字、 姓氏和年級屬性和其他項目。</span><span class="sxs-lookup"><span data-stu-id="0d704-107">The class has first name, last name, and class year properties, among others.</span></span> <span data-ttu-id="0d704-108">每三個宣告建立的新執行個體`Student`，與屬性`First`設為"Michael，"屬性`Last`設定為"Tucker"，而所有其他成員設定為其預設值。</span><span class="sxs-lookup"><span data-stu-id="0d704-108">Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values.</span></span> <span data-ttu-id="0d704-109">程序中的每個宣告的結果就相當於下列的範例中，不會使用物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="0d704-109">The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#20](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_1.vb)]  
  
 <span data-ttu-id="0d704-110">實作`Student`類別，請參閱[How to： 建立項目的清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)。</span><span class="sxs-lookup"><span data-stu-id="0d704-110">For an implementation of the `Student` class, see [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="0d704-111">您可以從設定的類別，並建立一份該主題複製程式碼`Student`若要使用的物件。</span><span class="sxs-lookup"><span data-stu-id="0d704-111">You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.</span></span>  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a><span data-ttu-id="0d704-112">若要使用物件初始設定式建立具名類別的物件</span><span class="sxs-lookup"><span data-stu-id="0d704-112">To create an object of a named class by using an object initializer</span></span>  
  
1.  <span data-ttu-id="0d704-113">開始宣告，如同您計劃使用建構函式。</span><span class="sxs-lookup"><span data-stu-id="0d704-113">Begin the declaration as if you planned to use a constructor.</span></span>  
  
     `Dim student1 As New Student`  
  
2.  <span data-ttu-id="0d704-114">輸入關鍵字`With`，後面接著括號括住的初始設定清單。</span><span class="sxs-lookup"><span data-stu-id="0d704-114">Type the keyword `With`, followed by an initialization list in braces.</span></span>  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  <span data-ttu-id="0d704-115">在初始設定清單中，包含您想要初始化，並將初始值指派給它的每一個屬性。</span><span class="sxs-lookup"><span data-stu-id="0d704-115">In the initialization list, include each property that you want to initialize and assign an initial value to it.</span></span> <span data-ttu-id="0d704-116">屬性名稱前面有一個句號。</span><span class="sxs-lookup"><span data-stu-id="0d704-116">The name of the property is preceded by a period.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#21](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_2.vb)]  
  
     <span data-ttu-id="0d704-117">您可以初始化類別的一個或多個成員。</span><span class="sxs-lookup"><span data-stu-id="0d704-117">You can initialize one or more members of the class.</span></span>  
  
4.  <span data-ttu-id="0d704-118">或者，您可以宣告類別的新執行個體，然後再將值指派給它。</span><span class="sxs-lookup"><span data-stu-id="0d704-118">Alternatively, you can declare a new instance of the class and then assign a value to it.</span></span> <span data-ttu-id="0d704-119">首先，宣告的執行個體`Student`:</span><span class="sxs-lookup"><span data-stu-id="0d704-119">First, declare an instance of `Student`:</span></span>  
  
     `Dim student2 As Student`  
  
5.  <span data-ttu-id="0d704-120">開始的執行個體建立`Student`以一般方式。</span><span class="sxs-lookup"><span data-stu-id="0d704-120">Begin the creation of an instance of `Student` in the normal way.</span></span>  
  
     `Dim student2 As Student = New Student`  
  
6.  <span data-ttu-id="0d704-121">型別`With`，然後物件初始設定式來初始化新執行個體的一或多個成員。</span><span class="sxs-lookup"><span data-stu-id="0d704-121">Type `With` and then an object initializer to initialize one or more members of the new instance.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#22](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_3.vb)]  
  
7.  <span data-ttu-id="0d704-122">您可以藉由略過簡化上一個步驟中的定義`As Student`。</span><span class="sxs-lookup"><span data-stu-id="0d704-122">You can simplify the definition in the previous step by omitting `As Student`.</span></span> <span data-ttu-id="0d704-123">如果您這樣做，在編譯器判斷`student3`的執行個體`Student`使用區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="0d704-123">If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#23](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_4.vb)]  
  
     <span data-ttu-id="0d704-124">如需詳細資訊，請參閱[區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="0d704-124">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d704-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d704-125">See Also</span></span>  
 [<span data-ttu-id="0d704-126">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="0d704-126">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="0d704-127">如何：建立項目清單</span><span class="sxs-lookup"><span data-stu-id="0d704-127">How to: Create a List of Items</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)  
 [<span data-ttu-id="0d704-128">物件初始設定式：具名和匿名類型</span><span class="sxs-lookup"><span data-stu-id="0d704-128">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="0d704-129">匿名類型</span><span class="sxs-lookup"><span data-stu-id="0d704-129">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
