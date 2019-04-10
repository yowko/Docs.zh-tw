---
title: HOW TO：宣告結構 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: a52daddaa8701ccca9bd9b5b4a48535a6ffa19ed
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343554"
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="65b28-102">HOW TO：宣告結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65b28-102">How to: Declare a Structure (Visual Basic)</span></span>
<span data-ttu-id="65b28-103">開始使用在 structure 宣告[Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)，然後您使用`End Structure`陳述式。</span><span class="sxs-lookup"><span data-stu-id="65b28-103">You begin a structure declaration with the [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md), and you end it with the `End Structure` statement.</span></span> <span data-ttu-id="65b28-104">這兩個陳述式之間必須宣告至少一個*項目*。</span><span class="sxs-lookup"><span data-stu-id="65b28-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="65b28-105">項目可以是任何資料類型，但至少一個必須為非共用的變數或非共用、 非自訂的事件。</span><span class="sxs-lookup"><span data-stu-id="65b28-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="65b28-106">您無法初始化任何在結構宣告中的結構項目。</span><span class="sxs-lookup"><span data-stu-id="65b28-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="65b28-107">當您宣告結構類型的變數時，您將值指派至項目透過變數來存取它們。</span><span class="sxs-lookup"><span data-stu-id="65b28-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="65b28-108">如需結構和類別之間的差異的討論，請參閱 <<c0> [ 結構和類別](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="65b28-108">For a discussion of the differences between structures and classes, see [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="65b28-109">基於示範目的，假設您想要用來追蹤員工的名稱、 電話分機號碼和薪資。</span><span class="sxs-lookup"><span data-stu-id="65b28-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="65b28-110">一種結構可讓您在單一變數中。</span><span class="sxs-lookup"><span data-stu-id="65b28-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="65b28-111">若要宣告結構</span><span class="sxs-lookup"><span data-stu-id="65b28-111">To declare a structure</span></span>  
  
1. <span data-ttu-id="65b28-112">建立的開始和結束陳述式中的結構。</span><span class="sxs-lookup"><span data-stu-id="65b28-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="65b28-113">您可以指定的結構，使用的存取層級[公開金鑰](../../../../visual-basic/language-reference/modifiers/public.md)，[受保護](../../../../visual-basic/language-reference/modifiers/protected.md)， [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)，或[私人](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字，或者您可以讓它預設為`Public`。</span><span class="sxs-lookup"><span data-stu-id="65b28-113">You can specify the access level of a structure using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2. <span data-ttu-id="65b28-114">加入結構主體中的項目。</span><span class="sxs-lookup"><span data-stu-id="65b28-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="65b28-115">結構必須有至少一個項目。</span><span class="sxs-lookup"><span data-stu-id="65b28-115">A structure must have at least one element.</span></span> <span data-ttu-id="65b28-116">您必須宣告每個項目，並為其指定存取層級。</span><span class="sxs-lookup"><span data-stu-id="65b28-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="65b28-117">如果您使用[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)而不需要任何關鍵字，可存取性，預設值為`Public`。</span><span class="sxs-lookup"><span data-stu-id="65b28-117">If you use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
    ```  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     <span data-ttu-id="65b28-118">`salary`在上述範例中的欄位是`Private`，這表示它是外部結構，甚至是從包含的類別無法存取。</span><span class="sxs-lookup"><span data-stu-id="65b28-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="65b28-119">不過，`giveRaise`程序是`Public`，因此它可以從外部呼叫結構。</span><span class="sxs-lookup"><span data-stu-id="65b28-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="65b28-120">同樣地，您可以提高`salaryReviewTime`結構之外的事件。</span><span class="sxs-lookup"><span data-stu-id="65b28-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="65b28-121">變數，除了`Sub`程序和事件，您也可以定義常數，`Function`程序和在結構中的屬性。</span><span class="sxs-lookup"><span data-stu-id="65b28-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="65b28-122">您可以指定最多一個屬性為*屬性預設*，前提是需要至少一個引數。</span><span class="sxs-lookup"><span data-stu-id="65b28-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="65b28-123">您可以處理的事件[Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub`程序。</span><span class="sxs-lookup"><span data-stu-id="65b28-123">You can handle an event with a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="65b28-124">如需詳細資訊，請參閱[如何：宣告，並在 Visual Basic 中呼叫預設屬性](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)。</span><span class="sxs-lookup"><span data-stu-id="65b28-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65b28-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65b28-125">See also</span></span>

- [<span data-ttu-id="65b28-126">資料類型</span><span class="sxs-lookup"><span data-stu-id="65b28-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="65b28-127">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="65b28-127">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="65b28-128">複合資料類型</span><span class="sxs-lookup"><span data-stu-id="65b28-128">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="65b28-129">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="65b28-129">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="65b28-130">結構</span><span class="sxs-lookup"><span data-stu-id="65b28-130">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="65b28-131">資料類型疑難排解</span><span class="sxs-lookup"><span data-stu-id="65b28-131">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="65b28-132">結構變數</span><span class="sxs-lookup"><span data-stu-id="65b28-132">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [<span data-ttu-id="65b28-133">結構和其他程式設計項目</span><span class="sxs-lookup"><span data-stu-id="65b28-133">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [<span data-ttu-id="65b28-134">結構和類別</span><span class="sxs-lookup"><span data-stu-id="65b28-134">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="65b28-135">使用者定義資料類型</span><span class="sxs-lookup"><span data-stu-id="65b28-135">User-Defined Data Type</span></span>](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
