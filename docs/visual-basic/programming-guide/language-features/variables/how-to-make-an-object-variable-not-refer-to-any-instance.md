---
title: 如何：讓物件變數不參考執行個體
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 61bb06401ebd1e479c9256a80a12d87240831063
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91080249"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="11429-102">如何：讓物件變數不參考執行個體 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11429-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>

<span data-ttu-id="11429-103">您可以藉由將物件變數設定為 [Nothing](../../../language-reference/nothing.md)，將物件變數與任何物件實例解除關聯。</span><span class="sxs-lookup"><span data-stu-id="11429-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="11429-104">將物件變數與任何物件實例解除關聯</span><span class="sxs-lookup"><span data-stu-id="11429-104">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="11429-105">`Nothing`在指派語句中將變數設為。</span><span class="sxs-lookup"><span data-stu-id="11429-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="11429-106">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="11429-106">Robust Programming</span></span>  

 <span data-ttu-id="11429-107">如果您的程式碼嘗試存取已設定為的物件變數成員 `Nothing` ，則 <xref:System.NullReferenceException> 會發生。</span><span class="sxs-lookup"><span data-stu-id="11429-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="11429-108">如果您經常將物件變數設定為 `Nothing` ，或變數未初始化，則將成員存取放在區塊中是很好的做法 `Try...Catch...Finally` 。</span><span class="sxs-lookup"><span data-stu-id="11429-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="11429-109">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="11429-109">.NET Framework Security</span></span>  

 <span data-ttu-id="11429-110">如果您針對包含機密資料或機密資料的物件使用物件變數，您可以在 `Nothing` 不主動處理其中一個物件時，將變數設為。</span><span class="sxs-lookup"><span data-stu-id="11429-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="11429-111">這樣可減少惡意程式碼存取資料的機會。</span><span class="sxs-lookup"><span data-stu-id="11429-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11429-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11429-112">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="11429-113">物件變數</span><span class="sxs-lookup"><span data-stu-id="11429-113">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="11429-114">物件變數指派</span><span class="sxs-lookup"><span data-stu-id="11429-114">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="11429-115">什麼</span><span class="sxs-lookup"><span data-stu-id="11429-115">Nothing</span></span>](../../../language-reference/nothing.md)
- [<span data-ttu-id="11429-116">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="11429-116">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
