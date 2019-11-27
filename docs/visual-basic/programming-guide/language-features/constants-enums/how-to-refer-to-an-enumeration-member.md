---
title: 如何：參考列舉類型成員
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: 01db5b84783eda45cd7867dc8fea8a69fc18b98a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354001"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="1c19d-102">如何：參考列舉成員 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c19d-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="1c19d-103">列舉提供了一種便利的方式，可使用一組相關的常數，並將常數值與名稱產生關聯。</span><span class="sxs-lookup"><span data-stu-id="1c19d-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="1c19d-104">例如，您可以宣告列舉來當作一組與當週的日次建立關聯的整數常數，接著在程式碼中使用日次的名稱而不是它們的整數值。</span><span class="sxs-lookup"><span data-stu-id="1c19d-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="1c19d-105">您可以避免在 `Imports` 語句中使用完整限定名稱。</span><span class="sxs-lookup"><span data-stu-id="1c19d-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="1c19d-106">如需詳細資訊，請參閱列舉[和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)性。</span><span class="sxs-lookup"><span data-stu-id="1c19d-106">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="1c19d-107">參考列舉成員</span><span class="sxs-lookup"><span data-stu-id="1c19d-107">To refer to an enumeration member</span></span>  
  
- <span data-ttu-id="1c19d-108">使用列舉限定成員名稱。</span><span class="sxs-lookup"><span data-stu-id="1c19d-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="1c19d-109">例如，下列範例會將 `FirstDayOfWeek` 列舉的 `Saturday` 成員指派給變數 `DayValue`。</span><span class="sxs-lookup"><span data-stu-id="1c19d-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="1c19d-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="1c19d-110">See also</span></span>

- [<span data-ttu-id="1c19d-111">如何：宣告列舉</span><span class="sxs-lookup"><span data-stu-id="1c19d-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="1c19d-112">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="1c19d-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="1c19d-113">如何：在 Visual Basic 中逐一查看列舉</span><span class="sxs-lookup"><span data-stu-id="1c19d-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="1c19d-114">如何：決定與列舉值相關聯的字串</span><span class="sxs-lookup"><span data-stu-id="1c19d-114">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="1c19d-115">何時使用列舉</span><span class="sxs-lookup"><span data-stu-id="1c19d-115">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
