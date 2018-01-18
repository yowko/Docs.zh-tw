---
title: "LINQ to SQL 中的安全性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0ee361c27bd14f0266b2b86f315f9c091e049c12
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="security-in-linq-to-sql"></a><span data-ttu-id="ab213-102">LINQ to SQL 中的安全性</span><span class="sxs-lookup"><span data-stu-id="ab213-102">Security in LINQ to SQL</span></span>
<span data-ttu-id="ab213-103">當您連接至資料庫時，永遠都會存在安全性風險。</span><span class="sxs-lookup"><span data-stu-id="ab213-103">Security risks are always present when you connect to a database.</span></span> <span data-ttu-id="ab213-104">雖然 LINQ to SQL 可能會包含一些使用 SQL Server 資料的新方式，但是並不會提供任何額外的安全性機制。</span><span class="sxs-lookup"><span data-stu-id="ab213-104">Although LINQ to SQL may include some new ways to work with data in SQL Server, it does not provide any additional security mechanisms.</span></span>  
  
## <a name="access-control-and-authentication"></a><span data-ttu-id="ab213-105">存取控制和驗證</span><span class="sxs-lookup"><span data-stu-id="ab213-105">Access Control and Authentication</span></span>  
 <span data-ttu-id="ab213-106">LINQ to SQL 本身並沒有使用者模型或驗證機制。</span><span class="sxs-lookup"><span data-stu-id="ab213-106">LINQ to SQL does not have its own user model or authentication mechanisms.</span></span> <span data-ttu-id="ab213-107">您可以使用 SQL Server 安全性來控制對應至物件模型 (Object Model) 之資料庫、資料庫資料表、檢視表和預存程序 (Stored Procedure) 的存取權。</span><span class="sxs-lookup"><span data-stu-id="ab213-107">Use SQL Server Security to control access to the database, database tables, views, and stored procedures that are mapped to your object model.</span></span> <span data-ttu-id="ab213-108">請將最低必要存取權授與使用者，並且要求增強式密碼來進行使用者驗證。</span><span class="sxs-lookup"><span data-stu-id="ab213-108">Grant the minimally required access to users and require strong passwords for user authentication.</span></span>  
  
## <a name="mapping-and-schema-information"></a><span data-ttu-id="ab213-109">對應和結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="ab213-109">Mapping and Schema Information</span></span>  
 <span data-ttu-id="ab213-110">物件模型或外部對應檔案中的 SQL-CLR 型別對應和資料庫結構描述資訊可供所有在檔案系統中擁有這些檔案之存取權的使用者使用。</span><span class="sxs-lookup"><span data-stu-id="ab213-110">SQL-CLR type mapping and database schema information in your object model or external mapping file is available for all with access to those files in the file system.</span></span> <span data-ttu-id="ab213-111">假設結構描述資訊可供所有可存取物件模型或外部對應檔案的使用者使用。若要防止其他人對結構描述資訊進行更普遍的存取，請使用檔案安全性機制來保護原始程式檔 (Source File) 和對應檔案的安全。</span><span class="sxs-lookup"><span data-stu-id="ab213-111">Assume that schema information will be available to all who can access the object model or external mapping file.To prevent more widespread access to schema information, use file security mechanisms to secure source files and mapping files.</span></span>  
  
## <a name="connection-strings"></a><span data-ttu-id="ab213-112">連接字串</span><span class="sxs-lookup"><span data-stu-id="ab213-112">Connection Strings</span></span>  
 <span data-ttu-id="ab213-113">請盡可能避免在連接字串中使用密碼。</span><span class="sxs-lookup"><span data-stu-id="ab213-113">Using passwords in connection strings should be avoided whenever possible.</span></span> <span data-ttu-id="ab213-114">不但連接字串本身會產生安全性風險，而且使用物件關聯式設計工具或 SQLMetal 命令列工具時，連接字串可能也會以純文字的方式加入至物件模型或外部對應檔案。</span><span class="sxs-lookup"><span data-stu-id="ab213-114">Not only is a connection string a security risk in its own right, but the connection string may also be added in clear text to the object model or external mapping file when using the Object Relational Designer or SQLMetal command-line tool.</span></span> <span data-ttu-id="ab213-115">可經由檔案系統存取物件模型或外部對應檔案的任何人都可能會看見連接密碼 (如果包含在連接字串中的話)。</span><span class="sxs-lookup"><span data-stu-id="ab213-115">Anyone with access to the object model or external mapping file via the file system could see the connection password (if it is included in the connection string).</span></span>  
  
 <span data-ttu-id="ab213-116">若要將這類風險降到最低，請使用整合式安全性，與 [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] 進行信任連接。</span><span class="sxs-lookup"><span data-stu-id="ab213-116">To minimize such risks, use integrated security to make a trusted connection with [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ab213-117">使用這種方法，就不需要將密碼儲存在連接字串中。</span><span class="sxs-lookup"><span data-stu-id="ab213-117">By using this approach, you do not have to store a password in the connection string.</span></span> <span data-ttu-id="ab213-118">如需詳細資訊，請參閱[SQL Server 安全性](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md)。</span><span class="sxs-lookup"><span data-stu-id="ab213-118">For more information, see [SQL Server Security](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md).</span></span>  
  
 <span data-ttu-id="ab213-119">如果沒有整合式安全性，連接字串將會需要純文字密碼。</span><span class="sxs-lookup"><span data-stu-id="ab213-119">In the absence of integrated security, a clear-text password will be needed in the connection string.</span></span> <span data-ttu-id="ab213-120">協助保護連接字串安全的最佳方法如下所示 (按照風險的遞增順序列出)：</span><span class="sxs-lookup"><span data-stu-id="ab213-120">The best way to help secure your connection string, in increasing order of risk, is as follows:</span></span>  
  
-   <span data-ttu-id="ab213-121">使用整合式安全性。</span><span class="sxs-lookup"><span data-stu-id="ab213-121">Use integrated security.</span></span>  
  
-   <span data-ttu-id="ab213-122">使用密碼來保護連接字串的安全，並且盡可能減少在連接字串前後傳遞密碼。</span><span class="sxs-lookup"><span data-stu-id="ab213-122">Secure connection strings with passwords and minimize passing around connection strings.</span></span>  
  
-   <span data-ttu-id="ab213-123">使用 <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> 類別 (Class) 來取代連接字串，因為它會限制公開的持續期間。</span><span class="sxs-lookup"><span data-stu-id="ab213-123">Use a <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> class instead of a connection string since it limits the duration of exposure.</span></span> <span data-ttu-id="ab213-124">您可以使用 <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> 來具現化 LINQ to SQL <xref:System.Data.SqlClient.SqlConnection> 類別。</span><span class="sxs-lookup"><span data-stu-id="ab213-124">The LINQ to SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> class can be instantiated using a <xref:System.Data.SqlClient.SqlConnection>.</span></span>  
  
-   <span data-ttu-id="ab213-125">盡可能減少所有連接字串的存留期 (Lifetime) 和接觸點。</span><span class="sxs-lookup"><span data-stu-id="ab213-125">Minimize lifetimes and touch points for all connection strings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab213-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="ab213-126">See Also</span></span>  
 [<span data-ttu-id="ab213-127">背景資訊</span><span class="sxs-lookup"><span data-stu-id="ab213-127">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="ab213-128">常見問題集</span><span class="sxs-lookup"><span data-stu-id="ab213-128">Frequently Asked Questions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
