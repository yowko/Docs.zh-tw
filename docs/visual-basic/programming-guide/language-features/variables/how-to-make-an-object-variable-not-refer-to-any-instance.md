---
title: HOW TO：讓物件變數不參考任何實例（Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: e647f2f891b06aa1767faac49b01df98ea31ec1c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004909"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="6dcc8-102">HOW TO：讓物件變數不參考任何實例（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="6dcc8-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="6dcc8-103">您可以藉由將物件變數設定為 [[無](../../../../visual-basic/language-reference/nothing.md)]，將它與任何物件實例取消關聯。</span><span class="sxs-lookup"><span data-stu-id="6dcc8-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="6dcc8-104">取消物件變數與任何物件實例的關聯</span><span class="sxs-lookup"><span data-stu-id="6dcc8-104">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="6dcc8-105">在指派語句中，將變數設定為 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="6dcc8-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="6dcc8-106">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="6dcc8-106">Robust Programming</span></span>  
 <span data-ttu-id="6dcc8-107">如果您的程式碼嘗試存取已設定為 `Nothing` 之物件變數的成員，就會發生 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="6dcc8-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="6dcc8-108">如果您經常將物件變數設定為 `Nothing`，或是變數尚未初始化，則在 @no__t 1 區塊中括住成員存取是個不錯的主意。</span><span class="sxs-lookup"><span data-stu-id="6dcc8-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6dcc8-109">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="6dcc8-109">.NET Framework Security</span></span>  
 <span data-ttu-id="6dcc8-110">如果您使用物件變數做為包含機密或敏感性資料的物件，當您不積極處理其中一個物件時，可以將此變數設定為 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="6dcc8-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="6dcc8-111">這可減少惡意程式碼取得資料存取權的機會。</span><span class="sxs-lookup"><span data-stu-id="6dcc8-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dcc8-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dcc8-112">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="6dcc8-113">物件變數</span><span class="sxs-lookup"><span data-stu-id="6dcc8-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="6dcc8-114">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="6dcc8-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="6dcc8-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="6dcc8-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="6dcc8-116">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="6dcc8-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
