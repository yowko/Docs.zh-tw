---
title: "內容連接"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 40aa71a16c7a0616cfcf318901858da7587fa20b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="the-context-connection"></a><span data-ttu-id="c45e4-102">內容連接</span><span class="sxs-lookup"><span data-stu-id="c45e4-102">The Context Connection</span></span>
<span data-ttu-id="c45e4-103">內部資料存取的問題是很常見的案例。</span><span class="sxs-lookup"><span data-stu-id="c45e4-103">The problem of internal data access is a fairly common scenario.</span></span> <span data-ttu-id="c45e4-104">也就是說，您想要存取執行 Commn Language Runtime (CLR) 預存程序或函式所在的同一部伺服器。</span><span class="sxs-lookup"><span data-stu-id="c45e4-104">That is, you wish to access the same server on which your common language runtime (CLR) stored procedure or function is executing.</span></span> <span data-ttu-id="c45e4-105">有一個選擇是使用 <xref:System.Data.SqlClient.SqlConnection> 建立連接，指定指向本機伺服器的連接字串，並開啟連接。</span><span class="sxs-lookup"><span data-stu-id="c45e4-105">One option is to create a connection using <xref:System.Data.SqlClient.SqlConnection>, specify a connection string that points to the local server, and open the connection.</span></span> <span data-ttu-id="c45e4-106">這需要指定認證以進行登入。</span><span class="sxs-lookup"><span data-stu-id="c45e4-106">This requires specifying credentials for logging in.</span></span> <span data-ttu-id="c45e4-107">連接與預存程序或函式位於不同的資料庫工作階段中，因此可能會具有不同的 `SET` 選項、位於單獨交易中，或是找不到暫存資料表等。</span><span class="sxs-lookup"><span data-stu-id="c45e4-107">The connection is in a different database session than the stored procedure or function, it may have different `SET` options, it is in a separate transaction, it does not see your temporary tables, and so on.</span></span> <span data-ttu-id="c45e4-108">如果 Managed 預存程序或函式程式碼是在 SQL Server 處理序中執行的，則會是因為其他使用者已連接至該伺服器並執行 SQL 陳述式來叫用它。</span><span class="sxs-lookup"><span data-stu-id="c45e4-108">If your managed stored procedure or function code is executing in the SQL Server process, it is because someone connected to that server and executed a SQL statement to invoke it.</span></span> <span data-ttu-id="c45e4-109">您可能會想讓預存程序或函式在該連接的內容及其交易、`SET` 選項等條件中執行。</span><span class="sxs-lookup"><span data-stu-id="c45e4-109">You probably want the stored procedure or function to execute in the context of that connection, along with its transaction, `SET` options, and so on.</span></span> <span data-ttu-id="c45e4-110">這就稱為內容連接。</span><span class="sxs-lookup"><span data-stu-id="c45e4-110">This is called the context connection.</span></span>  
  
 <span data-ttu-id="c45e4-111">內容連接可讓您在第一次叫用程式碼的同一內容中執行 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c45e4-111">The context connection lets you execute Transact-SQL statements in the same context that your code was invoked in the first place.</span></span> <span data-ttu-id="c45e4-112">如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。</span><span class="sxs-lookup"><span data-stu-id="c45e4-112">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="c45e4-113">**SQL Server 線上叢書**</span><span class="sxs-lookup"><span data-stu-id="c45e4-113">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="c45e4-114">內容連線</span><span class="sxs-lookup"><span data-stu-id="c45e4-114">The Context Connection</span></span>](http://go.microsoft.com/fwlink/?LinkId=115395)  
  
## <a name="see-also"></a><span data-ttu-id="c45e4-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="c45e4-115">See Also</span></span>  
 [<span data-ttu-id="c45e4-116">在 Managed 程式碼中建立 SQL Server 2005 物件</span><span class="sxs-lookup"><span data-stu-id="c45e4-116">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="c45e4-117">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="c45e4-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
