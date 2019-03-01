---
title: HOW TO：群組相關聯的常值放在一起 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 63475487c8a35f5b306b28d4e7097324bef00d85
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977821"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="6baee-102">HOW TO：群組相關聯的常值放在一起 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6baee-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="6baee-103">列舉是相關的常數群組在一起的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="6baee-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="6baee-104">您建立的列舉`Enum`「 宣告 」 區段中的類別或模組的陳述式。</span><span class="sxs-lookup"><span data-stu-id="6baee-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="6baee-105">如需詳細資訊，請參閱[如何：宣告列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)。</span><span class="sxs-lookup"><span data-stu-id="6baee-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="6baee-106">群組關聯的常數值</span><span class="sxs-lookup"><span data-stu-id="6baee-106">To group related constant values</span></span>  
  
1.  <span data-ttu-id="6baee-107">撰寫包含程式碼存取層級中，宣告`Enum`關鍵字，且有效的名稱。</span><span class="sxs-lookup"><span data-stu-id="6baee-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="6baee-108">這個範例會建立`Private`列舉型別， `temperatureValues`。</span><span class="sxs-lookup"><span data-stu-id="6baee-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2.  <span data-ttu-id="6baee-109">列舉中定義的常數。</span><span class="sxs-lookup"><span data-stu-id="6baee-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="6baee-110">這個範例會建立`Public`列舉型別`temperatureValues`並指派其值。</span><span class="sxs-lookup"><span data-stu-id="6baee-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6baee-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6baee-111">See also</span></span>
- [<span data-ttu-id="6baee-112">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="6baee-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="6baee-113">如何：參考列舉成員</span><span class="sxs-lookup"><span data-stu-id="6baee-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="6baee-114">何時使用列舉</span><span class="sxs-lookup"><span data-stu-id="6baee-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="6baee-115">常數的概觀</span><span class="sxs-lookup"><span data-stu-id="6baee-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="6baee-116">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="6baee-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="6baee-117">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="6baee-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
