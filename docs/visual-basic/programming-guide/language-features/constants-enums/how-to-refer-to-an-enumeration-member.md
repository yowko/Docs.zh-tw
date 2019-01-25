---
title: HOW TO：參考列舉成員 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: efaaecb231b340798012206a0f23fde0ad4cdbeb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601994"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="cdd88-102">HOW TO：參考列舉成員 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cdd88-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="cdd88-103">列舉型別提供便利的方式來使用相關常數組和名稱相關聯的常數值。</span><span class="sxs-lookup"><span data-stu-id="cdd88-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="cdd88-104">例如，您可以宣告列舉來當作一組與當週的日次建立關聯的整數常數，接著在程式碼中使用日次的名稱而不是它們的整數值。</span><span class="sxs-lookup"><span data-stu-id="cdd88-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="cdd88-105">您可以避免使用具有完整格式的名稱`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="cdd88-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="cdd88-106">如需詳細資訊，請參閱 <<c0> [ 列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)。</span><span class="sxs-lookup"><span data-stu-id="cdd88-106">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="cdd88-107">若要參考列舉成員</span><span class="sxs-lookup"><span data-stu-id="cdd88-107">To refer to an enumeration member</span></span>  
  
-   <span data-ttu-id="cdd88-108">限定成員名稱與列舉型別。</span><span class="sxs-lookup"><span data-stu-id="cdd88-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="cdd88-109">例如，下列範例會將指派`Saturday`隸屬`FirstDayOfWeek`列舉型別變數`DayValue`。</span><span class="sxs-lookup"><span data-stu-id="cdd88-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-refer-to-an-enumeration-member_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cdd88-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdd88-110">See also</span></span>
- [<span data-ttu-id="cdd88-111">如何：宣告列舉</span><span class="sxs-lookup"><span data-stu-id="cdd88-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="cdd88-112">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="cdd88-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="cdd88-113">如何：逐一查看 Visual Basic 中列舉</span><span class="sxs-lookup"><span data-stu-id="cdd88-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="cdd88-114">如何：決定與列舉值關聯的字串</span><span class="sxs-lookup"><span data-stu-id="cdd88-114">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="cdd88-115">何時使用列舉</span><span class="sxs-lookup"><span data-stu-id="cdd88-115">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
