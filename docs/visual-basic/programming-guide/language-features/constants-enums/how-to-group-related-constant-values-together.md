---
title: 如何：將關聯的常數值群組在一起
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 0f694aee722e8ce31f663ec9fe52a09a2eb2a958
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058725"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="55cef-102">如何：將關聯的常數值群組在一起 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55cef-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>

<span data-ttu-id="55cef-103">列舉是將相關常數群組在一起的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="55cef-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="55cef-104">您可以使用 `Enum` 類別或模組之宣告區段中的語句來建立列舉。</span><span class="sxs-lookup"><span data-stu-id="55cef-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="55cef-105">如需詳細資訊，請參閱 [如何：宣告列舉](how-to-declare-enumerations.md)。</span><span class="sxs-lookup"><span data-stu-id="55cef-105">For more information, see [How to: Declare an Enumeration](how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="55cef-106">若要將相關常數值分組</span><span class="sxs-lookup"><span data-stu-id="55cef-106">To group related constant values</span></span>  
  
1. <span data-ttu-id="55cef-107">撰寫包含程式碼存取層級、 `Enum` 關鍵字和有效名稱的宣告。</span><span class="sxs-lookup"><span data-stu-id="55cef-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="55cef-108">這個範例會建立 `Private` 列舉型別 `temperatureValues` 。</span><span class="sxs-lookup"><span data-stu-id="55cef-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. <span data-ttu-id="55cef-109">定義列舉中的常數。</span><span class="sxs-lookup"><span data-stu-id="55cef-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="55cef-110">這個範例會建立 `Public` 列舉 `temperatureValues` 並指派其值。</span><span class="sxs-lookup"><span data-stu-id="55cef-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="55cef-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55cef-111">See also</span></span>

- [<span data-ttu-id="55cef-112">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="55cef-112">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="55cef-113">如何：參考列舉類型成員</span><span class="sxs-lookup"><span data-stu-id="55cef-113">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="55cef-114">何時使用列舉類型</span><span class="sxs-lookup"><span data-stu-id="55cef-114">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="55cef-115">常數的概觀</span><span class="sxs-lookup"><span data-stu-id="55cef-115">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="55cef-116">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="55cef-116">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="55cef-117">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="55cef-117">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
