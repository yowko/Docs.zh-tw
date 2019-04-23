---
title: 在 SQL Server 中簽署預存程序
ms.date: 01/05/2018
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
ms.openlocfilehash: 2c2076294c0e06ec411ceb1f5b1238dc3d7eb304
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59313914"
---
# <a name="signing-stored-procedures-in-sql-server"></a><span data-ttu-id="1c14b-102">在 SQL Server 中簽署預存程序</span><span class="sxs-lookup"><span data-stu-id="1c14b-102">Signing Stored Procedures in SQL Server</span></span>
 <span data-ttu-id="1c14b-103">數位簽章是指使用簽署者之私密金鑰 (Private Key) 加密的資料摘要。</span><span class="sxs-lookup"><span data-stu-id="1c14b-103">A digital signature is a data digest encrypted with the private key of the signer.</span></span> <span data-ttu-id="1c14b-104">私密金鑰可確保數位簽章對於其 Bearer 或擁有者而言是唯一的。</span><span class="sxs-lookup"><span data-stu-id="1c14b-104">The private key ensures that the digital signature is unique to its bearer or owner.</span></span> <span data-ttu-id="1c14b-105">您可以簽署預存程序、 函式 （除了內嵌資料表值函式）、 觸發程序，以及組件。</span><span class="sxs-lookup"><span data-stu-id="1c14b-105">You can sign stored procedures, functions (except for inline table-valued functions), triggers, and assemblies.</span></span>  
  
 <span data-ttu-id="1c14b-106">您可以使用憑證或非對稱金鑰來簽署預存程序。</span><span class="sxs-lookup"><span data-stu-id="1c14b-106">You can sign a stored procedure with a certificate or an asymmetric key.</span></span> <span data-ttu-id="1c14b-107">這是針對無法透過擁有權鏈結繼承權限或擁有權鏈結中斷 (例如動態 SQL) 的案例所設計。</span><span class="sxs-lookup"><span data-stu-id="1c14b-107">This is designed for scenarios when permissions cannot be inherited through ownership chaining or when the ownership chain is broken, such as dynamic SQL.</span></span> <span data-ttu-id="1c14b-108">然後您可以建立對應至憑證的使用者授與憑證的預存程序需要存取的物件上的使用者權限。</span><span class="sxs-lookup"><span data-stu-id="1c14b-108">You can then create a user mapped to the certificate, granting the certificate user permissions on the objects the stored procedure needs to access.</span></span>  

 <span data-ttu-id="1c14b-109">您可以也建立登入對應到相同的憑證，然後授與任何必要的伺服器層級權限，該登入，或新增的登入一或多個固定的伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="1c14b-109">You can also create a login mapped to the same certificate, and then grant any necessary server-level permissions to that login, or add the login to one or more of the fixed server roles.</span></span> <span data-ttu-id="1c14b-110">這為了避免在`TRUSTWORTHY`資料庫所需較高的層級權限的情況下的設定。</span><span class="sxs-lookup"><span data-stu-id="1c14b-110">This is designed to avoid enabling the `TRUSTWORTHY` database setting for scenarios in which higher level permissions are needed.</span></span>  
  
 <span data-ttu-id="1c14b-111">執行預存程序時，SQL Server 會結合憑證使用者和/或登入的權限與呼叫端。</span><span class="sxs-lookup"><span data-stu-id="1c14b-111">When the stored procedure is executed, SQL Server combines the permissions of the certificate user and/or login with those of the caller.</span></span> <span data-ttu-id="1c14b-112">不同於`EXECUTE AS`子句，它不會變更的程序的執行內容。</span><span class="sxs-lookup"><span data-stu-id="1c14b-112">Unlike the `EXECUTE AS` clause, it does not change the execution context of the procedure.</span></span> <span data-ttu-id="1c14b-113">傳回登入和使用者名稱的內建函式會傳回呼叫端的名稱，而非憑證使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="1c14b-113">Built-in functions that return login and user names return the name of the caller, not the certificate user name.</span></span>  
  
## <a name="creating-certificates"></a><span data-ttu-id="1c14b-114">建立憑證</span><span class="sxs-lookup"><span data-stu-id="1c14b-114">Creating Certificates</span></span>  
 <span data-ttu-id="1c14b-115">當您登入時使用憑證或非對稱金鑰加密的預存程序程式碼，以及執行的雜湊所組成的資料摘要的預存程序-身為使用者，會使用建立的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="1c14b-115">When you sign a stored procedure with a certificate or asymmetric key, a data digest consisting of the encrypted hash of the stored procedure code, along with the execute-as user, is created using the private key.</span></span> <span data-ttu-id="1c14b-116">在執行階段中，系統會使用公開金鑰 (Public Key) 來解密資料摘要，並與預存程序的雜湊值 (Hash Value) 進行比較。</span><span class="sxs-lookup"><span data-stu-id="1c14b-116">At run time, the data digest is decrypted with the public key and compared with the hash value of the stored procedure.</span></span> <span data-ttu-id="1c14b-117">變更 execute-因為使用者會使數位簽章不再相符，導致無效的雜湊值。</span><span class="sxs-lookup"><span data-stu-id="1c14b-117">Changing the execute-as user invalidates the hash value so that the digital signature no longer matches.</span></span> <span data-ttu-id="1c14b-118">修改預存程序會卸除簽章完全，這可防止沒有私密金鑰存取權變更的預存程序程式碼的人。</span><span class="sxs-lookup"><span data-stu-id="1c14b-118">Modifying the stored procedure drops the signature entirely, which prevents someone who does not have access to the private key from changing the stored procedure code.</span></span> <span data-ttu-id="1c14b-119">在任一情況下，您必須重新簽署程序每次變更的程式碼或 execute-以使用者身分。</span><span class="sxs-lookup"><span data-stu-id="1c14b-119">In either case, you must re-sign the procedure each time you change the code or the execute-as user.</span></span>  
  
 <span data-ttu-id="1c14b-120">簽署模組是兩個所需的步驟：</span><span class="sxs-lookup"><span data-stu-id="1c14b-120">There are two required steps involved in signing a module:</span></span>  
  
1. <span data-ttu-id="1c14b-121">使用 Transact-SQL `CREATE CERTIFICATE [certificateName]` 陳述式來建立憑證。</span><span class="sxs-lookup"><span data-stu-id="1c14b-121">Create a certificate using the Transact-SQL `CREATE CERTIFICATE [certificateName]` statement.</span></span> <span data-ttu-id="1c14b-122">這個陳述式具有許多設定開始和結束日期與密碼的選項。</span><span class="sxs-lookup"><span data-stu-id="1c14b-122">This statement has several options for setting a start and end date and a password.</span></span> <span data-ttu-id="1c14b-123">預設的到期日是一年。</span><span class="sxs-lookup"><span data-stu-id="1c14b-123">The default expiration date is one year.</span></span>  
  
1. <span data-ttu-id="1c14b-124">使用 Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` 陳述式並搭配憑證來簽署程序。</span><span class="sxs-lookup"><span data-stu-id="1c14b-124">Sign the procedure with the certificate using the Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` statement.</span></span>  

<span data-ttu-id="1c14b-125">一旦已簽署的模組，一或多個主體，就必須建立以便保存應與憑證相關聯的額外權限。</span><span class="sxs-lookup"><span data-stu-id="1c14b-125">Once the module has been signed, one or more principals needs to be created in order to hold the additional permissions that should be associated with the certificate.</span></span>  

<span data-ttu-id="1c14b-126">如果此模組需要額外的資料庫層級權限：</span><span class="sxs-lookup"><span data-stu-id="1c14b-126">If the module needs additional database-level permissions:</span></span>  
  
1. <span data-ttu-id="1c14b-127">使用 Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` 陳述式來建立與憑證相關聯的資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="1c14b-127">Create a database user associated with that certificate using the Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` statement.</span></span> <span data-ttu-id="1c14b-128">這位使用者只會在資料庫中存在，而且不與登入相關聯，除非也從相同的憑證建立登入。</span><span class="sxs-lookup"><span data-stu-id="1c14b-128">This user exists in the database only and is not associated with a login unless a login has also been created from that same certificate.</span></span>  
  
1. <span data-ttu-id="1c14b-129">授與憑證使用者必要的資料庫層級權限。</span><span class="sxs-lookup"><span data-stu-id="1c14b-129">Grant the certificate user the required database-level permissions.</span></span>  
  
<span data-ttu-id="1c14b-130">如果此模組需要額外的伺服器層級權限：</span><span class="sxs-lookup"><span data-stu-id="1c14b-130">If the module needs additional server-level permissions:</span></span>  
  
1. <span data-ttu-id="1c14b-131">若要將憑證複製`master`資料庫。</span><span class="sxs-lookup"><span data-stu-id="1c14b-131">Copy the certificate to the `master` database.</span></span>  
 
1. <span data-ttu-id="1c14b-132">建立與使用 TRANSACT-SQL 該憑證相關聯的登入`CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]`陳述式。</span><span class="sxs-lookup"><span data-stu-id="1c14b-132">Create a login associated with that certificate using the Transact-SQL `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]` statement.</span></span>  
  
1. <span data-ttu-id="1c14b-133">授與憑證登入需要的伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="1c14b-133">Grant the certificate login the required server-level permissions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1c14b-134">憑證無法授與權限給擁有使用 DENY 陳述式撤銷之權限的使用者。</span><span class="sxs-lookup"><span data-stu-id="1c14b-134">A certificate cannot grant permissions to a user that has had permissions revoked using the DENY statement.</span></span> <span data-ttu-id="1c14b-135">DENY 的優先順序永遠高於 GRANT，可防止呼叫端繼承授與憑證使用者的權限。</span><span class="sxs-lookup"><span data-stu-id="1c14b-135">DENY always takes precedence over GRANT, preventing the caller from inheriting permissions granted to the certificate user.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="1c14b-136">外部資源</span><span class="sxs-lookup"><span data-stu-id="1c14b-136">External Resources</span></span>  
 <span data-ttu-id="1c14b-137">如需詳細資訊，請參閱下列資源。</span><span class="sxs-lookup"><span data-stu-id="1c14b-137">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="1c14b-138">資源</span><span class="sxs-lookup"><span data-stu-id="1c14b-138">Resource</span></span>|<span data-ttu-id="1c14b-139">描述</span><span class="sxs-lookup"><span data-stu-id="1c14b-139">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="1c14b-140">[模組簽署](https://go.microsoft.com/fwlink/?LinkId=98590)中 SQL Server 線上叢書</span><span class="sxs-lookup"><span data-stu-id="1c14b-140">[Module Signing](https://go.microsoft.com/fwlink/?LinkId=98590) in SQL Server Books Online</span></span>|<span data-ttu-id="1c14b-141">說明模組簽署，並提供範例案例以及相關 Transact-SQL 主題的連結。</span><span class="sxs-lookup"><span data-stu-id="1c14b-141">Describes module signing, providing a sample scenario and links to the relevant Transact-SQL topics.</span></span>|  
|<span data-ttu-id="1c14b-142">[簽署憑證的預存程序](/sql/relational-databases/tutorial-signing-stored-procedures-with-a-certificate)中 SQL Server 線上叢書</span><span class="sxs-lookup"><span data-stu-id="1c14b-142">[Signing Stored Procedures with a Certificate](/sql/relational-databases/tutorial-signing-stored-procedures-with-a-certificate) in SQL Server Books Online</span></span>|<span data-ttu-id="1c14b-143">提供使用憑證來簽署預存程序的教學課程。</span><span class="sxs-lookup"><span data-stu-id="1c14b-143">Provides a tutorial for signing a stored procedure with a certificate.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c14b-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c14b-144">See also</span></span>

- [<span data-ttu-id="1c14b-145">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="1c14b-145">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [<span data-ttu-id="1c14b-146">SQL Server 安全性概觀</span><span class="sxs-lookup"><span data-stu-id="1c14b-146">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [<span data-ttu-id="1c14b-147">SQL Server 中的應用程式安全性案例</span><span class="sxs-lookup"><span data-stu-id="1c14b-147">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="1c14b-148">在 SQL Server 中使用預存程序來管理權限</span><span class="sxs-lookup"><span data-stu-id="1c14b-148">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="1c14b-149">在 SQL Server 中撰寫安全的動態 SQL</span><span class="sxs-lookup"><span data-stu-id="1c14b-149">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="1c14b-150">在 SQL Server 中使用模擬來自訂權限</span><span class="sxs-lookup"><span data-stu-id="1c14b-150">Customizing Permissions with Impersonation in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)
- [<span data-ttu-id="1c14b-151">使用預存程序修改資料</span><span class="sxs-lookup"><span data-stu-id="1c14b-151">Modifying Data with Stored Procedures</span></span>](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="1c14b-152">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="1c14b-152">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
