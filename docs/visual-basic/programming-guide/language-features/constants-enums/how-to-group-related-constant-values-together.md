---
title: 如何：將關聯的常數值群組在一起
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 151eefee4f69e1db8ba40f91334da8a051b95732
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354037"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="959a0-102">如何：將關聯的常數值群組在一起 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="959a0-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="959a0-103">An enumeration is the best way to group related constants together.</span><span class="sxs-lookup"><span data-stu-id="959a0-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="959a0-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span><span class="sxs-lookup"><span data-stu-id="959a0-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="959a0-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="959a0-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="959a0-106">To group related constant values</span><span class="sxs-lookup"><span data-stu-id="959a0-106">To group related constant values</span></span>  
  
1. <span data-ttu-id="959a0-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span><span class="sxs-lookup"><span data-stu-id="959a0-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="959a0-108">This example creates the `Private` enumeration, `temperatureValues`.</span><span class="sxs-lookup"><span data-stu-id="959a0-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. <span data-ttu-id="959a0-109">Define the constants in the enumeration.</span><span class="sxs-lookup"><span data-stu-id="959a0-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="959a0-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span><span class="sxs-lookup"><span data-stu-id="959a0-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="959a0-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="959a0-111">See also</span></span>

- [<span data-ttu-id="959a0-112">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="959a0-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="959a0-113">如何：參考列舉成員</span><span class="sxs-lookup"><span data-stu-id="959a0-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="959a0-114">何時使用列舉</span><span class="sxs-lookup"><span data-stu-id="959a0-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="959a0-115">常數的概觀</span><span class="sxs-lookup"><span data-stu-id="959a0-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="959a0-116">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="959a0-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="959a0-117">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="959a0-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
