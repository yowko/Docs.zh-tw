---
title: 預設
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: 0c2808795d6fcbad7892369fd7f460ebf0406093
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372968"
---
# <a name="default-visual-basic"></a><span data-ttu-id="131d1-102">Default (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="131d1-102">Default (Visual Basic)</span></span>
<span data-ttu-id="131d1-103">將屬性識別為其類別、結構或介面的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="131d1-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="131d1-104">備註</span><span class="sxs-lookup"><span data-stu-id="131d1-104">Remarks</span></span>  
 <span data-ttu-id="131d1-105">類別、結構或介面最多可以指定其中一個屬性做為*預設屬性*，前提是該屬性至少接受一個參數。</span><span class="sxs-lookup"><span data-stu-id="131d1-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="131d1-106">如果程式碼在不指定成員的情況下參考類別或結構，Visual Basic 會將該參考解析為預設屬性。</span><span class="sxs-lookup"><span data-stu-id="131d1-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="131d1-107">預設屬性可能會減少原始碼字元數，但它們可能會使您的程式碼更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="131d1-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="131d1-108">如果呼叫程式碼不熟悉您的類別或結構，當它對類別或結構名稱進行參考時，就無法確定該參考是要存取類別或結構本身，還是預設屬性。</span><span class="sxs-lookup"><span data-stu-id="131d1-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="131d1-109">這可能會導致編譯器錯誤或細微的執行時間邏輯錯誤。</span><span class="sxs-lookup"><span data-stu-id="131d1-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="131d1-110">您可以藉由一律使用[Option Strict 語句](../statements/option-strict-statement.md)將編譯器類型檢查設定為，來減少預設屬性錯誤的機率 `On` 。</span><span class="sxs-lookup"><span data-stu-id="131d1-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="131d1-111">如果您打算在程式碼中使用預先定義的類別或結構，就必須判斷它是否有預設屬性，如果是，它的名稱為何。</span><span class="sxs-lookup"><span data-stu-id="131d1-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="131d1-112">由於這些缺點，您應該考慮不要定義預設屬性。</span><span class="sxs-lookup"><span data-stu-id="131d1-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="131d1-113">為了讓程式碼更容易閱讀，您也應該考慮明確參考所有屬性，甚至是預設屬性。</span><span class="sxs-lookup"><span data-stu-id="131d1-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="131d1-114">`Default`修飾詞可以在此內容中使用：</span><span class="sxs-lookup"><span data-stu-id="131d1-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="131d1-115">Property Statement</span><span class="sxs-lookup"><span data-stu-id="131d1-115">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="131d1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="131d1-116">See also</span></span>

- [<span data-ttu-id="131d1-117">如何：在 Visual Basic 中宣告及呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="131d1-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="131d1-118">關鍵字</span><span class="sxs-lookup"><span data-stu-id="131d1-118">Keywords</span></span>](../keywords/index.md)
