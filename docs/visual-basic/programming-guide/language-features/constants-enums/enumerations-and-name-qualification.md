---
title: 列舉和名稱限定性條件
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
ms.openlocfilehash: 4121266447b771ba954ad52a46e0d8b88de3f9cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347502"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="2417c-102">列舉和名稱限定 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2417c-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="2417c-103">一般來說，在參考列舉的成員時，您必須使用列舉名稱來限定成員名稱。</span><span class="sxs-lookup"><span data-stu-id="2417c-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="2417c-104">例如，若要參考 `Days` 列舉的 `Sunday` 成員，您可以使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="2417c-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="2417c-105">使用 Imports 語句</span><span class="sxs-lookup"><span data-stu-id="2417c-105">Using the Imports Statement</span></span>  
 <span data-ttu-id="2417c-106">您可以藉由將 `Imports` 語句加入程式碼的命名空間宣告區段，來避免使用完整名稱，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2417c-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 <span data-ttu-id="2417c-107">`Imports` 語句會從參考的專案和元件中匯入命名空間名稱，並從與語句出現所在模組的相同專案中匯入。</span><span class="sxs-lookup"><span data-stu-id="2417c-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="2417c-108">新增此語句之後，您可以參考列舉成員，而不需要限定，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2417c-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 <span data-ttu-id="2417c-109">藉由組織列舉中的相關常數集，您可以在不同的內容中使用相同的常數名稱。</span><span class="sxs-lookup"><span data-stu-id="2417c-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="2417c-110">例如，您可以將相同的名稱用於 `Days` 中的工作日常數，並 `WorkDays` 列舉。</span><span class="sxs-lookup"><span data-stu-id="2417c-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="2417c-111">如果您搭配列舉使用 `Imports` 語句，必須小心避免不明確的參考。</span><span class="sxs-lookup"><span data-stu-id="2417c-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="2417c-112">參考下列範例：</span><span class="sxs-lookup"><span data-stu-id="2417c-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 <span data-ttu-id="2417c-113">假設 `Monday` 同時是 `Days` 列舉和 `Workdays` 列舉的成員，則此程式碼會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="2417c-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="2417c-114">若要在參考個別常數時避免不明確的參考，請使用其列舉來限定常數名稱。</span><span class="sxs-lookup"><span data-stu-id="2417c-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="2417c-115">下列程式碼會參考 `Days` 和 `WorkDays` 列舉中的 `Saturday` 常數。</span><span class="sxs-lookup"><span data-stu-id="2417c-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="2417c-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="2417c-116">See also</span></span>

- [<span data-ttu-id="2417c-117">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="2417c-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="2417c-118">如何：宣告列舉</span><span class="sxs-lookup"><span data-stu-id="2417c-118">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="2417c-119">如何：參考列舉成員</span><span class="sxs-lookup"><span data-stu-id="2417c-119">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="2417c-120">如何：在 Visual Basic 中逐一查看列舉</span><span class="sxs-lookup"><span data-stu-id="2417c-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="2417c-121">如何：決定與列舉值相關聯的字串</span><span class="sxs-lookup"><span data-stu-id="2417c-121">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="2417c-122">何時使用列舉</span><span class="sxs-lookup"><span data-stu-id="2417c-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="2417c-123">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="2417c-123">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="2417c-124">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="2417c-124">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="2417c-125">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="2417c-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="2417c-126">資料類型</span><span class="sxs-lookup"><span data-stu-id="2417c-126">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
