---
title: 如何：讓物件變數不參考執行個體 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 8f85ba0adea522851e45b20ef5024491874c9a29
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43744017"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="0fc27-102">如何：讓物件變數不參考執行個體 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fc27-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="0fc27-103">您可以藉由將它設定為取消關聯的物件變數，從任何物件執行個體[Nothing](../../../../visual-basic/language-reference/nothing.md)。</span><span class="sxs-lookup"><span data-stu-id="0fc27-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="0fc27-104">若要解除關聯的物件變數，從任何物件執行個體</span><span class="sxs-lookup"><span data-stu-id="0fc27-104">To disassociate an object variable from any object instance</span></span>  
  
-   <span data-ttu-id="0fc27-105">將變數設定為`Nothing`指派陳述式中。</span><span class="sxs-lookup"><span data-stu-id="0fc27-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="0fc27-106">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="0fc27-106">Robust Programming</span></span>  
 <span data-ttu-id="0fc27-107">如果您的程式碼嘗試存取已設定為物件變數的成員`Nothing`、 <xref:System.NullReferenceException> ，就會發生。</span><span class="sxs-lookup"><span data-stu-id="0fc27-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="0fc27-108">如果您設定物件變數`Nothing`通常，如果有可能未初始化的變數，則會是個不錯的主意，來括住在成員存取`Try...Catch...Finally`區塊。</span><span class="sxs-lookup"><span data-stu-id="0fc27-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0fc27-109">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="0fc27-109">.NET Framework Security</span></span>  
 <span data-ttu-id="0fc27-110">如果您使用物件變數包含機密或敏感性資料的物件時，您可以將變數設`Nothing`時您都不需要主動處理的其中一個這些物件。</span><span class="sxs-lookup"><span data-stu-id="0fc27-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="0fc27-111">這可以減少取得資料的存取權的惡意程式碼的機會。</span><span class="sxs-lookup"><span data-stu-id="0fc27-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc27-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fc27-112">See Also</span></span>  
 <xref:System.NullReferenceException>  
 [<span data-ttu-id="0fc27-113">物件變數</span><span class="sxs-lookup"><span data-stu-id="0fc27-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="0fc27-114">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="0fc27-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="0fc27-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="0fc27-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="0fc27-116">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="0fc27-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="0fc27-117">疑難排解例外狀況：System.NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="0fc27-117">Troubleshooting Exceptions: System.NullReferenceException</span></span>](https://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)
