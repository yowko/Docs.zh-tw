---
title: End 陳述式
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
ms.openlocfilehash: 0c99b919b50701e93fab7caf5fb5d8b6b976d44b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90865855"
---
# <a name="end-statement"></a><span data-ttu-id="7e029-102">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="7e029-102">End Statement</span></span>

<span data-ttu-id="7e029-103">立即終止執行。</span><span class="sxs-lookup"><span data-stu-id="7e029-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e029-104">語法</span><span class="sxs-lookup"><span data-stu-id="7e029-104">Syntax</span></span>  
  
```vb  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="7e029-105">備註</span><span class="sxs-lookup"><span data-stu-id="7e029-105">Remarks</span></span>  

 <span data-ttu-id="7e029-106">您可以將 `End` 語句放在程式中的任何位置，以強制整個應用程式停止執行。</span><span class="sxs-lookup"><span data-stu-id="7e029-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="7e029-107">`End` 關閉任何以語句開啟的檔案 `Open` ，並清除所有應用程式的變數。</span><span class="sxs-lookup"><span data-stu-id="7e029-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="7e029-108">只要沒有任何其他程式保留其物件的參考，而且沒有任何程式碼正在執行時，應用程式就會關閉。</span><span class="sxs-lookup"><span data-stu-id="7e029-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e029-109">`End`語句會突然停止執行程式碼，而不會叫用 `Dispose` 或 `Finalize` 方法，或任何其他 Visual Basic 程式碼。</span><span class="sxs-lookup"><span data-stu-id="7e029-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="7e029-110">其他程式所持有的物件參考無效。</span><span class="sxs-lookup"><span data-stu-id="7e029-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="7e029-111">如果在 `End` 或區塊中遇到語句 `Try` `Catch` ，控制項就不會傳遞至對應的 `Finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="7e029-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="7e029-112">`Stop`語句會暫停執行，但與不同的 `End` 是，它不會關閉任何檔案或清除任何變數，除非在編譯的可執行檔 ( .exe) 檔中遇到。</span><span class="sxs-lookup"><span data-stu-id="7e029-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="7e029-113">由於您 `End` 的應用程式會在不參與任何可能開啟的資源的情況下終止，所以您應該嘗試在使用之前先徹底關閉。</span><span class="sxs-lookup"><span data-stu-id="7e029-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="7e029-114">例如，如果您的應用程式已開啟任何表單，您應該在控制權到達語句之前將其關閉 `End` 。</span><span class="sxs-lookup"><span data-stu-id="7e029-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="7e029-115">您應該 `End` 謹慎使用，而且只有在需要立即停止時才需要。</span><span class="sxs-lookup"><span data-stu-id="7e029-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="7e029-116">終止程式 (傳回 [語句](return-statement.md) 和結束 [語句](exit-statement.md) 的一般方式，) 不僅能完全關閉程式，還可讓呼叫程式碼有機會完全關閉。</span><span class="sxs-lookup"><span data-stu-id="7e029-116">The normal ways to terminate a procedure ([Return Statement](return-statement.md) and [Exit Statement](exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="7e029-117">例如，主控台應用程式可以直接從程式 `Return` 中取得 `Main` 。</span><span class="sxs-lookup"><span data-stu-id="7e029-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7e029-118">`End`語句會呼叫 <xref:System.Environment.Exit%2A> <xref:System.Environment> 命名空間中類別的方法 <xref:System> 。</span><span class="sxs-lookup"><span data-stu-id="7e029-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="7e029-119"><xref:System.Environment.Exit%2A> 需要您具備 `UnmanagedCode` 許可權。</span><span class="sxs-lookup"><span data-stu-id="7e029-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="7e029-120">如果沒有， <xref:System.Security.SecurityException> 就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7e029-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="7e029-121">當後面加上其他關鍵字時， [end \<keyword> 語句](end-keyword-statement.md) 會描述適當程式或區塊的定義結尾。</span><span class="sxs-lookup"><span data-stu-id="7e029-121">When followed by an additional keyword, [End \<keyword> Statement](end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="7e029-122">例如， `End Function` 結束程式的定義 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="7e029-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e029-123">範例</span><span class="sxs-lookup"><span data-stu-id="7e029-123">Example</span></span>  

 <span data-ttu-id="7e029-124">下列範例 `End` 會使用語句來終止程式碼執行（如果使用者要求的話）。</span><span class="sxs-lookup"><span data-stu-id="7e029-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="7e029-125">智慧型裝置開發人員注意事項</span><span class="sxs-lookup"><span data-stu-id="7e029-125">Smart Device Developer Notes</span></span>  

 <span data-ttu-id="7e029-126">不支援此陳述式。</span><span class="sxs-lookup"><span data-stu-id="7e029-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e029-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e029-127">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [<span data-ttu-id="7e029-128">Stop 陳述式</span><span class="sxs-lookup"><span data-stu-id="7e029-128">Stop Statement</span></span>](stop-statement.md)
- [<span data-ttu-id="7e029-129">End \<keyword> 語句</span><span class="sxs-lookup"><span data-stu-id="7e029-129">End \<keyword> Statement</span></span>](end-keyword-statement.md)
