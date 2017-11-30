---
title: Default (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 18126a0a5b6254da0b43e806b3de1f5b2127e6a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="default-visual-basic"></a><span data-ttu-id="0db41-102">Default (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0db41-102">Default (Visual Basic)</span></span>
<span data-ttu-id="0db41-103">將屬性識別為其類別、 結構或介面的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="0db41-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0db41-104">備註</span><span class="sxs-lookup"><span data-stu-id="0db41-104">Remarks</span></span>  
 <span data-ttu-id="0db41-105">類別、 結構或介面可以指定最多一個做為其屬性*預設屬性*，前提是屬性會使用至少一個參數。</span><span class="sxs-lookup"><span data-stu-id="0db41-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="0db41-106">如果程式碼會產生類別或結構的參考，而不指定的成員，Visual Basic 會解析該參考的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="0db41-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="0db41-107">預設屬性可能會導致小型減少原始程式碼字元，但它們可讓您的程式碼更難閱讀。</span><span class="sxs-lookup"><span data-stu-id="0db41-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="0db41-108">如果類別或結構名稱的參考時呼叫的程式碼不熟悉您自己的類別或結構，它無法確定該參考存取類別或結構本身或預設屬性。</span><span class="sxs-lookup"><span data-stu-id="0db41-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="0db41-109">這可能會導致編譯器錯誤或難以察覺的執行階段邏輯錯誤。</span><span class="sxs-lookup"><span data-stu-id="0db41-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="0db41-110">您可以稍微降低預設屬性錯誤的機率都使用[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)設定要檢查的編譯器型別`On`。</span><span class="sxs-lookup"><span data-stu-id="0db41-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="0db41-111">如果您打算使用預先定義的類別或結構中程式碼，您必須判斷是否具有預設屬性，而且如果是，它的名稱為何。</span><span class="sxs-lookup"><span data-stu-id="0db41-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="0db41-112">由於這些缺點，您應該考慮不要定義預設屬性。</span><span class="sxs-lookup"><span data-stu-id="0db41-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="0db41-113">程式碼的可讀性，您應該也會考慮一律明確地參考所有屬性，甚至是預設屬性。</span><span class="sxs-lookup"><span data-stu-id="0db41-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="0db41-114">`Default`修飾詞可用於此內容：</span><span class="sxs-lookup"><span data-stu-id="0db41-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="0db41-115">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="0db41-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="0db41-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0db41-116">See Also</span></span>  
 [<span data-ttu-id="0db41-117">如何： 宣告及呼叫在 Visual Basic 中的預設屬性</span><span class="sxs-lookup"><span data-stu-id="0db41-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="0db41-118">關鍵字</span><span class="sxs-lookup"><span data-stu-id="0db41-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
