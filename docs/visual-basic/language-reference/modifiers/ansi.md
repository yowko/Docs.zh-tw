---
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 0c38c2b81af7b4cb8fd1723853a09c5413f805af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344745"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="30378-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30378-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="30378-103">指定 Visual Basic 應該將所有字串封送處理成美國國家標準局（ANSI）值，而不論所宣告的外部程式名稱為何。</span><span class="sxs-lookup"><span data-stu-id="30378-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="30378-104">當您呼叫在專案外部定義的程式時，Visual Basic 編譯器無法存取正確呼叫程式所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="30378-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="30378-105">此資訊包括程式所在位置、識別方式、其呼叫順序和傳回類型，以及它所使用的字串字元集。</span><span class="sxs-lookup"><span data-stu-id="30378-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="30378-106">[Declare 語句](../../../visual-basic/language-reference/statements/declare-statement.md)會建立外部程式的參考，並提供此必要資訊。</span><span class="sxs-lookup"><span data-stu-id="30378-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="30378-107">`Declare` 語句中的 `charsetmodifier` 部分會在呼叫外部程式期間提供封送處理字串的字元集資訊。</span><span class="sxs-lookup"><span data-stu-id="30378-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="30378-108">它也會影響 Visual Basic 在外部檔案中搜尋外部程式名稱的方式。</span><span class="sxs-lookup"><span data-stu-id="30378-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="30378-109">`Ansi` 修飾詞指定 Visual Basic 應該將所有字串封送處理為 ANSI 值，而且在搜尋過程中，不需要修改其名稱，就應該查閱程式。</span><span class="sxs-lookup"><span data-stu-id="30378-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="30378-110">如果未指定任何字元集修飾詞，`Ansi` 為預設值。</span><span class="sxs-lookup"><span data-stu-id="30378-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30378-111">備註</span><span class="sxs-lookup"><span data-stu-id="30378-111">Remarks</span></span>  
 <span data-ttu-id="30378-112">`Ansi` 修飾詞可以在此內容中使用：</span><span class="sxs-lookup"><span data-stu-id="30378-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="30378-113">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="30378-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="30378-114">智慧型裝置開發人員注意事項</span><span class="sxs-lookup"><span data-stu-id="30378-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="30378-115">不支援這個關鍵字。</span><span class="sxs-lookup"><span data-stu-id="30378-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30378-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30378-116">See also</span></span>

- [<span data-ttu-id="30378-117">Auto</span><span class="sxs-lookup"><span data-stu-id="30378-117">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="30378-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="30378-118">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)
- [<span data-ttu-id="30378-119">關鍵字</span><span class="sxs-lookup"><span data-stu-id="30378-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
