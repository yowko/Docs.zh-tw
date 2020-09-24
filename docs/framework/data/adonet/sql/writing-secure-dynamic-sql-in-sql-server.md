---
title: 在 SQL Server 中撰寫安全的動態 SQL
ms.date: 03/30/2017
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
ms.openlocfilehash: c598427a17ceb289f75fab481a55016f0efe5624
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147446"
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a><span data-ttu-id="f5d6b-102">在 SQL Server 中撰寫安全的動態 SQL</span><span class="sxs-lookup"><span data-stu-id="f5d6b-102">Writing Secure Dynamic SQL in SQL Server</span></span>

<span data-ttu-id="f5d6b-103">SQL 插入式攻擊是指惡意使用者輸入 Transact-SQL 陳述式，而非提供有效輸入的程序。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-103">SQL Injection is the process by which a malicious user enters Transact-SQL statements instead of valid input.</span></span> <span data-ttu-id="f5d6b-104">如果在未驗證的情況下將輸入直接傳遞至伺服器，而且應用程式不慎執行了以資料隱碼方式撰寫的程式碼，攻擊就可能會破壞或損毀資料。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-104">If the input is passed directly to the server without being validated and if the application inadvertently executes the injected code, the attack has the potential to damage or destroy data.</span></span>  
  
 <span data-ttu-id="f5d6b-105">建構 SQL 陳述式的任何程序都應該經過檢閱，以確認有無插入弱點，因為 SQL Server 會執行收到的所有語法有效查詢。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-105">Any procedure that constructs SQL statements should be reviewed for injection vulnerabilities because SQL Server will execute all syntactically valid queries that it receives.</span></span> <span data-ttu-id="f5d6b-106">即使是參數化資料也可能被技術純熟又執意操作的攻擊者操縱。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-106">Even parameterized data can be manipulated by a skilled and determined attacker.</span></span> <span data-ttu-id="f5d6b-107">如果您使用動態 SQL，請務必將命令參數化，且一律不要將參數值直接包含在查詢字串中。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-107">If you use dynamic SQL, be sure to parameterize your commands, and never include parameter values directly into the query string.</span></span>  
  
## <a name="anatomy-of-a-sql-injection-attack"></a><span data-ttu-id="f5d6b-108">SQL 插入式攻擊的分析</span><span class="sxs-lookup"><span data-stu-id="f5d6b-108">Anatomy of a SQL Injection Attack</span></span>  

 <span data-ttu-id="f5d6b-109">資料隱碼處理的運作方式是不當地終止文字字串並附加新命令。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-109">The injection process works by prematurely terminating a text string and appending a new command.</span></span> <span data-ttu-id="f5d6b-110">因為插入的命令在執行之前可能附加有其他字串，所以不懷好意的人會使用註解標記 "--" 終止插入的字串。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-110">Because the inserted command may have additional strings appended to it before it is executed, the malefactor terminates the injected string with a comment mark "--".</span></span> <span data-ttu-id="f5d6b-111">在執行時，後續文字便會被忽略。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-111">Subsequent text is ignored at execution time.</span></span> <span data-ttu-id="f5d6b-112">可以使用分號 (;) 分隔符號插入多個命令。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-112">Multiple commands can be inserted using a semicolon (;) delimiter.</span></span>  
  
 <span data-ttu-id="f5d6b-113">只要插入的 SQL 程式碼語法正確，就無法以程式設計方式偵測竄改。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-113">As long as injected SQL code is syntactically correct, tampering cannot be detected programmatically.</span></span> <span data-ttu-id="f5d6b-114">因此，您必須驗證所有使用者輸入，並且仔細檢視在您使用的伺服器中執行建構之 SQL 命令的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-114">Therefore, you must validate all user input and carefully review code that executes constructed SQL commands in the server that you are using.</span></span> <span data-ttu-id="f5d6b-115">絕不串連未經驗證的使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-115">Never concatenate user input that is not validated.</span></span> <span data-ttu-id="f5d6b-116">字串串連是指令碼資料隱碼的主要進入點。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-116">String concatenation is the primary point of entry for script injection.</span></span>  
  
 <span data-ttu-id="f5d6b-117">以下提供一些實用的指導方針：</span><span class="sxs-lookup"><span data-stu-id="f5d6b-117">Here are some helpful guidelines:</span></span>  
  
- <span data-ttu-id="f5d6b-118">一律不要直接從使用者輸入建立 Transact-SQL 陳述式，並使用預存程序驗證使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-118">Never build Transact-SQL statements directly from user input; use stored procedures to validate user input.</span></span>  
  
- <span data-ttu-id="f5d6b-119">透過測試類型、長度、格式和範圍，驗證使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-119">Validate user input by testing type, length, format, and range.</span></span> <span data-ttu-id="f5d6b-120">使用 Transact-SQL QUOTENAME () 函式來逸出系統名稱或 REPLACE () 函式，以逸出字串中的任何字元。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-120">Use the Transact-SQL QUOTENAME() function to escape system names or the REPLACE() function to escape any character in a string.</span></span>  
  
- <span data-ttu-id="f5d6b-121">在應用程式的每一層實作多層驗證。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-121">Implement multiple layers of validation in each tier of your application.</span></span>  
  
- <span data-ttu-id="f5d6b-122">測試輸入的大小和資料類型，並強制執行適當的限制。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-122">Test the size and data type of input and enforce appropriate limits.</span></span> <span data-ttu-id="f5d6b-123">這有助於防止蓄意的緩衝區滿溢。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-123">This can help prevent deliberate buffer overruns.</span></span>  
  
- <span data-ttu-id="f5d6b-124">測試字串變數的內容，僅接受預期的值。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-124">Test the content of string variables and accept only expected values.</span></span> <span data-ttu-id="f5d6b-125">拒絕包含二進位資料、逸出序列和註解字元的項目。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-125">Reject entries that contain binary data, escape sequences, and comment characters.</span></span>  
  
- <span data-ttu-id="f5d6b-126">使用 XML 文件時，在輸入資料時即驗證所有資料的結構描述。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-126">When you are working with XML documents, validate all data against its schema as it is entered.</span></span>  
  
- <span data-ttu-id="f5d6b-127">在多層環境中，所有資料應在進入受信任區域之前進行驗證。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-127">In multi-tiered environments, all data should be validated before admission to the trusted zone.</span></span>  
  
- <span data-ttu-id="f5d6b-128">在可用以建構檔案名稱的欄位中，不接受下列字串：AUX、CLOCK$、COM1 到 COM8、CON、CONFIG$、LPT1 到 LPT8、NUL 和 PRN。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-128">Do not accept the following strings in fields from which file names can be constructed: AUX, CLOCK$, COM1 through COM8, CON, CONFIG$, LPT1 through LPT8, NUL, and PRN.</span></span>  
  
- <span data-ttu-id="f5d6b-129">搭配預存程序和命令使用 <xref:System.Data.SqlClient.SqlParameter> 物件，以提供類型檢查及長度驗證功能。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-129">Use <xref:System.Data.SqlClient.SqlParameter> objects with stored procedures and commands to provide type checking and length validation.</span></span>  
  
- <span data-ttu-id="f5d6b-130">在用戶端程式碼中使用 <xref:System.Text.RegularExpressions.Regex> 運算式來篩選無效字元。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-130">Use <xref:System.Text.RegularExpressions.Regex> expressions in client code to filter invalid characters.</span></span>  
  
## <a name="dynamic-sql-strategies"></a><span data-ttu-id="f5d6b-131">動態 SQL 策略</span><span class="sxs-lookup"><span data-stu-id="f5d6b-131">Dynamic SQL Strategies</span></span>  

 <span data-ttu-id="f5d6b-132">在您的程序式程式碼中執行動態建立的 SQL 陳述式會中斷擁有權鏈結，使 SQL Server 針對動態 SQL 所存取的物件檢查呼叫者的權限。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-132">Executing dynamically created SQL statements in your procedural code breaks the ownership chain, causing SQL Server to check the permissions of the caller against the objects being accessed by the dynamic SQL.</span></span>  
  
 <span data-ttu-id="f5d6b-133">SQL Server 具有一些方法，可使用執行動態 SQL 的預存程序和使用者定義函式來授與資料存取權給使用者。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-133">SQL Server has methods for granting users access to data using stored procedures and user-defined functions that execute dynamic SQL.</span></span>  
  
- <span data-ttu-id="f5d6b-134">使用模擬搭配 Transact-SQL EXECUTE AS 子句，如[在 SQL Server 中使用模擬來自訂權限](customizing-permissions-with-impersonation-in-sql-server.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-134">Using impersonation with the Transact-SQL EXECUTE AS clause, as described in [Customizing Permissions with Impersonation in SQL Server](customizing-permissions-with-impersonation-in-sql-server.md).</span></span>  
  
- <span data-ttu-id="f5d6b-135">使用憑證簽署預存程序，如[在 SQL Server 中簽署預存程序](signing-stored-procedures-in-sql-server.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-135">Signing stored procedures with certificates, as described in [Signing Stored Procedures in SQL Server](signing-stored-procedures-in-sql-server.md).</span></span>  
  
### <a name="execute-as"></a><span data-ttu-id="f5d6b-136">EXECUTE AS</span><span class="sxs-lookup"><span data-stu-id="f5d6b-136">EXECUTE AS</span></span>  

 <span data-ttu-id="f5d6b-137">EXECUTE AS 子句會將呼叫者的權限取代為 EXECUTE AS 子句中所指定使用者的權限。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-137">The EXECUTE AS clause replaces the permissions of the caller with that of the user specified in the EXECUTE AS clause.</span></span> <span data-ttu-id="f5d6b-138">巢狀預存程序或觸發程序會以 Proxy 使用者的資訊安全內容執行。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-138">Nested stored procedures or triggers execute under the security context of the proxy user.</span></span> <span data-ttu-id="f5d6b-139">這可能會中斷依賴資料列層級安全性或需要稽核的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-139">This can break applications that rely on row-level security or require auditing.</span></span> <span data-ttu-id="f5d6b-140">某些會傳回使用者身分識別的函式會傳回 EXECUTE AS 子句中指定的使用者，而非原始呼叫者。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-140">Some functions that return the identity of the user return the user specified in the EXECUTE AS clause, not the original caller.</span></span> <span data-ttu-id="f5d6b-141">只有在執行程序之後或發出 REVERT 陳述式時，執行內容才會還原為原始呼叫者。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-141">Execution context is reverted to the original caller only after execution of the procedure or when a REVERT statement is issued.</span></span>  
  
### <a name="certificate-signing"></a><span data-ttu-id="f5d6b-142">憑證簽署</span><span class="sxs-lookup"><span data-stu-id="f5d6b-142">Certificate Signing</span></span>  

 <span data-ttu-id="f5d6b-143">當使用憑證簽署的預存程序執行時，授與憑證使用者的權限會與呼叫者的權限合併。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-143">When a stored procedure that has been signed with a certificate executes, the permissions granted to the certificate user are merged with those of the caller.</span></span> <span data-ttu-id="f5d6b-144">執行內容會維持不變；憑證使用者並不會模擬呼叫者。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-144">The execution context remains the same; the certificate user does not impersonate the caller.</span></span> <span data-ttu-id="f5d6b-145">簽署預存程序需要實作數個步驟。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-145">Signing stored procedures requires several steps to implement.</span></span> <span data-ttu-id="f5d6b-146">每次修改程序之後，都必須重新簽署。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-146">Each time the procedure is modified, it must be re-signed.</span></span>  
  
### <a name="cross-database-access"></a><span data-ttu-id="f5d6b-147">跨資料庫存取</span><span class="sxs-lookup"><span data-stu-id="f5d6b-147">Cross Database Access</span></span>  

 <span data-ttu-id="f5d6b-148">執行以動態方式建立的 SQL 陳述式時，跨資料庫擁有權鏈結無法運作。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-148">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed.</span></span> <span data-ttu-id="f5d6b-149">您可以在 SQL Server 中建立存取其他資料庫資料的預存程序，並使用存在於兩個資料庫中的憑證來簽署程序，藉此解決上述問題。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-149">You can work around this in SQL Server by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="f5d6b-150">這可讓使用者存取由程序所使用的資料庫資源，不需要授與他們資料庫存取權或權限。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-150">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="f5d6b-151">外部資源</span><span class="sxs-lookup"><span data-stu-id="f5d6b-151">External Resources</span></span>  

 <span data-ttu-id="f5d6b-152">如需詳細資訊，請參閱下列資源。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-152">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="f5d6b-153">資源</span><span class="sxs-lookup"><span data-stu-id="f5d6b-153">Resource</span></span>|<span data-ttu-id="f5d6b-154">描述</span><span class="sxs-lookup"><span data-stu-id="f5d6b-154">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="f5d6b-155">《SQL Server 線上叢書》中的[預存程序](/sql/relational-databases/stored-procedures/stored-procedures-database-engine)和 [SQL 資料隱碼](/sql/relational-databases/security/sql-injection)</span><span class="sxs-lookup"><span data-stu-id="f5d6b-155">[Stored Procedures](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) and [SQL Injection](/sql/relational-databases/security/sql-injection) in SQL Server Books Online</span></span>|<span data-ttu-id="f5d6b-156">各主題會描述如何建立預存程序，以及 SQL 插入式攻擊的運作方式。</span><span class="sxs-lookup"><span data-stu-id="f5d6b-156">Topics describe how to create stored procedures and how SQL Injection works.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5d6b-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5d6b-157">See also</span></span>

- [<span data-ttu-id="f5d6b-158">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="f5d6b-158">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="f5d6b-159">SQL Server 安全性概觀</span><span class="sxs-lookup"><span data-stu-id="f5d6b-159">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="f5d6b-160">SQL Server 中的應用程式安全性案例</span><span class="sxs-lookup"><span data-stu-id="f5d6b-160">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="f5d6b-161">使用預存程序管理 SQL Server 中的權限</span><span class="sxs-lookup"><span data-stu-id="f5d6b-161">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="f5d6b-162">在 SQL Server 中簽署預存程序</span><span class="sxs-lookup"><span data-stu-id="f5d6b-162">Signing Stored Procedures in SQL Server</span></span>](signing-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="f5d6b-163">在 SQL Server 中使用模擬來自訂權限</span><span class="sxs-lookup"><span data-stu-id="f5d6b-163">Customizing Permissions with Impersonation in SQL Server</span></span>](customizing-permissions-with-impersonation-in-sql-server.md)
- <span data-ttu-id="f5d6b-164">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="f5d6b-164">[ADO.NET Overview](../ado-net-overview.md)</span></span>
