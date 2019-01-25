---
title: Unicode (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: 491bbb24be8e6a3044b0a433c5ad262596ae00d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655279"
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="3bb2d-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3bb2d-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="3bb2d-103">指定 Visual Basic 應封送處理為 Unicode 值，不論所宣告外部程序名稱的所有字串。</span><span class="sxs-lookup"><span data-stu-id="3bb2d-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="3bb2d-104">當您呼叫在專案以外定義的程序時，Visual Basic 編譯器並沒有存取它必須擁有才能正確地呼叫程序的資訊。</span><span class="sxs-lookup"><span data-stu-id="3bb2d-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="3bb2d-105">此資訊包括程序所在的位置、 其識別方式、 其呼叫的順序和傳回型別，以及字串字元設定它使用。</span><span class="sxs-lookup"><span data-stu-id="3bb2d-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="3bb2d-106">[Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)會建立外部程序的參考，並提供這些必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="3bb2d-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="3bb2d-107">`charsetmodifier`部分`Declare`陳述式提供在外部的程序呼叫封送處理字串的字元組資訊。</span><span class="sxs-lookup"><span data-stu-id="3bb2d-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="3bb2d-108">它也會影響 Visual Basic 會將外部檔案的外部程序名稱的搜尋。</span><span class="sxs-lookup"><span data-stu-id="3bb2d-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="3bb2d-109">`Unicode`修飾詞會指定 Visual Basic 應封送處理為 Unicode 值的所有字串，並應該查閱而不需要在搜尋期間修改其名稱的程序。</span><span class="sxs-lookup"><span data-stu-id="3bb2d-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="3bb2d-110">如果未不指定任何字元組修飾詞，則`Ansi`是預設值。</span><span class="sxs-lookup"><span data-stu-id="3bb2d-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bb2d-111">備註</span><span class="sxs-lookup"><span data-stu-id="3bb2d-111">Remarks</span></span>  
 <span data-ttu-id="3bb2d-112">`Unicode`修飾詞，請使用此內容中：</span><span class="sxs-lookup"><span data-stu-id="3bb2d-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="3bb2d-113">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="3bb2d-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="3bb2d-114">智慧型裝置開發人員注意事項</span><span class="sxs-lookup"><span data-stu-id="3bb2d-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="3bb2d-115">不支援此關鍵字。</span><span class="sxs-lookup"><span data-stu-id="3bb2d-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bb2d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bb2d-116">See also</span></span>
- [<span data-ttu-id="3bb2d-117">Ansi</span><span class="sxs-lookup"><span data-stu-id="3bb2d-117">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="3bb2d-118">Auto</span><span class="sxs-lookup"><span data-stu-id="3bb2d-118">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="3bb2d-119">關鍵字</span><span class="sxs-lookup"><span data-stu-id="3bb2d-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
