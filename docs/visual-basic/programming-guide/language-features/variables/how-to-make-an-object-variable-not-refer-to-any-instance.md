---
title: HOW TO：讓物件變數不參考任何執行個體 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: ceee1b47fb66cfb8e24b6871af3be6475031504f
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738873"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="3b8a9-102">HOW TO：讓物件變數不參考任何執行個體 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b8a9-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="3b8a9-103">您可以藉由將它設定為取消關聯的物件變數，從任何物件執行個體[Nothing](../../../../visual-basic/language-reference/nothing.md)。</span><span class="sxs-lookup"><span data-stu-id="3b8a9-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="3b8a9-104">若要解除關聯的物件變數，從任何物件執行個體</span><span class="sxs-lookup"><span data-stu-id="3b8a9-104">To disassociate an object variable from any object instance</span></span>  
  
-   <span data-ttu-id="3b8a9-105">將變數設定為`Nothing`指派陳述式中。</span><span class="sxs-lookup"><span data-stu-id="3b8a9-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="3b8a9-106">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="3b8a9-106">Robust Programming</span></span>  
 <span data-ttu-id="3b8a9-107">如果您的程式碼嘗試存取已設定為物件變數的成員`Nothing`、 <xref:System.NullReferenceException> ，就會發生。</span><span class="sxs-lookup"><span data-stu-id="3b8a9-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="3b8a9-108">如果您設定物件變數`Nothing`通常，如果有可能未初始化的變數，則會是個不錯的主意，來括住在成員存取`Try...Catch...Finally`區塊。</span><span class="sxs-lookup"><span data-stu-id="3b8a9-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="3b8a9-109">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="3b8a9-109">.NET Framework Security</span></span>  
 <span data-ttu-id="3b8a9-110">如果您使用物件變數包含機密或敏感性資料的物件時，您可以將變數設`Nothing`時您都不需要主動處理的其中一個這些物件。</span><span class="sxs-lookup"><span data-stu-id="3b8a9-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="3b8a9-111">這可以減少取得資料的存取權的惡意程式碼的機會。</span><span class="sxs-lookup"><span data-stu-id="3b8a9-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b8a9-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b8a9-112">See also</span></span>
- <xref:System.NullReferenceException>
- [<span data-ttu-id="3b8a9-113">物件變數</span><span class="sxs-lookup"><span data-stu-id="3b8a9-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="3b8a9-114">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="3b8a9-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="3b8a9-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="3b8a9-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="3b8a9-116">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="3b8a9-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
