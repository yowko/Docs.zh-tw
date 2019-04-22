---
title: End 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: 4fc4fd36fb6b057195e9d8a79eb0a5b3ac9ff95c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832017"
---
# <a name="end-statement"></a><span data-ttu-id="0c573-102">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="0c573-102">End Statement</span></span>
<span data-ttu-id="0c573-103">立即結束執行。</span><span class="sxs-lookup"><span data-stu-id="0c573-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c573-104">語法</span><span class="sxs-lookup"><span data-stu-id="0c573-104">Syntax</span></span>  
  
```  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="0c573-105">備註</span><span class="sxs-lookup"><span data-stu-id="0c573-105">Remarks</span></span>  
 <span data-ttu-id="0c573-106">您可以將`End`強制整個應用程式停止執行程序中的任何位置的陳述式。</span><span class="sxs-lookup"><span data-stu-id="0c573-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="0c573-107">`End` 關閉任何開啟的檔案`Open`陳述式，並清除所有應用程式的變數。</span><span class="sxs-lookup"><span data-stu-id="0c573-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="0c573-108">只要不有任何其他程式會儲存其物件的參考，並沒有其程式碼正在關閉應用程式。</span><span class="sxs-lookup"><span data-stu-id="0c573-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c573-109">`End`陳述式會突然，停止執行程式碼，並不會呼叫`Dispose`或`Finalize`方法或任何其他 Visual Basic 程式碼。</span><span class="sxs-lookup"><span data-stu-id="0c573-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="0c573-110">其他程式所持有的物件參考都會失效。</span><span class="sxs-lookup"><span data-stu-id="0c573-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="0c573-111">如果`End`陳述式中遇到`Try`或是`Catch`區塊中，控制項不會通過對應`Finally`區塊。</span><span class="sxs-lookup"><span data-stu-id="0c573-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="0c573-112">`Stop`陳述式暫停執行，但不同於`End`，不會關閉任何檔案或清除任何變數，但若發生在已編譯可執行檔 (.exe) 檔案中。</span><span class="sxs-lookup"><span data-stu-id="0c573-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="0c573-113">因為`End`會終止您的應用程式不會理會可能已經開啟的任何資源，您應該試著關閉完全後才能使用它。</span><span class="sxs-lookup"><span data-stu-id="0c573-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="0c573-114">比方說，如果您的應用程式有任何開啟的表單，您應該先關閉這些控制項達到`End`陳述式。</span><span class="sxs-lookup"><span data-stu-id="0c573-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="0c573-115">您應該使用`End`盡量節制，而且只有當您需要立即停止。</span><span class="sxs-lookup"><span data-stu-id="0c573-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="0c573-116">終止程序的一般方式 ([Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)並[Exit 陳述式](../../../visual-basic/language-reference/statements/exit-statement.md)) 不僅完全關閉程序，但也可讓呼叫端程式碼完全關閉。</span><span class="sxs-lookup"><span data-stu-id="0c573-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="0c573-117">主控台應用程式，比方說，只要`Return`從`Main`程序。</span><span class="sxs-lookup"><span data-stu-id="0c573-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0c573-118">`End`陳述式會呼叫<xref:System.Environment.Exit%2A>方法<xref:System.Environment>類別在<xref:System>命名空間。</span><span class="sxs-lookup"><span data-stu-id="0c573-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="0c573-119"><xref:System.Environment.Exit%2A> 您必須有`UnmanagedCode`權限。</span><span class="sxs-lookup"><span data-stu-id="0c573-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="0c573-120">如果您未這麼做，<xref:System.Security.SecurityException>就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0c573-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="0c573-121">其他的關鍵字，後面跟著[結束\<關鍵字 > 陳述式](../../../visual-basic/language-reference/statements/end-keyword-statement.md)描述定義適當的程序或區塊的結尾。</span><span class="sxs-lookup"><span data-stu-id="0c573-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="0c573-122">例如，`End Function`結束的定義`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="0c573-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c573-123">範例</span><span class="sxs-lookup"><span data-stu-id="0c573-123">Example</span></span>  
 <span data-ttu-id="0c573-124">下列範例會使用`End`陳述式來終止執行程式碼，如果在使用者要求。</span><span class="sxs-lookup"><span data-stu-id="0c573-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="0c573-125">智慧型裝置開發人員注意事項</span><span class="sxs-lookup"><span data-stu-id="0c573-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="0c573-126">不支援此陳述式。</span><span class="sxs-lookup"><span data-stu-id="0c573-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c573-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c573-127">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [<span data-ttu-id="0c573-128">Stop 陳述式</span><span class="sxs-lookup"><span data-stu-id="0c573-128">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)
- [<span data-ttu-id="0c573-129">結束\<關鍵字 > 陳述式</span><span class="sxs-lookup"><span data-stu-id="0c573-129">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
