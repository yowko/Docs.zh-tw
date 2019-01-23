---
title: Sub 或 Function 未定義 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 4627f8ddb979780481feadbef06225baf6a7c0ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532171"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="088ec-102">Sub 或 Function 未定義 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="088ec-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="088ec-103">A`Sub`或`Function`必須定義，才能呼叫。</span><span class="sxs-lookup"><span data-stu-id="088ec-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="088ec-104">可能導致本錯誤的原因包括：</span><span class="sxs-lookup"><span data-stu-id="088ec-104">Possible causes of this error include:</span></span>  
  
-   <span data-ttu-id="088ec-105">拼錯下列程序名稱。</span><span class="sxs-lookup"><span data-stu-id="088ec-105">Misspelling the procedure name.</span></span>  
  
-   <span data-ttu-id="088ec-106">嘗試從另一個專案呼叫的程序，而不需明確新增至該專案中的參考**參考** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="088ec-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
-   <span data-ttu-id="088ec-107">指定看不到呼叫的程序的程序。</span><span class="sxs-lookup"><span data-stu-id="088ec-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
-   <span data-ttu-id="088ec-108">Windows 動態連結程式庫 (DLL) 常式或 Macintosh 不在指定的文件庫或程式碼資源的程式碼資源常式宣告。</span><span class="sxs-lookup"><span data-stu-id="088ec-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="088ec-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="088ec-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="088ec-110">請確定程序名稱拼字正確。</span><span class="sxs-lookup"><span data-stu-id="088ec-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2.  <span data-ttu-id="088ec-111">尋找包含您想要呼叫的程序的專案名稱**參考** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="088ec-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="088ec-112">如果沒有出現，請按一下**瀏覽**按鈕來搜尋它。</span><span class="sxs-lookup"><span data-stu-id="088ec-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="088ec-113">選取的專案名稱，左邊的核取方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="088ec-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="088ec-114">請檢查常式的名稱。</span><span class="sxs-lookup"><span data-stu-id="088ec-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="088ec-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="088ec-115">See also</span></span>
- [<span data-ttu-id="088ec-116">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="088ec-116">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="088ec-117">管理專案中的參考</span><span class="sxs-lookup"><span data-stu-id="088ec-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="088ec-118">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="088ec-118">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="088ec-119">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="088ec-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
