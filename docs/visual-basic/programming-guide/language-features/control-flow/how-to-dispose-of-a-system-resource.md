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
ms.openlocfilehash: dd15c6746628f45b072d46eea40051ed9afb7921
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403494"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="1819a-102">如何：處置系統資源 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1819a-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="1819a-103">您可以使用 `Using` 區塊，確保當您的程式碼結束區塊時，系統會處置資源。</span><span class="sxs-lookup"><span data-stu-id="1819a-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="1819a-104">如果您使用的系統資源會耗用大量的記憶體，或其他元件也想要使用，這就很有用。</span><span class="sxs-lookup"><span data-stu-id="1819a-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="1819a-105">若要在程式碼完成時處置資料庫連接</span><span class="sxs-lookup"><span data-stu-id="1819a-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1. <span data-ttu-id="1819a-106">請確定您在來源檔案的開頭包含資料庫連接的適當[Imports 語句（.Net 命名空間和類型）](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) （在此案例中為 <xref:System.Data.SqlClient> ）。</span><span class="sxs-lookup"><span data-stu-id="1819a-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2. <span data-ttu-id="1819a-107">`Using`使用和語句建立區塊 `Using` `End Using` 。</span><span class="sxs-lookup"><span data-stu-id="1819a-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="1819a-108">在區塊內，放入處理資料庫連接的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1819a-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3. <span data-ttu-id="1819a-109">宣告連接，並建立它的實例作為語句的一部分 `Using` 。</span><span class="sxs-lookup"><span data-stu-id="1819a-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="1819a-110">無論您如何結束區塊，系統都會處置資源，包括未處理之例外狀況的情況。</span><span class="sxs-lookup"><span data-stu-id="1819a-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="1819a-111">請注意，您無法 `sqc` 從區塊外部存取 `Using` ，因為它的範圍限制為區塊。</span><span class="sxs-lookup"><span data-stu-id="1819a-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="1819a-112">您可以在系統資源（例如檔案控制代碼或 COM 包裝函式）上使用這項相同的技術。</span><span class="sxs-lookup"><span data-stu-id="1819a-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="1819a-113">當您想要在 `Using` 結束區塊之後讓其他元件有可用的資源時，請使用區塊 `Using` 。</span><span class="sxs-lookup"><span data-stu-id="1819a-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1819a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1819a-114">See also</span></span>

- <xref:System.Data.SqlClient.SqlConnection>
- [<span data-ttu-id="1819a-115">控制流程</span><span class="sxs-lookup"><span data-stu-id="1819a-115">Control Flow</span></span>](index.md)
- [<span data-ttu-id="1819a-116">決策結構</span><span class="sxs-lookup"><span data-stu-id="1819a-116">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="1819a-117">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="1819a-117">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="1819a-118">其他控制結構</span><span class="sxs-lookup"><span data-stu-id="1819a-118">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="1819a-119">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="1819a-119">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="1819a-120">Using 語句</span><span class="sxs-lookup"><span data-stu-id="1819a-120">Using Statement</span></span>](../../../language-reference/statements/using-statement.md)
