---
title: 如何：讓物件變數不參考執行個體
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: cce2e59cb76652937868a731ad308872d1aba2f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410447"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="b2479-102">如何：讓物件變數不參考執行個體 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2479-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="b2479-103">您可以藉由將物件變數設定為 [[無](../../../language-reference/nothing.md)]，將它與任何物件實例取消關聯。</span><span class="sxs-lookup"><span data-stu-id="b2479-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="b2479-104">取消物件變數與任何物件實例的關聯</span><span class="sxs-lookup"><span data-stu-id="b2479-104">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="b2479-105">在指派語句中，將變數設定為 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="b2479-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="b2479-106">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="b2479-106">Robust Programming</span></span>  
 <span data-ttu-id="b2479-107">如果您的程式碼嘗試存取已設定為之物件變數的成員 `Nothing` ， <xref:System.NullReferenceException> 就會發生。</span><span class="sxs-lookup"><span data-stu-id="b2479-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="b2479-108">如果您將物件變數設定為 [ `Nothing` 經常]，或者如果可能是變數未初始化，最好將成員存取括在 `Try...Catch...Finally` 區塊中。</span><span class="sxs-lookup"><span data-stu-id="b2479-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b2479-109">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="b2479-109">.NET Framework Security</span></span>  
 <span data-ttu-id="b2479-110">如果您針對包含機密或敏感性資料的物件使用物件變數，則可以在 `Nothing` 不積極處理其中一個物件時，將該變數設定為。</span><span class="sxs-lookup"><span data-stu-id="b2479-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="b2479-111">這可減少惡意程式碼取得資料存取權的機會。</span><span class="sxs-lookup"><span data-stu-id="b2479-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2479-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2479-112">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="b2479-113">物件變數</span><span class="sxs-lookup"><span data-stu-id="b2479-113">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="b2479-114">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="b2479-114">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="b2479-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="b2479-115">Nothing</span></span>](../../../language-reference/nothing.md)
- [<span data-ttu-id="b2479-116">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="b2479-116">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
