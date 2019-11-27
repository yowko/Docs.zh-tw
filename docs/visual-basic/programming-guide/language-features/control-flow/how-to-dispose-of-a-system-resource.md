---
title: 如何：處置系統資源
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: c493051050442597196ba484fb9ce8e99249dbb7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353950"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="25c6e-102">如何：處置系統資源 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25c6e-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="25c6e-103">您可以使用 `Using` 區塊，確保當您的程式碼結束區塊時，系統會處置資源。</span><span class="sxs-lookup"><span data-stu-id="25c6e-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="25c6e-104">如果您使用的系統資源會耗用大量的記憶體，或其他元件也想要使用，這就很有用。</span><span class="sxs-lookup"><span data-stu-id="25c6e-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="25c6e-105">若要在程式碼完成時處置資料庫連接</span><span class="sxs-lookup"><span data-stu-id="25c6e-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1. <span data-ttu-id="25c6e-106">請確定您在來源檔案的開頭包含資料庫連接的適當[Imports 語句（.Net 命名空間和類型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) （在此案例中為 <xref:System.Data.SqlClient>）。</span><span class="sxs-lookup"><span data-stu-id="25c6e-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2. <span data-ttu-id="25c6e-107">使用 `Using` 和 `End Using` 語句來建立 `Using` 區塊。</span><span class="sxs-lookup"><span data-stu-id="25c6e-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="25c6e-108">在區塊內，放入處理資料庫連接的程式碼。</span><span class="sxs-lookup"><span data-stu-id="25c6e-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3. <span data-ttu-id="25c6e-109">宣告連接，並建立它的實例做為 `Using` 語句的一部分。</span><span class="sxs-lookup"><span data-stu-id="25c6e-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="25c6e-110">無論您如何結束區塊，系統都會處置資源，包括未處理之例外狀況的情況。</span><span class="sxs-lookup"><span data-stu-id="25c6e-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="25c6e-111">請注意，您無法從 `Using` 區塊外部存取 `sqc`，因為它的範圍限制為區塊。</span><span class="sxs-lookup"><span data-stu-id="25c6e-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="25c6e-112">您可以在系統資源（例如檔案控制代碼或 COM 包裝函式）上使用這項相同的技術。</span><span class="sxs-lookup"><span data-stu-id="25c6e-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="25c6e-113">當您想要在結束 [`Using`] 區塊之後，保留其他元件的可用資源時，請使用 `Using` 區塊。</span><span class="sxs-lookup"><span data-stu-id="25c6e-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25c6e-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="25c6e-114">See also</span></span>

- <xref:System.Data.SqlClient.SqlConnection>
- [<span data-ttu-id="25c6e-115">控制流程</span><span class="sxs-lookup"><span data-stu-id="25c6e-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="25c6e-116">決策結構</span><span class="sxs-lookup"><span data-stu-id="25c6e-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="25c6e-117">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="25c6e-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="25c6e-118">其他控制結構</span><span class="sxs-lookup"><span data-stu-id="25c6e-118">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="25c6e-119">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="25c6e-119">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="25c6e-120">Using 陳述式</span><span class="sxs-lookup"><span data-stu-id="25c6e-120">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
