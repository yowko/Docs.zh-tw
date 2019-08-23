---
title: End 語句 (Visual Basic)
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
ms.openlocfilehash: 9307cf10e6125441bd49baa0e663a5a13f234005
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944470"
---
# <a name="end-statement"></a><span data-ttu-id="0fcee-102">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="0fcee-102">End Statement</span></span>
<span data-ttu-id="0fcee-103">立即終止執行。</span><span class="sxs-lookup"><span data-stu-id="0fcee-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fcee-104">語法</span><span class="sxs-lookup"><span data-stu-id="0fcee-104">Syntax</span></span>  
  
```  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="0fcee-105">備註</span><span class="sxs-lookup"><span data-stu-id="0fcee-105">Remarks</span></span>  
 <span data-ttu-id="0fcee-106">您可以將`End`語句放在程式中的任何位置, 以強制整個應用程式停止執行。</span><span class="sxs-lookup"><span data-stu-id="0fcee-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="0fcee-107">`End`關閉任何以`Open`語句開啟的檔案, 並清除所有應用程式的變數。</span><span class="sxs-lookup"><span data-stu-id="0fcee-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="0fcee-108">應用程式會在沒有任何其他程式持有其物件的參考, 而且沒有任何執行中的程式碼時立即關閉。</span><span class="sxs-lookup"><span data-stu-id="0fcee-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0fcee-109">語句會突然停止程式碼執行, 而且不會`Dispose`叫用`Finalize`或方法, 或是任何其他 Visual Basic 程式碼。 `End`</span><span class="sxs-lookup"><span data-stu-id="0fcee-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="0fcee-110">其他程式所持有的物件參考無效。</span><span class="sxs-lookup"><span data-stu-id="0fcee-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="0fcee-111">`Finally`如果在或區塊`Catch`內遇到語句,則控制項不會傳遞至`End`對應 `Try`的區塊。</span><span class="sxs-lookup"><span data-stu-id="0fcee-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="0fcee-112">語句會暫停執行, 但與`End`不同的是, 它不會關閉任何檔案或清除任何變數, 除非在編譯的可執行檔 (.exe) 中遇到此錯誤。 `Stop`</span><span class="sxs-lookup"><span data-stu-id="0fcee-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="0fcee-113">由於`End`會終止您的應用程式, 而不會參與任何可能開啟的資源, 因此您應該在使用之前, 先徹底關閉。</span><span class="sxs-lookup"><span data-stu-id="0fcee-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="0fcee-114">例如, 如果您的應用程式開啟了任何表單, 您應該先關閉它們, `End`然後再控制到達語句。</span><span class="sxs-lookup"><span data-stu-id="0fcee-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="0fcee-115">您應該謹慎`End`使用, 而且只有在需要立即停止時才會用到。</span><span class="sxs-lookup"><span data-stu-id="0fcee-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="0fcee-116">結束程式 ([Return 語句](../../../visual-basic/language-reference/statements/return-statement.md)和[Exit 語句](../../../visual-basic/language-reference/statements/exit-statement.md)) 的一般方法不只是完全關閉程式, 還能讓呼叫程式碼有機會完全關閉。</span><span class="sxs-lookup"><span data-stu-id="0fcee-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="0fcee-117">例如, 主控台應用程式可以只`Return` `Main`從程式中進行。</span><span class="sxs-lookup"><span data-stu-id="0fcee-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0fcee-118">語句會<xref:System.Environment>在命名<xref:System>空間中<xref:System.Environment.Exit%2A>呼叫類別的方法。 `End`</span><span class="sxs-lookup"><span data-stu-id="0fcee-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="0fcee-119"><xref:System.Environment.Exit%2A>需要您擁有`UnmanagedCode`許可權。</span><span class="sxs-lookup"><span data-stu-id="0fcee-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="0fcee-120">如果不這麼做, <xref:System.Security.SecurityException>就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0fcee-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="0fcee-121">當後面加上額外的關鍵字時, [end \<關鍵字 > 語句](../../../visual-basic/language-reference/statements/end-keyword-statement.md)會描寫適當程式或區塊定義的結尾。</span><span class="sxs-lookup"><span data-stu-id="0fcee-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="0fcee-122">例如, `End Function`會結束程式的定義`Function` 。</span><span class="sxs-lookup"><span data-stu-id="0fcee-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fcee-123">範例</span><span class="sxs-lookup"><span data-stu-id="0fcee-123">Example</span></span>  
 <span data-ttu-id="0fcee-124">下列範例會使用`End`語句來結束程式碼執行 (如果使用者要求)。</span><span class="sxs-lookup"><span data-stu-id="0fcee-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="0fcee-125">智慧型裝置開發人員注意事項</span><span class="sxs-lookup"><span data-stu-id="0fcee-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="0fcee-126">不支援此語句。</span><span class="sxs-lookup"><span data-stu-id="0fcee-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fcee-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fcee-127">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [<span data-ttu-id="0fcee-128">Stop 陳述式</span><span class="sxs-lookup"><span data-stu-id="0fcee-128">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)
- [<span data-ttu-id="0fcee-129">End \<關鍵字 > 語句</span><span class="sxs-lookup"><span data-stu-id="0fcee-129">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
