---
title: "在 SQL Server 中簽署預存程序"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b3d90579e28fde40d461bdb511d797e5d7f6f179
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="signing-stored-procedures-in-sql-server"></a><span data-ttu-id="cd7de-102">在 SQL Server 中簽署預存程序</span><span class="sxs-lookup"><span data-stu-id="cd7de-102">Signing Stored Procedures in SQL Server</span></span>
<span data-ttu-id="cd7de-103">您可以使用憑證或非對稱金鑰來簽署預存程序。</span><span class="sxs-lookup"><span data-stu-id="cd7de-103">You can sign a stored procedure with a certificate or an asymmetric key.</span></span> <span data-ttu-id="cd7de-104">這是針對無法透過擁有權鏈結繼承權限或擁有權鏈結中斷 (例如動態 SQL) 的案例所設計。</span><span class="sxs-lookup"><span data-stu-id="cd7de-104">This is designed for scenarios when permissions cannot be inherited through ownership chaining or when the ownership chain is broken, such as dynamic SQL.</span></span> <span data-ttu-id="cd7de-105">然後，您可以建立對應至憑證的使用者，並授與該預存程序需要存取之物件的權限給憑證使用者。</span><span class="sxs-lookup"><span data-stu-id="cd7de-105">You then create a user mapped to the certificate, granting the certificate user permissions on the objects the stored procedure needs to access.</span></span>  
  
 <span data-ttu-id="cd7de-106">執行此預存程序時，SQL Server 會結合憑證使用者的權限與呼叫端的權限。</span><span class="sxs-lookup"><span data-stu-id="cd7de-106">When the stored procedure is executed, SQL Server combines the permissions of the certificate user with those of the caller.</span></span> <span data-ttu-id="cd7de-107">與 EXECUTE AS 子句不同的是，它不會變更程序的執行內容。</span><span class="sxs-lookup"><span data-stu-id="cd7de-107">Unlike the EXECUTE AS clause, it does not change the execution context of the procedure.</span></span> <span data-ttu-id="cd7de-108">傳回登入和使用者名稱的內建函式會傳回呼叫端的名稱，而非憑證使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="cd7de-108">Built-in functions that return login and user names return the name of the caller, not the certificate user name.</span></span>  
  
 <span data-ttu-id="cd7de-109">數位簽章是指使用簽署者之私密金鑰 (Private Key) 加密的資料摘要。</span><span class="sxs-lookup"><span data-stu-id="cd7de-109">A digital signature is a data digest encrypted with the private key of the signer.</span></span> <span data-ttu-id="cd7de-110">私密金鑰可確保數位簽章對於其 Bearer 或擁有者而言是唯一的。</span><span class="sxs-lookup"><span data-stu-id="cd7de-110">The private key ensures that the digital signature is unique to its bearer or owner.</span></span> <span data-ttu-id="cd7de-111">您可以簽署預存程序、函式或觸發程序 (Trigger)。</span><span class="sxs-lookup"><span data-stu-id="cd7de-111">You can sign stored procedures, functions, or triggers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd7de-112">您可以在 master 資料庫中建立憑證，以便授與伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="cd7de-112">You can create a certificate in the master database to grant server-level permissions.</span></span>  
  
## <a name="creating-certificates"></a><span data-ttu-id="cd7de-113">建立憑證</span><span class="sxs-lookup"><span data-stu-id="cd7de-113">Creating Certificates</span></span>  
 <span data-ttu-id="cd7de-114">當您使用憑證來簽署預存程序時，系統會使用私密金鑰來建立資料摘要，其中包含預存程序程式碼的加密雜湊。</span><span class="sxs-lookup"><span data-stu-id="cd7de-114">When you sign a stored procedure with a certificate, a data digest consisting of the encrypted hash of the stored procedure code is created using the private key.</span></span> <span data-ttu-id="cd7de-115">在執行階段中，系統會使用公開金鑰 (Public Key) 來解密資料摘要，並與預存程序的雜湊值 (Hash Value) 進行比較。</span><span class="sxs-lookup"><span data-stu-id="cd7de-115">At run time, the data digest is decrypted with the public key and compared with the hash value of the stored procedure.</span></span> <span data-ttu-id="cd7de-116">修改預存程序會讓雜湊值無效，因而導致數位簽章不再相符。</span><span class="sxs-lookup"><span data-stu-id="cd7de-116">Modifying the stored procedure invalidates the hash value so that the digital signature no longer matches.</span></span> <span data-ttu-id="cd7de-117">這樣做可防止沒有私密金鑰存取權的人員變更預存程序程式碼。</span><span class="sxs-lookup"><span data-stu-id="cd7de-117">This prevents someone who does not have access to the private key from changing the stored procedure code.</span></span> <span data-ttu-id="cd7de-118">因此，每次修改程序時，您就必須重新簽署程序。</span><span class="sxs-lookup"><span data-stu-id="cd7de-118">Therefore you must re-sign the procedure each time you modify it.</span></span>  
  
 <span data-ttu-id="cd7de-119">簽署模組包含四個步驟：</span><span class="sxs-lookup"><span data-stu-id="cd7de-119">There are four steps involved in signing a module:</span></span>  
  
1.  <span data-ttu-id="cd7de-120">使用 Transact-SQL `CREATE CERTIFICATE [certificateName]` 陳述式來建立憑證。</span><span class="sxs-lookup"><span data-stu-id="cd7de-120">Create a certificate using the Transact-SQL `CREATE CERTIFICATE [certificateName]` statement.</span></span> <span data-ttu-id="cd7de-121">這個陳述式具有許多設定開始和結束日期與密碼的選項。</span><span class="sxs-lookup"><span data-stu-id="cd7de-121">This statement has several options for setting a start and end date and a password.</span></span> <span data-ttu-id="cd7de-122">預設的到期日是一年。</span><span class="sxs-lookup"><span data-stu-id="cd7de-122">The default expiration date is one year</span></span>  
  
2.  <span data-ttu-id="cd7de-123">使用 Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` 陳述式來建立與憑證相關聯的資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="cd7de-123">Create a database user associated with that certificate using the Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` statement.</span></span> <span data-ttu-id="cd7de-124">這位使用者僅存在資料庫中，而且與登入沒有任何關聯。</span><span class="sxs-lookup"><span data-stu-id="cd7de-124">This user exists in the database only and is not associated with a login.</span></span>  
  
3.  <span data-ttu-id="cd7de-125">授與資料庫物件的必要權限給憑證使用者。</span><span class="sxs-lookup"><span data-stu-id="cd7de-125">Grant the certificate user the required permissions on the database objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd7de-126">憑證無法授與權限給擁有使用 DENY 陳述式撤銷之權限的使用者。</span><span class="sxs-lookup"><span data-stu-id="cd7de-126">A certificate cannot grant permissions to a user that has had permissions revoked using the DENY statement.</span></span> <span data-ttu-id="cd7de-127">DENY 的優先順序永遠高於 GRANT，可防止呼叫端繼承授與憑證使用者的權限。</span><span class="sxs-lookup"><span data-stu-id="cd7de-127">DENY always takes precedence over GRANT, preventing the caller from inheriting permissions granted to the certificate user.</span></span>  
  
1.  <span data-ttu-id="cd7de-128">使用 Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` 陳述式並搭配憑證來簽署程序。</span><span class="sxs-lookup"><span data-stu-id="cd7de-128">Sign the procedure with the certificate using the Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` statement.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="cd7de-129">外部資源</span><span class="sxs-lookup"><span data-stu-id="cd7de-129">External Resources</span></span>  
 <span data-ttu-id="cd7de-130">如需詳細資訊，請參閱下列資源。</span><span class="sxs-lookup"><span data-stu-id="cd7de-130">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="cd7de-131">資源</span><span class="sxs-lookup"><span data-stu-id="cd7de-131">Resource</span></span>|<span data-ttu-id="cd7de-132">描述</span><span class="sxs-lookup"><span data-stu-id="cd7de-132">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="cd7de-133">[模組簽署](http://go.microsoft.com/fwlink/?LinkId=98590)SQL Server 線上叢書中</span><span class="sxs-lookup"><span data-stu-id="cd7de-133">[Module Signing](http://go.microsoft.com/fwlink/?LinkId=98590) in SQL Server Books Online</span></span>|<span data-ttu-id="cd7de-134">說明模組簽署，並提供範例案例以及相關 Transact-SQL 主題的連結。</span><span class="sxs-lookup"><span data-stu-id="cd7de-134">Describes module signing, providing a sample scenario and links to the relevant Transact-SQL topics.</span></span>|  
|<span data-ttu-id="cd7de-135">[簽署憑證的預存程序](http://msdn.microsoft.com/library/bb283630.aspx)SQL Server 線上叢書中</span><span class="sxs-lookup"><span data-stu-id="cd7de-135">[Signing Stored Procedures with a Certificate](http://msdn.microsoft.com/library/bb283630.aspx) in SQL Server Books Online</span></span>|<span data-ttu-id="cd7de-136">提供使用憑證來簽署預存程序的教學課程。</span><span class="sxs-lookup"><span data-stu-id="cd7de-136">Provides a tutorial for signing a stored procedure with a certificate.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd7de-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="cd7de-137">See Also</span></span>  
 [<span data-ttu-id="cd7de-138">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="cd7de-138">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="cd7de-139">SQL Server 安全性概觀</span><span class="sxs-lookup"><span data-stu-id="cd7de-139">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="cd7de-140">SQL Server 中的應用程式安全性案例</span><span class="sxs-lookup"><span data-stu-id="cd7de-140">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="cd7de-141">在 SQL Server 中使用預存程序來管理權限</span><span class="sxs-lookup"><span data-stu-id="cd7de-141">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="cd7de-142">在 SQL Server 中撰寫安全的動態 SQL</span><span class="sxs-lookup"><span data-stu-id="cd7de-142">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [<span data-ttu-id="cd7de-143">在 SQL Server 中使用模擬來自訂權限</span><span class="sxs-lookup"><span data-stu-id="cd7de-143">Customizing Permissions with Impersonation in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [<span data-ttu-id="cd7de-144">使用預存程序修改資料</span><span class="sxs-lookup"><span data-stu-id="cd7de-144">Modifying Data with Stored Procedures</span></span>](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [<span data-ttu-id="cd7de-145">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="cd7de-145">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
