---
title: Auto (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: e4beb320b3aa0cadb790dd3ab92255496bc32f05
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843834"
---
# <a name="auto-visual-basic"></a><span data-ttu-id="a090f-102">Auto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a090f-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="a090f-103">指定 Visual Basic 應封送處理根據.NET Framework 的規則，根據所宣告外部程序的外部名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="a090f-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="a090f-104">當您呼叫在專案以外定義的程序時，Visual Basic 編譯器並沒有存取它必須正確地呼叫程序的資訊。</span><span class="sxs-lookup"><span data-stu-id="a090f-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="a090f-105">此資訊包括程序所在的位置、 其識別方式、 其呼叫的順序和傳回型別，以及字串字元設定它使用。</span><span class="sxs-lookup"><span data-stu-id="a090f-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="a090f-106">[Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)會建立外部程序的參考，並提供這些必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="a090f-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="a090f-107">`charsetmodifier`部分`Declare`陳述式提供在外部的程序呼叫封送處理字串的字元組資訊。</span><span class="sxs-lookup"><span data-stu-id="a090f-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="a090f-108">它也會影響 Visual Basic 會將外部檔案的外部程序名稱的搜尋。</span><span class="sxs-lookup"><span data-stu-id="a090f-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="a090f-109">`Auto`修飾詞會指定 Visual Basic 應該根據.NET Framework 規則的字串封送處理和它應該決定設定的執行階段平台和可能的基底字元，修改外部程序名稱如果初始搜尋將會失敗。</span><span class="sxs-lookup"><span data-stu-id="a090f-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="a090f-110">如需詳細資訊，請參閱 < 字元集 」 中[Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="a090f-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="a090f-111">如果未不指定任何字元組修飾詞，則`Ansi`是預設值。</span><span class="sxs-lookup"><span data-stu-id="a090f-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a090f-112">備註</span><span class="sxs-lookup"><span data-stu-id="a090f-112">Remarks</span></span>  
 <span data-ttu-id="a090f-113">`Auto`修飾詞，請使用此內容中：</span><span class="sxs-lookup"><span data-stu-id="a090f-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="a090f-114">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="a090f-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="a090f-115">智慧型裝置開發人員注意事項</span><span class="sxs-lookup"><span data-stu-id="a090f-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="a090f-116">不支援此關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a090f-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a090f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a090f-117">See also</span></span>

- [<span data-ttu-id="a090f-118">Ansi</span><span class="sxs-lookup"><span data-stu-id="a090f-118">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="a090f-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="a090f-119">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)
- [<span data-ttu-id="a090f-120">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a090f-120">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
