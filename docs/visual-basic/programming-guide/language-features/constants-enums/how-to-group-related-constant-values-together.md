---
title: "如何：將關聯的常數值群組在一起 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be57b56047654d6eb3536bb0b8f63eca27decdb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="99f02-102">如何：將關聯的常數值群組在一起 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99f02-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="99f02-103">列舉類型是最佳的方式來分組相關的常數。</span><span class="sxs-lookup"><span data-stu-id="99f02-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="99f02-104">建立列舉，含`Enum`陳述式的宣告區段中的類別或模組。</span><span class="sxs-lookup"><span data-stu-id="99f02-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="99f02-105">如需詳細資訊，請參閱[如何： 宣告列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)。</span><span class="sxs-lookup"><span data-stu-id="99f02-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="99f02-106">群組關聯的常數值</span><span class="sxs-lookup"><span data-stu-id="99f02-106">To group related constant values</span></span>  
  
1.  <span data-ttu-id="99f02-107">撰寫包含程式碼存取層級中，宣告`Enum`關鍵字，且是有效的名稱。</span><span class="sxs-lookup"><span data-stu-id="99f02-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="99f02-108">這個範例會建立`Private`列舉型別， `temperatureValues`。</span><span class="sxs-lookup"><span data-stu-id="99f02-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]  
  
2.  <span data-ttu-id="99f02-109">列舉型別中定義的常數。</span><span class="sxs-lookup"><span data-stu-id="99f02-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="99f02-110">這個範例會建立`Public`列舉`temperatureValues`並指派其值。</span><span class="sxs-lookup"><span data-stu-id="99f02-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="99f02-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99f02-111">See Also</span></span>  
 [<span data-ttu-id="99f02-112">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="99f02-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="99f02-113">如何：參考列舉成員</span><span class="sxs-lookup"><span data-stu-id="99f02-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="99f02-114">何時使用列舉</span><span class="sxs-lookup"><span data-stu-id="99f02-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="99f02-115">常數的概觀</span><span class="sxs-lookup"><span data-stu-id="99f02-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="99f02-116">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="99f02-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="99f02-117">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="99f02-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
