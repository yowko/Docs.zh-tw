---
title: 作法：宣告結構
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: bffdc5974eff6b71e0abc4780a61aa300769eed6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058543"
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="e2a76-102">如何：宣告結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2a76-102">How to: Declare a Structure (Visual Basic)</span></span>

<span data-ttu-id="e2a76-103">您可以使用 [Structure 語句](../../../language-reference/statements/structure-statement.md)來開始結構宣告，然後使用語句來結束它 `End Structure` 。</span><span class="sxs-lookup"><span data-stu-id="e2a76-103">You begin a structure declaration with the [Structure Statement](../../../language-reference/statements/structure-statement.md), and you end it with the `End Structure` statement.</span></span> <span data-ttu-id="e2a76-104">在這兩個語句之間，您必須宣告至少一個 *元素*。</span><span class="sxs-lookup"><span data-stu-id="e2a76-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="e2a76-105">元素可以是任何資料類型，但至少一個必須是非共用變數或非共用的 noncustom 事件。</span><span class="sxs-lookup"><span data-stu-id="e2a76-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="e2a76-106">您無法初始化結構宣告中的任何結構元素。</span><span class="sxs-lookup"><span data-stu-id="e2a76-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="e2a76-107">當您將變數宣告為結構類型時，您可以透過變數存取它們，藉以指派值給專案。</span><span class="sxs-lookup"><span data-stu-id="e2a76-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="e2a76-108">如需結構和類別之間差異的討論，請參閱 [結構和類別](structures-and-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="e2a76-108">For a discussion of the differences between structures and classes, see [Structures and Classes](structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="e2a76-109">基於示範目的，請考慮您要追蹤員工姓名、電話分機和薪資的情況。</span><span class="sxs-lookup"><span data-stu-id="e2a76-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="e2a76-110">結構可讓您在單一變數中進行這項作業。</span><span class="sxs-lookup"><span data-stu-id="e2a76-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="e2a76-111">宣告結構</span><span class="sxs-lookup"><span data-stu-id="e2a76-111">To declare a structure</span></span>  
  
1. <span data-ttu-id="e2a76-112">建立結構的開頭和結尾語句。</span><span class="sxs-lookup"><span data-stu-id="e2a76-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="e2a76-113">您可以使用 [Public](../../../language-reference/modifiers/public.md)、 [Protected](../../../language-reference/modifiers/protected.md)、 [Friend](../../../language-reference/modifiers/friend.md)或 [Private](../../../language-reference/modifiers/private.md) 關鍵字來指定結構的存取層級，也可以讓它預設為 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="e2a76-113">You can specify the access level of a structure using the [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), or [Private](../../../language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. <span data-ttu-id="e2a76-114">將元素加入至結構的主體。</span><span class="sxs-lookup"><span data-stu-id="e2a76-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="e2a76-115">結構至少必須有一個元素。</span><span class="sxs-lookup"><span data-stu-id="e2a76-115">A structure must have at least one element.</span></span> <span data-ttu-id="e2a76-116">您必須宣告每個元素，並為其指定存取層級。</span><span class="sxs-lookup"><span data-stu-id="e2a76-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="e2a76-117">如果您在沒有任何關鍵字的情況下使用 [Dim 語句](../../../language-reference/statements/dim-statement.md) ，存取範圍預設為 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="e2a76-117">If you use the [Dim Statement](../../../language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
    ```vb  
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
  
     <span data-ttu-id="e2a76-118">`salary`上述範例中的欄位是 `Private` ，這表示它無法在結構外部存取，即使是從包含類別也一樣。</span><span class="sxs-lookup"><span data-stu-id="e2a76-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="e2a76-119">不過， `giveRaise` 程式是 `Public` ，因此可以從結構外部呼叫。</span><span class="sxs-lookup"><span data-stu-id="e2a76-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="e2a76-120">同樣地，您可以 `salaryReviewTime` 從結構外部引發事件。</span><span class="sxs-lookup"><span data-stu-id="e2a76-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="e2a76-121">除了變數、 `Sub` 程式和事件之外，您也可以 `Function` 在結構中定義常數、程式和屬性。</span><span class="sxs-lookup"><span data-stu-id="e2a76-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="e2a76-122">您可以指定最多一個屬性作為 *預設屬性*，前提是它至少需要一個引數。</span><span class="sxs-lookup"><span data-stu-id="e2a76-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="e2a76-123">您可以使用[共用](../../../language-reference/modifiers/shared.md)程式來處理事件 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="e2a76-123">You can handle an event with a [Shared](../../../language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="e2a76-124">如需詳細資訊，請參閱 [如何：在 Visual Basic 中宣告及呼叫預設屬性](../procedures/how-to-declare-and-call-a-default-property.md)。</span><span class="sxs-lookup"><span data-stu-id="e2a76-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2a76-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2a76-125">See also</span></span>

- [<span data-ttu-id="e2a76-126">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="e2a76-126">Data Types</span></span>](index.md)
- [<span data-ttu-id="e2a76-127">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="e2a76-127">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="e2a76-128">複合資料類型</span><span class="sxs-lookup"><span data-stu-id="e2a76-128">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="e2a76-129">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="e2a76-129">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="e2a76-130">結構</span><span class="sxs-lookup"><span data-stu-id="e2a76-130">Structures</span></span>](structures.md)
- [<span data-ttu-id="e2a76-131">疑難排解資料類型的問題</span><span class="sxs-lookup"><span data-stu-id="e2a76-131">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="e2a76-132">結構變數</span><span class="sxs-lookup"><span data-stu-id="e2a76-132">Structure Variables</span></span>](structure-variables.md)
- [<span data-ttu-id="e2a76-133">結構與其他程式設計項目</span><span class="sxs-lookup"><span data-stu-id="e2a76-133">Structures and Other Programming Elements</span></span>](structures-and-other-programming-elements.md)
- [<span data-ttu-id="e2a76-134">結構與類別</span><span class="sxs-lookup"><span data-stu-id="e2a76-134">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="e2a76-135">使用者定義資料類型</span><span class="sxs-lookup"><span data-stu-id="e2a76-135">User-Defined Data Type</span></span>](../../../language-reference/data-types/user-defined-data-type.md)
