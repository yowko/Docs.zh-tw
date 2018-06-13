---
title: 如何：處置系統資源 (Visual Basic)
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
ms.openlocfilehash: cbb66934833da2bd6f0b797944dbb9c4df267cfc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647227"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="cbd43-102">如何：處置系統資源 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbd43-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="cbd43-103">您可以使用`Using`區塊，以確保系統處置資源的程式碼結束該區塊時。</span><span class="sxs-lookup"><span data-stu-id="cbd43-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="cbd43-104">這非常有用，如果您使用，會消耗大量的記憶體，或其他元件也會想要使用的系統資源。</span><span class="sxs-lookup"><span data-stu-id="cbd43-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="cbd43-105">它與您的程式碼完成時處置的資料庫連接</span><span class="sxs-lookup"><span data-stu-id="cbd43-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1.  <span data-ttu-id="cbd43-106">請確定您有適當[Imports 陳述式 （.NET 命名空間和類型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)的原始程式檔開頭的資料庫連接 (在此情況下， <xref:System.Data.SqlClient>)。</span><span class="sxs-lookup"><span data-stu-id="cbd43-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2.  <span data-ttu-id="cbd43-107">建立`Using`區塊`Using`和`End Using`陳述式。</span><span class="sxs-lookup"><span data-stu-id="cbd43-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="cbd43-108">在區塊內，將程式碼處理的資料庫連接。</span><span class="sxs-lookup"><span data-stu-id="cbd43-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3.  <span data-ttu-id="cbd43-109">宣告連接，建立它的執行個體的一部分`Using`陳述式。</span><span class="sxs-lookup"><span data-stu-id="cbd43-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="cbd43-110">系統處置的資源，不論您如何結束區塊中，包括大小寫的未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cbd43-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="cbd43-111">請注意，您無法存取`sqc`從外部`Using`封鎖，因為其範圍僅限於該區塊。</span><span class="sxs-lookup"><span data-stu-id="cbd43-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="cbd43-112">您可以使用這項技術上的系統資源，例如檔案控制代碼或 COM 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="cbd43-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="cbd43-113">您使用`Using`時要先離開資源可供其他元件都結束後，封鎖`Using`區塊。</span><span class="sxs-lookup"><span data-stu-id="cbd43-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbd43-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbd43-114">See Also</span></span>  
 <xref:System.Data.SqlClient.SqlConnection>  
 [<span data-ttu-id="cbd43-115">控制流程</span><span class="sxs-lookup"><span data-stu-id="cbd43-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="cbd43-116">決策結構</span><span class="sxs-lookup"><span data-stu-id="cbd43-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="cbd43-117">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="cbd43-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="cbd43-118">其他控制結構</span><span class="sxs-lookup"><span data-stu-id="cbd43-118">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [<span data-ttu-id="cbd43-119">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="cbd43-119">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="cbd43-120">Using 陳述式</span><span class="sxs-lookup"><span data-stu-id="cbd43-120">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
