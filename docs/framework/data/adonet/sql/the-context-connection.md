---
title: 內容連接
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: 83e9f4a9672d2703514c0a86ad8d41b968c255fd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343437"
---
# <a name="the-context-connection"></a><span data-ttu-id="da65f-102">內容連接</span><span class="sxs-lookup"><span data-stu-id="da65f-102">The Context Connection</span></span>
<span data-ttu-id="da65f-103">內部資料存取的問題是很常見的案例。</span><span class="sxs-lookup"><span data-stu-id="da65f-103">The problem of internal data access is a fairly common scenario.</span></span> <span data-ttu-id="da65f-104">也就是說，您想要存取執行 Commn Language Runtime (CLR) 預存程序或函式所在的同一部伺服器。</span><span class="sxs-lookup"><span data-stu-id="da65f-104">That is, you wish to access the same server on which your common language runtime (CLR) stored procedure or function is executing.</span></span> <span data-ttu-id="da65f-105">有一個選擇是使用 <xref:System.Data.SqlClient.SqlConnection> 建立連接，指定指向本機伺服器的連接字串，並開啟連接。</span><span class="sxs-lookup"><span data-stu-id="da65f-105">One option is to create a connection using <xref:System.Data.SqlClient.SqlConnection>, specify a connection string that points to the local server, and open the connection.</span></span> <span data-ttu-id="da65f-106">這需要指定認證以進行登入。</span><span class="sxs-lookup"><span data-stu-id="da65f-106">This requires specifying credentials for logging in.</span></span> <span data-ttu-id="da65f-107">連接與預存程序或函式位於不同的資料庫工作階段中，因此可能會具有不同的 `SET` 選項、位於單獨異動中，或是找不到暫存資料表等。</span><span class="sxs-lookup"><span data-stu-id="da65f-107">The connection is in a different database session than the stored procedure or function, it may have different `SET` options, it is in a separate transaction, it does not see your temporary tables, and so on.</span></span> <span data-ttu-id="da65f-108">如果 Managed 預存程序或函式程式碼是在 SQL Server 處理序中執行的，則會是因為其他使用者已連接至該伺服器並執行 SQL 陳述式來叫用它。</span><span class="sxs-lookup"><span data-stu-id="da65f-108">If your managed stored procedure or function code is executing in the SQL Server process, it is because someone connected to that server and executed a SQL statement to invoke it.</span></span> <span data-ttu-id="da65f-109">您可能會想讓預存程序或函式在該連接的內容及其異動、`SET` 選項等條件中執行。</span><span class="sxs-lookup"><span data-stu-id="da65f-109">You probably want the stored procedure or function to execute in the context of that connection, along with its transaction, `SET` options, and so on.</span></span> <span data-ttu-id="da65f-110">這就稱為內容連接。</span><span class="sxs-lookup"><span data-stu-id="da65f-110">This is called the context connection.</span></span>  
  
 <span data-ttu-id="da65f-111">內容連接可讓您在第一次叫用程式碼的同一內容中執行 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="da65f-111">The context connection lets you execute Transact-SQL statements in the same context that your code was invoked in the first place.</span></span> <span data-ttu-id="da65f-112">如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。</span><span class="sxs-lookup"><span data-stu-id="da65f-112">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 **<span data-ttu-id="da65f-113">SQL Server 線上叢書</span><span class="sxs-lookup"><span data-stu-id="da65f-113">SQL Server Books Online</span></span>**  
  
1. [<span data-ttu-id="da65f-114">內容連接</span><span class="sxs-lookup"><span data-stu-id="da65f-114">The Context Connection</span></span>](https://go.microsoft.com/fwlink/?LinkId=115395)  
  
## <a name="see-also"></a><span data-ttu-id="da65f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da65f-115">See also</span></span>

- [<span data-ttu-id="da65f-116">ADO.NET Managed 提供者和DataSet開發人員中心</span><span class="sxs-lookup"><span data-stu-id="da65f-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
