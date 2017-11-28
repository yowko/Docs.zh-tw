---
title: "在 SQL Server 中撰寫安全的動態 SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 926794f4bb603548b74dd95fd9040d9471d70a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a><span data-ttu-id="5eca6-102">在 SQL Server 中撰寫安全的動態 SQL</span><span class="sxs-lookup"><span data-stu-id="5eca6-102">Writing Secure Dynamic SQL in SQL Server</span></span>
<span data-ttu-id="5eca6-103">「SQL 插入」(SQL Injection) 是指惡意的使用者用來輸入 Transact-SQL 陳述式 (而非有效輸入) 的流程。</span><span class="sxs-lookup"><span data-stu-id="5eca6-103">SQL Injection is the process by which a malicious user enters Transact-SQL statements instead of valid input.</span></span> <span data-ttu-id="5eca6-104">如果該輸入未經驗證而直接傳遞至伺服器，而且應用程式不慎執行了插入的程式碼，則攻擊就可能會危及或損毀資料。</span><span class="sxs-lookup"><span data-stu-id="5eca6-104">If the input is passed directly to the server without being validated and if the application inadvertently executes the injected code, the attack has the potential to damage or destroy data.</span></span>  
  
 <span data-ttu-id="5eca6-105">您應該檢閱建構 SQL 陳述式的任何程序是否有插入弱點，因為 SQL Server 將會執行所有它收到的語法有效查詢。</span><span class="sxs-lookup"><span data-stu-id="5eca6-105">Any procedure that constructs SQL statements should be reviewed for injection vulnerabilities because SQL Server will execute all syntactically valid queries that it receives.</span></span> <span data-ttu-id="5eca6-106">即使是參數化的資料也可能會被富有技巧且果決的攻擊者所操作。</span><span class="sxs-lookup"><span data-stu-id="5eca6-106">Even parameterized data can be manipulated by a skilled and determined attacker.</span></span> <span data-ttu-id="5eca6-107">如果有使用動態 SQL，請務必將命令參數化，也絕對不要在查詢字串中直接包含參數值。</span><span class="sxs-lookup"><span data-stu-id="5eca6-107">If you use dynamic SQL, be sure to parameterize your commands, and never include parameter values directly into the query string.</span></span>  
  
## <a name="anatomy-of-a-sql-injection-attack"></a><span data-ttu-id="5eca6-108">SQL 插入式攻擊的分析</span><span class="sxs-lookup"><span data-stu-id="5eca6-108">Anatomy of a SQL Injection Attack</span></span>  
 <span data-ttu-id="5eca6-109">插入程序的運作方式是不當地結束文字字串並附加新的命令。</span><span class="sxs-lookup"><span data-stu-id="5eca6-109">The injection process works by prematurely terminating a text string and appending a new command.</span></span> <span data-ttu-id="5eca6-110">由於插入的命令可能會在執行之前附加其他字串，因此攻擊者會使用註解標記 "--" 來結束插入的字串。</span><span class="sxs-lookup"><span data-stu-id="5eca6-110">Because the inserted command may have additional strings appended to it before it is executed, the malefactor terminates the injected string with a comment mark "--".</span></span> <span data-ttu-id="5eca6-111">如此一來，系統會在執行時忽略後續文字。</span><span class="sxs-lookup"><span data-stu-id="5eca6-111">Subsequent text is ignored at execution time.</span></span> <span data-ttu-id="5eca6-112">攻擊者可能會使用分號 (;) 分隔符號 (Delimiter) 來插入多個命令。</span><span class="sxs-lookup"><span data-stu-id="5eca6-112">Multiple commands can be inserted using a semicolon (;) delimiter.</span></span>  
  
 <span data-ttu-id="5eca6-113">只要插入的 SQL 程式碼語法正確，您就無法以程式設計方式來偵測出是否遭竄改。</span><span class="sxs-lookup"><span data-stu-id="5eca6-113">As long as injected SQL code is syntactically correct, tampering cannot be detected programmatically.</span></span> <span data-ttu-id="5eca6-114">因此，您必須驗證所有使用者輸入並仔細地檢閱在您目前使用之伺服器上執行建構 SQL 命令的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5eca6-114">Therefore, you must validate all user input and carefully review code that executes constructed SQL commands in the server that you are using.</span></span> <span data-ttu-id="5eca6-115">絕對不要串連未經驗證的使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="5eca6-115">Never concatenate user input that is not validated.</span></span> <span data-ttu-id="5eca6-116">字串串連是指令碼攻擊的主要進入點。</span><span class="sxs-lookup"><span data-stu-id="5eca6-116">String concatenation is the primary point of entry for script injection.</span></span>  
  
 <span data-ttu-id="5eca6-117">下面是一些有用的方針：</span><span class="sxs-lookup"><span data-stu-id="5eca6-117">Here are some helpful guidelines:</span></span>  
  
-   <span data-ttu-id="5eca6-118">絕對不要直接根據使用者輸入來建立 Transact-SQL 陳述式，請使用預存程序 (Stored Procedure) 來驗證使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="5eca6-118">Never build Transact-SQL statements directly from user input; use stored procedures to validate user input.</span></span>  
  
-   <span data-ttu-id="5eca6-119">透過測試型別、長度、格式和範圍，驗證使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="5eca6-119">Validate user input by testing type, length, format, and range.</span></span> <span data-ttu-id="5eca6-120">請使用 Transact-SQL QUOTENAME() 函式來逸出系統名稱或使用 REPLACE() 函式來逸出字串中的任何字元。</span><span class="sxs-lookup"><span data-stu-id="5eca6-120">Use the Transact-SQL QUOTENAME() function to escape system names or the REPLACE() function to escape any character in a string.</span></span>  
  
-   <span data-ttu-id="5eca6-121">在每個應用程式層中實作多個驗證層。</span><span class="sxs-lookup"><span data-stu-id="5eca6-121">Implement multiple layers of validation in each tier of your application.</span></span>  
  
-   <span data-ttu-id="5eca6-122">測試輸入的大小和資料型別並強制執行適當的限制。</span><span class="sxs-lookup"><span data-stu-id="5eca6-122">Test the size and data type of input and enforce appropriate limits.</span></span> <span data-ttu-id="5eca6-123">這樣做有助於防止故意的緩衝區滿溢。</span><span class="sxs-lookup"><span data-stu-id="5eca6-123">This can help prevent deliberate buffer overruns.</span></span>  
  
-   <span data-ttu-id="5eca6-124">測試字串變數的內容並僅接受預期的值。</span><span class="sxs-lookup"><span data-stu-id="5eca6-124">Test the content of string variables and accept only expected values.</span></span> <span data-ttu-id="5eca6-125">請拒絕包含二進位資料、逸出序列 (Escape Sequence) 和註解字元的項目。</span><span class="sxs-lookup"><span data-stu-id="5eca6-125">Reject entries that contain binary data, escape sequences, and comment characters.</span></span>  
  
-   <span data-ttu-id="5eca6-126">如果您要使用 XML 文件，請在資料進入時，針對結構描述來驗證所有資料。</span><span class="sxs-lookup"><span data-stu-id="5eca6-126">When you are working with XML documents, validate all data against its schema as it is entered.</span></span>  
  
-   <span data-ttu-id="5eca6-127">在多層環境中，所有資料都應該先進行驗證，然後才能進入受信任的區域。</span><span class="sxs-lookup"><span data-stu-id="5eca6-127">In multi-tiered environments, all data should be validated before admission to the trusted zone.</span></span>  
  
-   <span data-ttu-id="5eca6-128">在可用以建構檔案名稱的欄位中，不接受下列字串：AUX、CLOCK$、COM1 到 COM8、CON、CONFIG$、LPT1 到 LPT8、NUL 和 PRN。</span><span class="sxs-lookup"><span data-stu-id="5eca6-128">Do not accept the following strings in fields from which file names can be constructed: AUX, CLOCK$, COM1 through COM8, CON, CONFIG$, LPT1 through LPT8, NUL, and PRN.</span></span>  
  
-   <span data-ttu-id="5eca6-129">請使用 <xref:System.Data.SqlClient.SqlParameter> 物件搭配預存程序和命令來提供型別檢查 (Type Checking) 和長度驗證。</span><span class="sxs-lookup"><span data-stu-id="5eca6-129">Use <xref:System.Data.SqlClient.SqlParameter> objects with stored procedures and commands to provide type checking and length validation.</span></span>  
  
-   <span data-ttu-id="5eca6-130">請在用戶端程式碼中使用 <xref:System.Text.RegularExpressions.Regex> 運算式來篩選無效的字元。</span><span class="sxs-lookup"><span data-stu-id="5eca6-130">Use <xref:System.Text.RegularExpressions.Regex> expressions in client code to filter invalid characters.</span></span>  
  
## <a name="dynamic-sql-strategies"></a><span data-ttu-id="5eca6-131">動態 SQL 策略</span><span class="sxs-lookup"><span data-stu-id="5eca6-131">Dynamic SQL Strategies</span></span>  
 <span data-ttu-id="5eca6-132">在程序性程式碼中執行動態建立的 SQL 陳述式會中斷擁有權鏈結，進而導致 SQL Server 針對動態 SQL 所存取的物件，檢查呼叫端的權限。</span><span class="sxs-lookup"><span data-stu-id="5eca6-132">Executing dynamically created SQL statements in your procedural code breaks the ownership chain, causing SQL Server to check the permissions of the caller against the objects being accessed by the dynamic SQL.</span></span>  
  
 <span data-ttu-id="5eca6-133">SQL Server 提供兩種方法，可使用執行動態 SQL 的預存程序和使用者定義函式，來授與資料存取權給使用者。</span><span class="sxs-lookup"><span data-stu-id="5eca6-133">SQL Server has methods for granting users access to data using stored procedures and user-defined functions that execute dynamic SQL.</span></span>  
  
-   <span data-ttu-id="5eca6-134">使用模擬搭配 TRANSACT-SQL EXECUTE AS 子句中所述[模擬 SQL Server 中的自訂權限](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5eca6-134">Using impersonation with the Transact-SQL EXECUTE AS clause, as described in [Customizing Permissions with Impersonation in SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md).</span></span>  
  
-   <span data-ttu-id="5eca6-135">簽署憑證，預存程序中所述[SQL Server 中簽署預存程序](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5eca6-135">Signing stored procedures with certificates, as described in [Signing Stored Procedures in SQL Server](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md).</span></span>  
  
### <a name="execute-as"></a><span data-ttu-id="5eca6-136">EXECUTE AS</span><span class="sxs-lookup"><span data-stu-id="5eca6-136">EXECUTE AS</span></span>  
 <span data-ttu-id="5eca6-137">EXECUTE AS 子句會將呼叫端的權限取代成 EXECUTE AS 子句中指定之使用者的權限。</span><span class="sxs-lookup"><span data-stu-id="5eca6-137">The EXECUTE AS clause replaces the permissions of the caller with that of the user specified in the EXECUTE AS clause.</span></span> <span data-ttu-id="5eca6-138">巢狀預存程序或觸發程序 (Trigger) 會在 Proxy 使用者的安全性內容底下執行。</span><span class="sxs-lookup"><span data-stu-id="5eca6-138">Nested stored procedures or triggers execute under the security context of the proxy user.</span></span> <span data-ttu-id="5eca6-139">這樣會中斷仰賴列層級安全性或需要稽核的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5eca6-139">This can break applications that rely on row-level security or require auditing.</span></span> <span data-ttu-id="5eca6-140">傳回使用者識別的某些函式會傳回 EXECUTE AS 子句中指定的使用者，而非原始呼叫端。</span><span class="sxs-lookup"><span data-stu-id="5eca6-140">Some functions that return the identity of the user return the user specified in the EXECUTE AS clause, not the original caller.</span></span> <span data-ttu-id="5eca6-141">只有在執行此程序之後，或發出 REVERT 陳述式時，執行內容才會還原成原始呼叫端。</span><span class="sxs-lookup"><span data-stu-id="5eca6-141">Execution context is reverted to the original caller only after execution of the procedure or when a REVERT statement is issued.</span></span>  
  
### <a name="certificate-signing"></a><span data-ttu-id="5eca6-142">憑證簽署</span><span class="sxs-lookup"><span data-stu-id="5eca6-142">Certificate Signing</span></span>  
 <span data-ttu-id="5eca6-143">當您執行已經使用某個憑證簽署的預存程序時，授與憑證使用者的權限就會與呼叫端的權限合併。</span><span class="sxs-lookup"><span data-stu-id="5eca6-143">When a stored procedure that has been signed with a certificate executes, the permissions granted to the certificate user are merged with those of the caller.</span></span> <span data-ttu-id="5eca6-144">雖然執行內容維持不變，但是憑證使用者無法模擬呼叫端。</span><span class="sxs-lookup"><span data-stu-id="5eca6-144">The execution context remains the same; the certificate user does not impersonate the caller.</span></span> <span data-ttu-id="5eca6-145">簽署預存程序需要實作許多步驟。</span><span class="sxs-lookup"><span data-stu-id="5eca6-145">Signing stored procedures requires several steps to implement.</span></span> <span data-ttu-id="5eca6-146">每次修改此程序時，您就必須重新簽署程序。</span><span class="sxs-lookup"><span data-stu-id="5eca6-146">Each time the procedure is modified, it must be re-signed.</span></span>  
  
### <a name="cross-database-access"></a><span data-ttu-id="5eca6-147">跨資料庫存取</span><span class="sxs-lookup"><span data-stu-id="5eca6-147">Cross Database Access</span></span>  
 <span data-ttu-id="5eca6-148">在執行動態建立之 SQL 陳述式的情況中，跨資料庫擁有權鏈結沒有作用。</span><span class="sxs-lookup"><span data-stu-id="5eca6-148">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed.</span></span> <span data-ttu-id="5eca6-149">您可以在 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 中建立存取其他資料庫資料的預存程序，並使用存在於兩個資料庫中的憑證來簽署程序，藉此解決上述問題。</span><span class="sxs-lookup"><span data-stu-id="5eca6-149">You can work around this in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="5eca6-150">如此可以讓使用者存取該程序所使用的資料庫資源，而不必為其授與資料庫存取權或權限。</span><span class="sxs-lookup"><span data-stu-id="5eca6-150">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="5eca6-151">外部資源</span><span class="sxs-lookup"><span data-stu-id="5eca6-151">External Resources</span></span>  
 <span data-ttu-id="5eca6-152">如需詳細資訊，請參閱下列資源。</span><span class="sxs-lookup"><span data-stu-id="5eca6-152">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="5eca6-153">資源</span><span class="sxs-lookup"><span data-stu-id="5eca6-153">Resource</span></span>|<span data-ttu-id="5eca6-154">說明</span><span class="sxs-lookup"><span data-stu-id="5eca6-154">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="5eca6-155">[預存程序](http://go.microsoft.com/fwlink/?LinkId=98233)和[SQL 資料隱碼](http://go.microsoft.com/fwlink/?LinkId=98234)SQL Server 線上叢書中</span><span class="sxs-lookup"><span data-stu-id="5eca6-155">[Stored Procedures](http://go.microsoft.com/fwlink/?LinkId=98233) and [SQL Injection](http://go.microsoft.com/fwlink/?LinkId=98234) in SQL Server Books Online</span></span>|<span data-ttu-id="5eca6-156">說明如何建立預存程序以及「SQL 插入」運作方式的主題。</span><span class="sxs-lookup"><span data-stu-id="5eca6-156">Topics describe how to create stored procedures and how SQL Injection works.</span></span>|  
|<span data-ttu-id="5eca6-157">[新的 SQL 截斷攻擊和如何加以避免](http://msdn.microsoft.com/msdnmag/issues/06/11/SQLSecurity/)MSDN Magazine 中。</span><span class="sxs-lookup"><span data-stu-id="5eca6-157">[New SQL Truncation Attacks And How To Avoid Them](http://msdn.microsoft.com/msdnmag/issues/06/11/SQLSecurity/) in MSDN Magazine.</span></span>|<span data-ttu-id="5eca6-158">說明如何分隔字元和字串、SQL 插入和截斷攻擊的修改。</span><span class="sxs-lookup"><span data-stu-id="5eca6-158">Describes how to delimit characters and strings, SQL injection, and modification by  truncation attacks.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5eca6-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5eca6-159">See Also</span></span>  
 [<span data-ttu-id="5eca6-160">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="5eca6-160">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="5eca6-161">SQL Server 安全性概觀</span><span class="sxs-lookup"><span data-stu-id="5eca6-161">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="5eca6-162">SQL Server 中的應用程式安全性案例</span><span class="sxs-lookup"><span data-stu-id="5eca6-162">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="5eca6-163">管理 SQL Server 中的預存程序的權限</span><span class="sxs-lookup"><span data-stu-id="5eca6-163">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="5eca6-164">簽署 SQL Server 中的預存程序</span><span class="sxs-lookup"><span data-stu-id="5eca6-164">Signing Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="5eca6-165">自訂 SQL Server 中的模擬權限</span><span class="sxs-lookup"><span data-stu-id="5eca6-165">Customizing Permissions with Impersonation in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [<span data-ttu-id="5eca6-166">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="5eca6-166">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
