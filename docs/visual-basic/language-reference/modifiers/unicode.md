---
title: Unicode
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: c4286ed9e9d5fd768ae29b7050b3d1505ccca9dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344215"
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="15439-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15439-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="15439-103">指定 Visual Basic 應該將所有字串封送處理成 Unicode 值，而不論所宣告的外部程式名稱為何。</span><span class="sxs-lookup"><span data-stu-id="15439-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="15439-104">當您呼叫在專案外部定義的程式時，Visual Basic 編譯器無法存取其所需的資訊，以便正確地呼叫程式。</span><span class="sxs-lookup"><span data-stu-id="15439-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="15439-105">此資訊包括程式所在位置、識別方式、其呼叫順序和傳回類型，以及它所使用的字串字元集。</span><span class="sxs-lookup"><span data-stu-id="15439-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="15439-106">[Declare 語句](../../../visual-basic/language-reference/statements/declare-statement.md)會建立外部程式的參考，並提供此必要資訊。</span><span class="sxs-lookup"><span data-stu-id="15439-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="15439-107">`Declare` 語句中的 `charsetmodifier` 部分會提供字元集資訊，以便在呼叫外部程式期間封送處理字串。</span><span class="sxs-lookup"><span data-stu-id="15439-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="15439-108">它也會影響 Visual Basic 在外部檔案中搜尋外部程式名稱的方式。</span><span class="sxs-lookup"><span data-stu-id="15439-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="15439-109">`Unicode` 修飾詞指定 Visual Basic 應該將所有字串封送處理成 Unicode 值，而且在搜尋過程中，不需要修改其名稱，就應該查閱程式。</span><span class="sxs-lookup"><span data-stu-id="15439-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="15439-110">如果未指定任何字元集修飾詞，`Ansi` 為預設值。</span><span class="sxs-lookup"><span data-stu-id="15439-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15439-111">備註</span><span class="sxs-lookup"><span data-stu-id="15439-111">Remarks</span></span>  
 <span data-ttu-id="15439-112">`Unicode` 修飾詞可以在此內容中使用：</span><span class="sxs-lookup"><span data-stu-id="15439-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="15439-113">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="15439-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="15439-114">智慧型裝置開發人員注意事項</span><span class="sxs-lookup"><span data-stu-id="15439-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="15439-115">不支援這個關鍵字。</span><span class="sxs-lookup"><span data-stu-id="15439-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15439-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15439-116">See also</span></span>

- [<span data-ttu-id="15439-117">Ansi</span><span class="sxs-lookup"><span data-stu-id="15439-117">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="15439-118">Auto</span><span class="sxs-lookup"><span data-stu-id="15439-118">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="15439-119">關鍵字</span><span class="sxs-lookup"><span data-stu-id="15439-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
