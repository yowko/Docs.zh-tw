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
ms.openlocfilehash: 6e067d72e557b97f8626b148e173e3d1583f92b8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086266"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="94eb2-102">列舉和名稱限定 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94eb2-102">Enumerations and Name Qualification (Visual Basic)</span></span>

<span data-ttu-id="94eb2-103">一般來說，當參考列舉的成員時，您必須以列舉名稱來限定成員名稱。</span><span class="sxs-lookup"><span data-stu-id="94eb2-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="94eb2-104">例如，若要參考列舉的 `Sunday` 成員 `Days` ，您可以使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="94eb2-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="94eb2-105">使用 Imports 語句</span><span class="sxs-lookup"><span data-stu-id="94eb2-105">Using the Imports Statement</span></span>  

 <span data-ttu-id="94eb2-106">您可以將 `Imports` 語句新增至程式碼的命名空間宣告區段，以避免使用完整名稱，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="94eb2-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 <span data-ttu-id="94eb2-107">`Imports`語句會從參考的專案和元件中匯入命名空間名稱，並從相同的專案內匯入該語句所在的模組。</span><span class="sxs-lookup"><span data-stu-id="94eb2-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="94eb2-108">新增此語句之後，您可以參考您的列舉成員，而不需限定，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="94eb2-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 <span data-ttu-id="94eb2-109">藉由在列舉中組織相關的常數集合，您可以在不同的內容中使用相同的常數名稱。</span><span class="sxs-lookup"><span data-stu-id="94eb2-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="94eb2-110">例如，您可以針對和列舉中的工作日常數使用相同的名稱 `Days` `WorkDays` 。</span><span class="sxs-lookup"><span data-stu-id="94eb2-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="94eb2-111">如果您使用語句搭配列舉 `Imports` ，您必須小心避免不明確的參考。</span><span class="sxs-lookup"><span data-stu-id="94eb2-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="94eb2-112">請考慮下列範例：</span><span class="sxs-lookup"><span data-stu-id="94eb2-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 <span data-ttu-id="94eb2-113">假設 `Monday` 是 `Days` 列舉和列舉的成員 `Workdays` ，此程式碼會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="94eb2-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="94eb2-114">若要在參考個別常數時避免不明確的參考，請使用其列舉來限定常數名稱。</span><span class="sxs-lookup"><span data-stu-id="94eb2-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="94eb2-115">下列程式碼會參考 `Saturday` 和列舉中的 `Days` 常數 `WorkDays` 。</span><span class="sxs-lookup"><span data-stu-id="94eb2-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="94eb2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94eb2-116">See also</span></span>

- [<span data-ttu-id="94eb2-117">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="94eb2-117">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="94eb2-118">如何：宣告列舉類型</span><span class="sxs-lookup"><span data-stu-id="94eb2-118">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="94eb2-119">如何：參考列舉類型成員</span><span class="sxs-lookup"><span data-stu-id="94eb2-119">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="94eb2-120">如何：在 Visual Basic 中逐一查看列舉類型</span><span class="sxs-lookup"><span data-stu-id="94eb2-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="94eb2-121">如何：決定與列舉值相關聯的字串</span><span class="sxs-lookup"><span data-stu-id="94eb2-121">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="94eb2-122">何時使用列舉類型</span><span class="sxs-lookup"><span data-stu-id="94eb2-122">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="94eb2-123">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="94eb2-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="94eb2-124">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="94eb2-124">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="94eb2-125">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="94eb2-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="94eb2-126">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="94eb2-126">Data Types</span></span>](../../../language-reference/data-types/index.md)
