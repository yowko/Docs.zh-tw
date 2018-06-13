---
title: Sub 或 Function 未定義 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 58e90d769d5a7f2d88b5c27d1ec7d0d28c8d7b03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593697"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="cf04d-102">Sub 或 Function 未定義 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf04d-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="cf04d-103">A`Sub`或`Function`必須定義，才能呼叫。</span><span class="sxs-lookup"><span data-stu-id="cf04d-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="cf04d-104">可能導致本錯誤的原因包括：</span><span class="sxs-lookup"><span data-stu-id="cf04d-104">Possible causes of this error include:</span></span>  
  
-   <span data-ttu-id="cf04d-105">拼錯的程序名稱。</span><span class="sxs-lookup"><span data-stu-id="cf04d-105">Misspelling the procedure name.</span></span>  
  
-   <span data-ttu-id="cf04d-106">嘗試從另一個專案中呼叫程序，而不需要明確加入至該專案中參考**參考** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cf04d-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
-   <span data-ttu-id="cf04d-107">指定看不到呼叫的程序的程序。</span><span class="sxs-lookup"><span data-stu-id="cf04d-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
-   <span data-ttu-id="cf04d-108">宣告 Windows 動態連結程式庫 (DLL) 常式或 Macintosh 不在指定的文件庫或程式碼資源的資源程式碼的常式。</span><span class="sxs-lookup"><span data-stu-id="cf04d-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cf04d-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="cf04d-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="cf04d-110">請確定程序名稱拼寫正確。</span><span class="sxs-lookup"><span data-stu-id="cf04d-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2.  <span data-ttu-id="cf04d-111">尋找包含您想要呼叫的程序的專案名稱**參考** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cf04d-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="cf04d-112">如果沒有出現，請按一下**瀏覽**按鈕，以進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="cf04d-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="cf04d-113">選取的專案名稱，左邊的核取方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="cf04d-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="cf04d-114">請檢查常式的名稱。</span><span class="sxs-lookup"><span data-stu-id="cf04d-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf04d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf04d-115">See Also</span></span>  
 [<span data-ttu-id="cf04d-116">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="cf04d-116">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="cf04d-117">管理專案中的參考</span><span class="sxs-lookup"><span data-stu-id="cf04d-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="cf04d-118">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="cf04d-118">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="cf04d-119">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="cf04d-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
