---
title: Auto (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1e32c4c910567829a4f5c59b48020db4dfbbeb7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="auto-visual-basic"></a><span data-ttu-id="a19a2-102">Auto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a19a2-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="a19a2-103">指定 Visual Basic 應封送處理字串根據.NET Framework 外部的程序所宣告的外部名稱為基礎的規則。</span><span class="sxs-lookup"><span data-stu-id="a19a2-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="a19a2-104">當您呼叫在專案外部定義的程序時，Visual Basic 編譯器並沒有存取它必須能夠正確地呼叫程序的資訊。</span><span class="sxs-lookup"><span data-stu-id="a19a2-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="a19a2-105">此資訊包括程序所在的位置、 如何識別、 它的呼叫順序和傳回型別，以及字串字元設定它使用。</span><span class="sxs-lookup"><span data-stu-id="a19a2-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="a19a2-106">[Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)會建立外部程序的參考，並提供此必要資訊。</span><span class="sxs-lookup"><span data-stu-id="a19a2-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="a19a2-107">`charsetmodifier`的一部分`Declare`陳述式提供給外部程序呼叫期間封送處理字串的字元組資訊。</span><span class="sxs-lookup"><span data-stu-id="a19a2-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="a19a2-108">它也會影響 Visual Basic 會將外部檔案的外部程序名稱的搜尋。</span><span class="sxs-lookup"><span data-stu-id="a19a2-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="a19a2-109">`Auto`修飾詞會指定 Visual Basic 應該根據.NET Framework 規則字串封送處理和，應該判斷基底字元集的執行階段平台，且可能修改外部程序名稱，如果初始搜尋將會失敗。</span><span class="sxs-lookup"><span data-stu-id="a19a2-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="a19a2-110">如需詳細資訊，請參閱 「 字元集 」 中[Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="a19a2-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="a19a2-111">如果未不指定任何字元 set 修飾詞，則`Ansi`是預設值。</span><span class="sxs-lookup"><span data-stu-id="a19a2-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a19a2-112">備註</span><span class="sxs-lookup"><span data-stu-id="a19a2-112">Remarks</span></span>  
 <span data-ttu-id="a19a2-113">`Auto`修飾詞可用於此內容：</span><span class="sxs-lookup"><span data-stu-id="a19a2-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="a19a2-114">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="a19a2-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="a19a2-115">智慧型裝置開發人員注意事項</span><span class="sxs-lookup"><span data-stu-id="a19a2-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="a19a2-116">不支援此關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a19a2-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a19a2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a19a2-117">See Also</span></span>  
 [<span data-ttu-id="a19a2-118">Ansi</span><span class="sxs-lookup"><span data-stu-id="a19a2-118">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [<span data-ttu-id="a19a2-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="a19a2-119">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [<span data-ttu-id="a19a2-120">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a19a2-120">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
