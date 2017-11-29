---
title: Ansi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aa5724eb9123b2776c3a579e4244c55b3129816b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="7b7ae-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b7ae-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="7b7ae-103">指定 Visual Basic 應封送處理至 Institute (ANSI) 值，不論所宣告外部程序名稱的所有字串。</span><span class="sxs-lookup"><span data-stu-id="7b7ae-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="7b7ae-104">當您呼叫在專案外部定義的程序時，Visual Basic 編譯器並沒有存取它需要正確地呼叫程序的資訊。</span><span class="sxs-lookup"><span data-stu-id="7b7ae-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="7b7ae-105">此資訊包括程序所在的位置、 如何識別、 它的呼叫順序和傳回型別，以及字串字元設定它使用。</span><span class="sxs-lookup"><span data-stu-id="7b7ae-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="7b7ae-106">[Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)會建立外部程序的參考，並提供此必要資訊。</span><span class="sxs-lookup"><span data-stu-id="7b7ae-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="7b7ae-107">`charsetmodifier`的一部分`Declare`陳述式提供給外部程序呼叫期間封送處理字串的字元組資訊。</span><span class="sxs-lookup"><span data-stu-id="7b7ae-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="7b7ae-108">它也會影響 Visual Basic 會將外部檔案的外部程序名稱的搜尋。</span><span class="sxs-lookup"><span data-stu-id="7b7ae-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="7b7ae-109">`Ansi`修飾詞會指定 Visual Basic 應封送處理為 ANSI 值的所有字串和應查詢程序而不需在搜尋期間修改其名稱。</span><span class="sxs-lookup"><span data-stu-id="7b7ae-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="7b7ae-110">如果未不指定任何字元 set 修飾詞，則`Ansi`是預設值。</span><span class="sxs-lookup"><span data-stu-id="7b7ae-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b7ae-111">備註</span><span class="sxs-lookup"><span data-stu-id="7b7ae-111">Remarks</span></span>  
 <span data-ttu-id="7b7ae-112">`Ansi`修飾詞可用於此內容：</span><span class="sxs-lookup"><span data-stu-id="7b7ae-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="7b7ae-113">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="7b7ae-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="7b7ae-114">智慧型裝置開發人員注意事項</span><span class="sxs-lookup"><span data-stu-id="7b7ae-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="7b7ae-115">不支援此關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7b7ae-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b7ae-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b7ae-116">See Also</span></span>  
 [<span data-ttu-id="7b7ae-117">Auto</span><span class="sxs-lookup"><span data-stu-id="7b7ae-117">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)  
 [<span data-ttu-id="7b7ae-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="7b7ae-118">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [<span data-ttu-id="7b7ae-119">關鍵字</span><span class="sxs-lookup"><span data-stu-id="7b7ae-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
