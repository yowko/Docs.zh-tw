---
title: Auto
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 7ea46e5f8b882bb986f23e792b240bad0c5be7a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351623"
---
# <a name="auto-visual-basic"></a><span data-ttu-id="51a9d-102">Auto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51a9d-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="51a9d-103">指定 Visual Basic 應根據所宣告外部程式的外部名稱，依據 .NET Framework 規則封送處理字串。</span><span class="sxs-lookup"><span data-stu-id="51a9d-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="51a9d-104">當您呼叫在專案外部定義的程式時，Visual Basic 編譯器無法存取正確呼叫程式所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="51a9d-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="51a9d-105">此資訊包括程式所在位置、識別方式、其呼叫順序和傳回類型，以及它所使用的字串字元集。</span><span class="sxs-lookup"><span data-stu-id="51a9d-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="51a9d-106">[Declare 語句](../../../visual-basic/language-reference/statements/declare-statement.md)會建立外部程式的參考，並提供此必要資訊。</span><span class="sxs-lookup"><span data-stu-id="51a9d-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="51a9d-107">`Declare` 語句中的 `charsetmodifier` 部分會在呼叫外部程式期間提供封送處理字串的字元集資訊。</span><span class="sxs-lookup"><span data-stu-id="51a9d-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="51a9d-108">它也會影響 Visual Basic 在外部檔案中搜尋外部程式名稱的方式。</span><span class="sxs-lookup"><span data-stu-id="51a9d-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="51a9d-109">`Auto` 修飾詞會指定 Visual Basic 應該根據 .NET Framework 規則封送處理字串，而且它應該決定執行時間平臺的基底字元集，如果初始搜尋失敗，則可能會修改外部程式名稱。</span><span class="sxs-lookup"><span data-stu-id="51a9d-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="51a9d-110">如需詳細資訊，請參閱[Declare 語句](../../../visual-basic/language-reference/statements/declare-statement.md)中的「字元集」。</span><span class="sxs-lookup"><span data-stu-id="51a9d-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="51a9d-111">如果未指定任何字元集修飾詞，`Ansi` 為預設值。</span><span class="sxs-lookup"><span data-stu-id="51a9d-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51a9d-112">備註</span><span class="sxs-lookup"><span data-stu-id="51a9d-112">Remarks</span></span>  
 <span data-ttu-id="51a9d-113">`Auto` 修飾詞可以在此內容中使用：</span><span class="sxs-lookup"><span data-stu-id="51a9d-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="51a9d-114">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="51a9d-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="51a9d-115">智慧型裝置開發人員注意事項</span><span class="sxs-lookup"><span data-stu-id="51a9d-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="51a9d-116">不支援這個關鍵字。</span><span class="sxs-lookup"><span data-stu-id="51a9d-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51a9d-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="51a9d-117">See also</span></span>

- [<span data-ttu-id="51a9d-118">Ansi</span><span class="sxs-lookup"><span data-stu-id="51a9d-118">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="51a9d-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="51a9d-119">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)
- [<span data-ttu-id="51a9d-120">關鍵字</span><span class="sxs-lookup"><span data-stu-id="51a9d-120">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
