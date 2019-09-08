---
title: 在 SQL Server 中進行驗證
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 49835ebf8ebe4d5bd200ed771477edc8af580b7d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794288"
---
# <a name="authentication-in-sql-server"></a><span data-ttu-id="e2206-102">在 SQL Server 中進行驗證</span><span class="sxs-lookup"><span data-stu-id="e2206-102">Authentication in SQL Server</span></span>
<span data-ttu-id="e2206-103">SQL Server 支援兩種驗證模式：Windows 驗證模式和混合模式。</span><span class="sxs-lookup"><span data-stu-id="e2206-103">SQL Server supports two authentication modes, Windows authentication mode and mixed mode.</span></span>  
  
- <span data-ttu-id="e2206-104">Windows 驗證是預設設定，也經常稱為整合式安全性，因為這個 SQL Server 安全性模型會與 Windows 緊密整合。</span><span class="sxs-lookup"><span data-stu-id="e2206-104">Windows authentication is the default, and is often referred to as integrated security because this SQL Server security model is tightly integrated with Windows.</span></span> <span data-ttu-id="e2206-105">特定的 Windows 使用者和群組帳戶會受信任而可登入 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="e2206-105">Specific Windows user and group accounts are trusted to log in to SQL Server.</span></span> <span data-ttu-id="e2206-106">已經過驗證的 Windows 使用者不必再提供額外認證資料。</span><span class="sxs-lookup"><span data-stu-id="e2206-106">Windows users who have already been authenticated do not have to present additional credentials.</span></span>  
  
- <span data-ttu-id="e2206-107">混合模式支援 Windows 和 SQL Server 提供的驗證。</span><span class="sxs-lookup"><span data-stu-id="e2206-107">Mixed mode supports authentication both by Windows and by SQL Server.</span></span> <span data-ttu-id="e2206-108">使用者名稱和密碼組會在 SQL Server 內進行維護。</span><span class="sxs-lookup"><span data-stu-id="e2206-108">User name and password pairs are maintained within SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e2206-109">建議盡量使用「Windows 驗證」。</span><span class="sxs-lookup"><span data-stu-id="e2206-109">We recommend using Windows authentication wherever possible.</span></span> <span data-ttu-id="e2206-110">Windows 驗證會使用一系列的加密訊息在 SQL Server 中驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="e2206-110">Windows authentication uses a series of encrypted messages to authenticate users in SQL Server.</span></span> <span data-ttu-id="e2206-111">使用 SQL Server 登入時，系統會在網路上傳遞 SQL Server 登入名稱和加密的密碼，使其較不安全。</span><span class="sxs-lookup"><span data-stu-id="e2206-111">When SQL Server logins are used, SQL Server login names and encrypted passwords are passed across the network, which makes them less secure.</span></span>  
  
 <span data-ttu-id="e2206-112">使用 Windows 驗證的好處是因為使用者已登入 Windows，所以不必再另行登入 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="e2206-112">With Windows authentication, users are already logged onto Windows and do not have to log on separately to SQL Server.</span></span> <span data-ttu-id="e2206-113">下列`SqlConnection.ConnectionString`指定 Windows 驗證，而不需要使用者提供使用者名稱或密碼。</span><span class="sxs-lookup"><span data-stu-id="e2206-113">The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring users to provide a user name or password.</span></span>  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
> <span data-ttu-id="e2206-114">登入不同於資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="e2206-114">Logins are distinct from database users.</span></span> <span data-ttu-id="e2206-115">您必須藉由個別作業，將登入或 Windows 群組對應到資料庫使用者或角色。</span><span class="sxs-lookup"><span data-stu-id="e2206-115">You must map logins or Windows groups to database users or roles in a separate operation.</span></span> <span data-ttu-id="e2206-116">接著再將存取資料庫物件的權限授與使用者或角色。</span><span class="sxs-lookup"><span data-stu-id="e2206-116">You then grant permissions to users or roles to access database objects.</span></span>  
  
## <a name="authentication-scenarios"></a><span data-ttu-id="e2206-117">驗證案例</span><span class="sxs-lookup"><span data-stu-id="e2206-117">Authentication Scenarios</span></span>  
 <span data-ttu-id="e2206-118">在下列情況中，Windows 驗證通常是最佳選擇：</span><span class="sxs-lookup"><span data-stu-id="e2206-118">Windows authentication is usually the best choice in the following situations:</span></span>  
  
- <span data-ttu-id="e2206-119">有網域控制站存在。</span><span class="sxs-lookup"><span data-stu-id="e2206-119">There is a domain controller.</span></span>  
  
- <span data-ttu-id="e2206-120">應用程式和資料庫位於相同的電腦。</span><span class="sxs-lookup"><span data-stu-id="e2206-120">The application and the database are on the same computer.</span></span>  
  
- <span data-ttu-id="e2206-121">您使用的是 SQL Server Express 或 LocalDB 的實例。</span><span class="sxs-lookup"><span data-stu-id="e2206-121">You are using an instance of SQL Server Express or LocalDB.</span></span>  
  
 <span data-ttu-id="e2206-122">SQL Server 登入通常用於以下狀況：</span><span class="sxs-lookup"><span data-stu-id="e2206-122">SQL Server logins are often used in the following situations:</span></span>  
  
- <span data-ttu-id="e2206-123">如果您擁有工作群組。</span><span class="sxs-lookup"><span data-stu-id="e2206-123">If you have a workgroup.</span></span>  
  
- <span data-ttu-id="e2206-124">使用者是自不同的非受信任網域進行連接。</span><span class="sxs-lookup"><span data-stu-id="e2206-124">Users connect from different, non-trusted domains.</span></span>  
  
- <span data-ttu-id="e2206-125">網際網路應用程式，例如 ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="e2206-125">Internet applications, such as ASP.NET.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2206-126">指定 Windows 驗證並不會停用 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="e2206-126">Specifying Windows authentication does not disable SQL Server logins.</span></span> <span data-ttu-id="e2206-127">請使用 ALTER LOGIN DISABLE Transact-SQL 陳述式來停用具有高權限的 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="e2206-127">Use the ALTER LOGIN DISABLE Transact-SQL statement to disable highly-privileged SQL Server logins.</span></span>  
  
## <a name="login-types"></a><span data-ttu-id="e2206-128">登入類型</span><span class="sxs-lookup"><span data-stu-id="e2206-128">Login Types</span></span>  
 <span data-ttu-id="e2206-129">SQL Server 支援三種登入類型：</span><span class="sxs-lookup"><span data-stu-id="e2206-129">SQL Server supports three types of logins:</span></span>  
  
- <span data-ttu-id="e2206-130">本機 Windows 使用者帳戶或受信任的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="e2206-130">A local Windows user account or trusted domain account.</span></span> <span data-ttu-id="e2206-131">SQL Server 會仰賴 Windows 來驗證 Windows 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="e2206-131">SQL Server relies on Windows to authenticate the Windows user accounts.</span></span>  
  
- <span data-ttu-id="e2206-132">Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="e2206-132">Windows group.</span></span> <span data-ttu-id="e2206-133">如果授與存取權給 Windows 群組，則也會授權給全部該群組成員的 Windows 使用者登入。</span><span class="sxs-lookup"><span data-stu-id="e2206-133">Granting access to a Windows group grants access to all Windows user logins that are members of the group.</span></span>  
  
- <span data-ttu-id="e2206-134">SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="e2206-134">SQL Server login.</span></span> <span data-ttu-id="e2206-135">SQL Server 會將使用者名稱和密碼雜湊儲存在 master 資料庫，並使用內部驗證方法確認登入作業。</span><span class="sxs-lookup"><span data-stu-id="e2206-135">SQL Server stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2206-136">SQL Server 提供從憑證建立的登入，或僅用於程式碼簽署的非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="e2206-136">SQL Server provides logins created from certificates or asymmetric keys that are used only for code signing.</span></span> <span data-ttu-id="e2206-137">而不會用來連接至 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="e2206-137">They cannot be used to connect to SQL Server.</span></span>  
  
## <a name="mixed-mode-authentication"></a><span data-ttu-id="e2206-138">混合模式驗證</span><span class="sxs-lookup"><span data-stu-id="e2206-138">Mixed Mode Authentication</span></span>  
 <span data-ttu-id="e2206-139">如果您必須使用混合模式驗證，則必須建立儲存在 SQL Server 中的 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="e2206-139">If you must use mixed mode authentication, you must create SQL Server logins, which are stored in SQL Server.</span></span> <span data-ttu-id="e2206-140">然後在執行階段時還需要提供 SQL Server 使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="e2206-140">You then have to supply the SQL Server user name and password at run time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e2206-141">SQL Server 會使用名為 `sa` (「系統管理員」的縮寫) 的 SQL Server 登入來進行安裝。</span><span class="sxs-lookup"><span data-stu-id="e2206-141">SQL Server installs with a SQL Server login named `sa` (an abbreviation of "system administrator").</span></span> <span data-ttu-id="e2206-142">請指派強式密碼給 `sa` 登入，且不要在應用程式中使用 `sa` 登入。</span><span class="sxs-lookup"><span data-stu-id="e2206-142">Assign a strong password to the `sa` login and do not use the `sa` login in your application.</span></span> <span data-ttu-id="e2206-143">`sa` 登入對應的是 `sysadmin` 固定伺服器角色，對於整個伺服器具有不可變更之管理權限。</span><span class="sxs-lookup"><span data-stu-id="e2206-143">The `sa` login maps to the `sysadmin` fixed server role, which has irrevocable administrative credentials on the whole server.</span></span> <span data-ttu-id="e2206-144">如果攻擊者取得系統管理員的存取權，就可以大肆破壞而毫不受限。</span><span class="sxs-lookup"><span data-stu-id="e2206-144">There are no limits to the potential damage if an attacker gains access as a system administrator.</span></span> <span data-ttu-id="e2206-145">Windows `BUILTIN\Administrators` 群組 (本機系統管理員群組) 的所有成員，都會預設為 `sysadmin` 角色的成員，但可以從該角色移除。</span><span class="sxs-lookup"><span data-stu-id="e2206-145">All members of the Windows `BUILTIN\Administrators` group (the local administrator's group) are members of the `sysadmin` role by default, but can be removed from that role.</span></span>  
  
 <span data-ttu-id="e2206-146">SQL Server 在或更新版本上[!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)]執行時，會為 SQL Server 登入提供 Windows 密碼原則機制。</span><span class="sxs-lookup"><span data-stu-id="e2206-146">SQL Server provides Windows password policy mechanisms for SQL Server logins when it is running on [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] or later versions.</span></span> <span data-ttu-id="e2206-147">密碼複雜性原則是為了阻止暴力攻擊而設計，方法是盡可能地增加密碼數目。</span><span class="sxs-lookup"><span data-stu-id="e2206-147">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="e2206-148">SQL Server 可以將中[!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)]所使用的相同複雜性和到期原則套用至 SQL Server 內使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="e2206-148">SQL Server can apply the same complexity and expiration policies used in [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] to passwords used inside SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e2206-149">串連來自使用者輸入的連接字串，可能會使您易遭受連接字串插入式攻擊。</span><span class="sxs-lookup"><span data-stu-id="e2206-149">Concatenating connection strings from user input can leave you vulnerable to a connection string injection attack.</span></span> <span data-ttu-id="e2206-150">請使用 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 在執行階段建立語法有效的連接字串。</span><span class="sxs-lookup"><span data-stu-id="e2206-150">Use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="e2206-151">如需詳細資訊，請參閱[連接字串建置器](../connection-string-builders.md)。</span><span class="sxs-lookup"><span data-stu-id="e2206-151">For more information, see [Connection String Builders](../connection-string-builders.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="e2206-152">外部資源</span><span class="sxs-lookup"><span data-stu-id="e2206-152">External Resources</span></span>  
 <span data-ttu-id="e2206-153">如需詳細資訊，請參閱下列資源。</span><span class="sxs-lookup"><span data-stu-id="e2206-153">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="e2206-154">Resource</span><span class="sxs-lookup"><span data-stu-id="e2206-154">Resource</span></span>|<span data-ttu-id="e2206-155">說明</span><span class="sxs-lookup"><span data-stu-id="e2206-155">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="e2206-156">原理</span><span class="sxs-lookup"><span data-stu-id="e2206-156">Principals</span></span>](/sql/relational-databases/security/authentication-access/principals-database-engine)|<span data-ttu-id="e2206-157">描述 SQL Server 中的登入和其他安全性主體。</span><span class="sxs-lookup"><span data-stu-id="e2206-157">Describes logins and other security principals in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e2206-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2206-158">See also</span></span>

- [<span data-ttu-id="e2206-159">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="e2206-159">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="e2206-160">SQL Server 中的應用程式安全性案例</span><span class="sxs-lookup"><span data-stu-id="e2206-160">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="e2206-161">連接至資料來源</span><span class="sxs-lookup"><span data-stu-id="e2206-161">Connecting to a Data Source</span></span>](../connecting-to-a-data-source.md)
- [<span data-ttu-id="e2206-162">連接字串</span><span class="sxs-lookup"><span data-stu-id="e2206-162">Connection Strings</span></span>](../connection-strings.md)
- [<span data-ttu-id="e2206-163">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="e2206-163">ADO.NET Overview</span></span>](../ado-net-overview.md)
