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
ms.openlocfilehash: bc213c3b5564d1833136df8f5b8dab1c6b012296
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875493"
---
# <a name="default-visual-basic"></a><span data-ttu-id="b7926-102">Default (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7926-102">Default (Visual Basic)</span></span>

<span data-ttu-id="b7926-103">將屬性識別為其類別、結構或介面的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="b7926-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7926-104">備註</span><span class="sxs-lookup"><span data-stu-id="b7926-104">Remarks</span></span>  

 <span data-ttu-id="b7926-105">類別、結構或介面最多可將其中一個屬性指定為 *預設屬性*，前提是該屬性至少接受一個參數。</span><span class="sxs-lookup"><span data-stu-id="b7926-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="b7926-106">如果程式碼在沒有指定成員的情況下參考類別或結構，Visual Basic 會將該參考解析為預設屬性。</span><span class="sxs-lookup"><span data-stu-id="b7926-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="b7926-107">預設屬性可能會減少原始程式碼字元，但可以讓您的程式碼更難以讀取。</span><span class="sxs-lookup"><span data-stu-id="b7926-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="b7926-108">如果呼叫程式碼不熟悉您的類別或結構，則在參考類別或結構名稱時，如果該參考存取類別或結構本身或預設屬性，則無法確定。</span><span class="sxs-lookup"><span data-stu-id="b7926-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="b7926-109">這可能會導致編譯器錯誤或微妙的執行時間邏輯錯誤。</span><span class="sxs-lookup"><span data-stu-id="b7926-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="b7926-110">您可以使用 [Option Strict 語句](../statements/option-strict-statement.md) 將編譯器類型檢查設定為，以稍微減少預設屬性錯誤的機率 `On` 。</span><span class="sxs-lookup"><span data-stu-id="b7926-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="b7926-111">如果您打算在程式碼中使用預先定義的類別或結構，就必須判斷它是否有預設屬性，如果是，它的名稱就是。</span><span class="sxs-lookup"><span data-stu-id="b7926-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="b7926-112">因為這些缺點，您應該考慮不要定義預設屬性。</span><span class="sxs-lookup"><span data-stu-id="b7926-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="b7926-113">為了讓程式碼更容易閱讀，您也應該考慮一律明確參考所有屬性，甚至是預設屬性。</span><span class="sxs-lookup"><span data-stu-id="b7926-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="b7926-114">`Default`修飾詞可用於此內容中：</span><span class="sxs-lookup"><span data-stu-id="b7926-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="b7926-115">Property Statement</span><span class="sxs-lookup"><span data-stu-id="b7926-115">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="b7926-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7926-116">See also</span></span>

- [<span data-ttu-id="b7926-117">如何：在 Visual Basic 中宣告及呼叫預設屬性</span><span class="sxs-lookup"><span data-stu-id="b7926-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="b7926-118">關鍵字</span><span class="sxs-lookup"><span data-stu-id="b7926-118">Keywords</span></span>](../keywords/index.md)
