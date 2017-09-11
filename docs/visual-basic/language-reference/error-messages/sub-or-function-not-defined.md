---
title: "Sub 或 Function 未定義 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID35
dev_langs:
- VB
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 837beec039e1fb8f8a796b2781d93de6d4cfb33a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="5cd2e-102">Sub 或 Function 未定義 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5cd2e-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="5cd2e-103">A`Sub`或`Function`必須定義，才能呼叫。</span><span class="sxs-lookup"><span data-stu-id="5cd2e-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="5cd2e-104">可能導致本錯誤的原因包括：</span><span class="sxs-lookup"><span data-stu-id="5cd2e-104">Possible causes of this error include:</span></span>  
  
-   <span data-ttu-id="5cd2e-105">程序名稱的拼字錯誤。</span><span class="sxs-lookup"><span data-stu-id="5cd2e-105">Misspelling the procedure name.</span></span>  
  
-   <span data-ttu-id="5cd2e-106">嘗試從另一個專案呼叫的程序，而不需要明確地將參考加入專案中**參考**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5cd2e-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
-   <span data-ttu-id="5cd2e-107">指定看不到呼叫的程序的程序。</span><span class="sxs-lookup"><span data-stu-id="5cd2e-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
-   <span data-ttu-id="5cd2e-108">Windows 動態連結程式庫 (DLL) 常式或 Macintosh 不在指定的文件庫或程式碼資源的程式碼資源常式宣告。</span><span class="sxs-lookup"><span data-stu-id="5cd2e-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5cd2e-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="5cd2e-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="5cd2e-110">請確定該程序名稱拼寫正確。</span><span class="sxs-lookup"><span data-stu-id="5cd2e-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2.  <span data-ttu-id="5cd2e-111">找出包含您想要呼叫的程序的專案名稱**參考**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5cd2e-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="5cd2e-112">如果沒有出現，按一下 [**瀏覽**] 按鈕，以進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="5cd2e-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="5cd2e-113">選取的專案名稱，左邊的核取方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="5cd2e-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="5cd2e-114">請檢查常式的名稱。</span><span class="sxs-lookup"><span data-stu-id="5cd2e-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cd2e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cd2e-115">See Also</span></span>  
 <span data-ttu-id="5cd2e-116">[錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md) </span><span class="sxs-lookup"><span data-stu-id="5cd2e-116">[Error Types](../../../visual-basic/programming-guide/language-features/error-types.md) </span></span>  
<span data-ttu-id="5cd2e-117"> [管理專案中的參考](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span><span class="sxs-lookup"><span data-stu-id="5cd2e-117"> [Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span></span>  
<span data-ttu-id="5cd2e-118"> [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5cd2e-118"> [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="5cd2e-119"> [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)</span><span class="sxs-lookup"><span data-stu-id="5cd2e-119"> [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)</span></span>
