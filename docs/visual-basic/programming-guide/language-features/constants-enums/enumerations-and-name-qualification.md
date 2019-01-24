---
title: 列舉和名稱限定 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: 0336ac54c6a0dadeb9758bcb15477fe96dbfcc65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513694"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="5f441-102">列舉和名稱限定 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f441-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="5f441-103">一般來說，當參考的列舉型別成員，您必須限定成員名稱列舉型別名稱。</span><span class="sxs-lookup"><span data-stu-id="5f441-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="5f441-104">例如，請參閱`Sunday`隸屬您`Days`列舉型別，您可以使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="5f441-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="5f441-105">使用 Imports 陳述式</span><span class="sxs-lookup"><span data-stu-id="5f441-105">Using the Imports Statement</span></span>  
 <span data-ttu-id="5f441-106">您可以避免使用完整限定的名稱，藉由新增`Imports`陳述式，以您的程式碼，如下列範例所示的命名空間宣告區段：</span><span class="sxs-lookup"><span data-stu-id="5f441-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 <span data-ttu-id="5f441-107">`Imports`陳述式匯入命名空間名稱，從參考的專案和組件和從模組的陳述式會出現相同的專案。</span><span class="sxs-lookup"><span data-stu-id="5f441-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="5f441-108">加入這個陳述式後，您可以參考您的列舉成員，但是不限定，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="5f441-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 <span data-ttu-id="5f441-109">藉由組織列舉型別中的相關常數組，您可以使用相同的常數名稱，在不同的內容中。</span><span class="sxs-lookup"><span data-stu-id="5f441-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="5f441-110">例如，您可以使用相同的名稱，在工作日常數`Days`和`WorkDays`列舉型別。</span><span class="sxs-lookup"><span data-stu-id="5f441-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="5f441-111">如果您使用`Imports`陳述式中的對列舉型別，您必須小心避免模稜兩可的參考。</span><span class="sxs-lookup"><span data-stu-id="5f441-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="5f441-112">參考下列範例：</span><span class="sxs-lookup"><span data-stu-id="5f441-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 <span data-ttu-id="5f441-113">假設`Monday`兩者的成員`Days`列舉型別和`Workdays`列舉型別，此程式碼會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="5f441-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="5f441-114">若要參考個別的常數時，請避免模稜兩可的參考，限定的列舉常數的名稱。</span><span class="sxs-lookup"><span data-stu-id="5f441-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="5f441-115">下列程式碼是指`Saturday`中的常數`Days`和`WorkDays`列舉型別。</span><span class="sxs-lookup"><span data-stu-id="5f441-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5f441-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f441-116">See also</span></span>
- [<span data-ttu-id="5f441-117">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="5f441-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="5f441-118">如何：宣告列舉</span><span class="sxs-lookup"><span data-stu-id="5f441-118">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="5f441-119">如何：參考列舉成員</span><span class="sxs-lookup"><span data-stu-id="5f441-119">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="5f441-120">如何：逐一查看 Visual Basic 中列舉</span><span class="sxs-lookup"><span data-stu-id="5f441-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="5f441-121">如何：決定與列舉值關聯的字串</span><span class="sxs-lookup"><span data-stu-id="5f441-121">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="5f441-122">何時使用列舉</span><span class="sxs-lookup"><span data-stu-id="5f441-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="5f441-123">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="5f441-123">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="5f441-124">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="5f441-124">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="5f441-125">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="5f441-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="5f441-126">資料類型</span><span class="sxs-lookup"><span data-stu-id="5f441-126">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
