---
title: 如何：使用物件初始設定式宣告物件
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: cf4954059a4b0bf015bed82a74357ecfd5f5987e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404871"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a><span data-ttu-id="3ae1a-102">如何：使用物件初始設定式宣告物件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ae1a-102">How to: Declare an Object by Using an Object Initializer (Visual Basic)</span></span>
<span data-ttu-id="3ae1a-103">物件初始化運算式可讓您在單一語句中宣告及具現化類別的實例。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-103">Object initializers enable you to declare and instantiate an instance of a class in a single statement.</span></span> <span data-ttu-id="3ae1a-104">此外，您可以同時初始化實例的一個或多個成員，而不叫用參數化的函式。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-104">In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.</span></span>  
  
 <span data-ttu-id="3ae1a-105">當您使用物件初始化運算式建立命名類型的實例時，會呼叫類別的無參數的函式，然後依照您指定的順序初始化指定的成員。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-105">When you use an object initializer to create an instance of a named type, the parameterless constructor for the class is called, followed by initialization of designated members in the order you specify.</span></span>  
  
 <span data-ttu-id="3ae1a-106">下列程式說明如何使用 `Student` 三種不同的方式來建立類別的實例。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-106">The following procedure shows how to create an instance of a `Student` class in three different ways.</span></span> <span data-ttu-id="3ae1a-107">類別具有 [名字]、[姓氏] 和 [class year] 屬性等等。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-107">The class has first name, last name, and class year properties, among others.</span></span> <span data-ttu-id="3ae1a-108">這三個宣告中的每一個都會建立新的實例 `Student` ，並將屬性 `First` 設定為 "Michael"、 `Last` 將屬性設定為 "Tucker"，並將所有其他成員設定為其預設值。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-108">Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values.</span></span> <span data-ttu-id="3ae1a-109">程式中每個宣告的結果相當於下列範例，這不會使用物件初始化運算式。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-109">The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.</span></span>  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 <span data-ttu-id="3ae1a-110">如需類別的執行 `Student` 方式，請參閱[如何：建立專案清單](../../concepts/linq/how-to-create-a-list-of-items.md)。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-110">For an implementation of the `Student` class, see [How to: Create a List of Items](../../concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="3ae1a-111">您可以從該主題複製程式碼來設定類別，並建立 `Student` 要使用的物件清單。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-111">You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.</span></span>  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a><span data-ttu-id="3ae1a-112">若要使用物件初始化運算式建立已命名類別的物件</span><span class="sxs-lookup"><span data-stu-id="3ae1a-112">To create an object of a named class by using an object initializer</span></span>  
  
1. <span data-ttu-id="3ae1a-113">開始宣告，就像您計畫使用的是一個函數。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-113">Begin the declaration as if you planned to use a constructor.</span></span>  
  
     `Dim student1 As New Student`  
  
2. <span data-ttu-id="3ae1a-114">輸入關鍵字 `With` ，後面接著以大括弧括住的初始化清單。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-114">Type the keyword `With`, followed by an initialization list in braces.</span></span>  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. <span data-ttu-id="3ae1a-115">在初始化清單中，包含您要初始化的每個屬性，並為其指派初始值。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-115">In the initialization list, include each property that you want to initialize and assign an initial value to it.</span></span> <span data-ttu-id="3ae1a-116">屬性的名稱前面會加上句點。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-116">The name of the property is preceded by a period.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     <span data-ttu-id="3ae1a-117">您可以初始化類別的一個或多個成員。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-117">You can initialize one or more members of the class.</span></span>  
  
4. <span data-ttu-id="3ae1a-118">或者，您可以宣告類別的新實例，然後為它指派值。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-118">Alternatively, you can declare a new instance of the class and then assign a value to it.</span></span> <span data-ttu-id="3ae1a-119">首先，宣告的實例 `Student` ：</span><span class="sxs-lookup"><span data-stu-id="3ae1a-119">First, declare an instance of `Student`:</span></span>  
  
     `Dim student2 As Student`  
  
5. <span data-ttu-id="3ae1a-120">以一般方式開始建立的實例 `Student` 。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-120">Begin the creation of an instance of `Student` in the normal way.</span></span>  
  
     `Dim student2 As Student = New Student`  
  
6. <span data-ttu-id="3ae1a-121">輸入 `With` ，然後按物件初始化運算式，將新實例的一個或多個成員初始化。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-121">Type `With` and then an object initializer to initialize one or more members of the new instance.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. <span data-ttu-id="3ae1a-122">您可以藉由省略來簡化上一個步驟中的定義 `As Student` 。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-122">You can simplify the definition in the previous step by omitting `As Student`.</span></span> <span data-ttu-id="3ae1a-123">如果您這樣做，編譯器 `student3` 會 `Student` 使用區欄位型別推斷來判斷是的實例。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-123">If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.</span></span>  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     <span data-ttu-id="3ae1a-124">如需詳細資訊，請參閱[區欄位型別推斷](../variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="3ae1a-124">For more information, see [Local Type Inference](../variables/local-type-inference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae1a-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ae1a-125">See also</span></span>

- [<span data-ttu-id="3ae1a-126">區域型別推斷</span><span class="sxs-lookup"><span data-stu-id="3ae1a-126">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="3ae1a-127">作法：建立項目清單</span><span class="sxs-lookup"><span data-stu-id="3ae1a-127">How to: Create a List of Items</span></span>](../../concepts/linq/how-to-create-a-list-of-items.md)
- [<span data-ttu-id="3ae1a-128">物件初始設定式：具名和匿名型別</span><span class="sxs-lookup"><span data-stu-id="3ae1a-128">Object Initializers: Named and Anonymous Types</span></span>](object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="3ae1a-129">匿名類型</span><span class="sxs-lookup"><span data-stu-id="3ae1a-129">Anonymous Types</span></span>](anonymous-types.md)
