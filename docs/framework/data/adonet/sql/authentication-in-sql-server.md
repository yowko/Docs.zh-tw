---
title: 在 SQL Server 中進行驗證
description: 瞭解使用 SQL Server ADO.NET 的驗證，包括 Windows 驗證模式和混合模式。
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: e9915598acfbdefb59069d6a9c6ef4b7c824e4c6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286542"
---
# <a name="authentication-in-sql-server"></a><span data-ttu-id="5909b-103">在 SQL Server 中進行驗證</span><span class="sxs-lookup"><span data-stu-id="5909b-103">Authentication in SQL Server</span></span>
<span data-ttu-id="5909b-104">SQL Server 支援兩種驗證模式：Windows 驗證模式和混合模式。</span><span class="sxs-lookup"><span data-stu-id="5909b-104">SQL Server supports two authentication modes, Windows authentication mode and mixed mode.</span></span>  
  
- <span data-ttu-id="5909b-105">Windows 驗證是預設設定，也經常稱為整合式安全性，原因為這個 SQL Server 安全性模型會與 Windows 緊密整合。</span><span class="sxs-lookup"><span data-stu-id="5909b-105">Windows authentication is the default, and is often referred to as integrated security because this SQL Server security model is tightly integrated with Windows.</span></span> <span data-ttu-id="5909b-106">特定的 Windows 使用者和群組帳戶要受到信任，才能登入 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="5909b-106">Specific Windows user and group accounts are trusted to log in to SQL Server.</span></span> <span data-ttu-id="5909b-107">已通過驗證的 Windows 使用者不需出示額外的認證。</span><span class="sxs-lookup"><span data-stu-id="5909b-107">Windows users who have already been authenticated do not have to present additional credentials.</span></span>  
  
- <span data-ttu-id="5909b-108">混合模式支援 Windows 和 SQL Server 提供的驗證。</span><span class="sxs-lookup"><span data-stu-id="5909b-108">Mixed mode supports authentication both by Windows and by SQL Server.</span></span> <span data-ttu-id="5909b-109">使用者名稱和密碼組會在 SQL Server 內進行維護。</span><span class="sxs-lookup"><span data-stu-id="5909b-109">User name and password pairs are maintained within SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5909b-110">我們建議盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="5909b-110">We recommend using Windows authentication wherever possible.</span></span> <span data-ttu-id="5909b-111">Windows 驗證會使用一系列的加密訊息在 SQL Server 中驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="5909b-111">Windows authentication uses a series of encrypted messages to authenticate users in SQL Server.</span></span> <span data-ttu-id="5909b-112">使用 SQL Server 登入時，SQL Server 登入名稱及加密密碼會透過網路傳遞，因而降低其安全性。</span><span class="sxs-lookup"><span data-stu-id="5909b-112">When SQL Server logins are used, SQL Server login names and encrypted passwords are passed across the network, which makes them less secure.</span></span>  
  
 <span data-ttu-id="5909b-113">使用 Windows 驗證的好處是因為使用者已登入 Windows，所以不必再另行登入 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="5909b-113">With Windows authentication, users are already logged onto Windows and do not have to log on separately to SQL Server.</span></span> <span data-ttu-id="5909b-114">下列 `SqlConnection.ConnectionString` 可指定 Windows 驗證，且不需要使用者提供使用者名稱或密碼。</span><span class="sxs-lookup"><span data-stu-id="5909b-114">The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring users to provide a user name or password.</span></span>  
  
```csharp  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;"
```  
  
> [!NOTE]
> <span data-ttu-id="5909b-115">登入與資料庫使用者不同。</span><span class="sxs-lookup"><span data-stu-id="5909b-115">Logins are distinct from database users.</span></span> <span data-ttu-id="5909b-116">您必須在個別作業中，將登入或 Windows 群組對應到資料庫使用者或角色。</span><span class="sxs-lookup"><span data-stu-id="5909b-116">You must map logins or Windows groups to database users or roles in a separate operation.</span></span> <span data-ttu-id="5909b-117">接著，您可以將權限授與使用者或角色來存取資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="5909b-117">You then grant permissions to users or roles to access database objects.</span></span>  
  
## <a name="authentication-scenarios"></a><span data-ttu-id="5909b-118">驗證案例</span><span class="sxs-lookup"><span data-stu-id="5909b-118">Authentication Scenarios</span></span>  
 <span data-ttu-id="5909b-119">在下列情況中，Windows 驗證通常是最佳選擇：</span><span class="sxs-lookup"><span data-stu-id="5909b-119">Windows authentication is usually the best choice in the following situations:</span></span>  
  
- <span data-ttu-id="5909b-120">有一個網域控制站。</span><span class="sxs-lookup"><span data-stu-id="5909b-120">There is a domain controller.</span></span>  
  
- <span data-ttu-id="5909b-121">應用程式和資料庫均位於相同電腦上。</span><span class="sxs-lookup"><span data-stu-id="5909b-121">The application and the database are on the same computer.</span></span>  
  
- <span data-ttu-id="5909b-122">您使用的是 SQL Server Express 或 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="5909b-122">You are using an instance of SQL Server Express or LocalDB.</span></span>  
  
 <span data-ttu-id="5909b-123">在下列情況中，通常會使用 SQL Server 登入：</span><span class="sxs-lookup"><span data-stu-id="5909b-123">SQL Server logins are often used in the following situations:</span></span>  
  
- <span data-ttu-id="5909b-124">如果您有工作群組。</span><span class="sxs-lookup"><span data-stu-id="5909b-124">If you have a workgroup.</span></span>  
  
- <span data-ttu-id="5909b-125">使用者從不受信任的不同網域進行連線。</span><span class="sxs-lookup"><span data-stu-id="5909b-125">Users connect from different, non-trusted domains.</span></span>  
  
- <span data-ttu-id="5909b-126">網際網路應用程式，例如 ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="5909b-126">Internet applications, such as ASP.NET.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5909b-127">指定 Windows 驗證並不會停用 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="5909b-127">Specifying Windows authentication does not disable SQL Server logins.</span></span> <span data-ttu-id="5909b-128">請使用 ALTER LOGIN DISABLE Transact-SQL 陳述式來停用具有高權限的 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="5909b-128">Use the ALTER LOGIN DISABLE Transact-SQL statement to disable highly-privileged SQL Server logins.</span></span>  
  
## <a name="login-types"></a><span data-ttu-id="5909b-129">登入類型</span><span class="sxs-lookup"><span data-stu-id="5909b-129">Login Types</span></span>  
 <span data-ttu-id="5909b-130">SQL Server 支援三種登入類型：</span><span class="sxs-lookup"><span data-stu-id="5909b-130">SQL Server supports three types of logins:</span></span>  
  
- <span data-ttu-id="5909b-131">本機 Windows 使用者帳戶或受信任的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="5909b-131">A local Windows user account or trusted domain account.</span></span> <span data-ttu-id="5909b-132">SQL Server 會仰賴 Windows 來驗證 Windows 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="5909b-132">SQL Server relies on Windows to authenticate the Windows user accounts.</span></span>  
  
- <span data-ttu-id="5909b-133">Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="5909b-133">Windows group.</span></span> <span data-ttu-id="5909b-134">為 Windows 群組授與存取權，可為屬於群組成員的所有 Windows 使用者登入授與存取權。</span><span class="sxs-lookup"><span data-stu-id="5909b-134">Granting access to a Windows group grants access to all Windows user logins that are members of the group.</span></span>  
  
- <span data-ttu-id="5909b-135">SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="5909b-135">SQL Server login.</span></span> <span data-ttu-id="5909b-136">SQL Server 會使用內部驗證方法確認登入作業，將使用者名稱和密碼雜湊儲存在 master 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5909b-136">SQL Server stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5909b-137">SQL Server 提供從憑證建立的登入或非對稱金鑰，這些項目只能用於程式碼簽署。</span><span class="sxs-lookup"><span data-stu-id="5909b-137">SQL Server provides logins created from certificates or asymmetric keys that are used only for code signing.</span></span> <span data-ttu-id="5909b-138">它們不能用來連線至 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="5909b-138">They cannot be used to connect to SQL Server.</span></span>  
  
## <a name="mixed-mode-authentication"></a><span data-ttu-id="5909b-139">混合模式驗證</span><span class="sxs-lookup"><span data-stu-id="5909b-139">Mixed Mode Authentication</span></span>  
 <span data-ttu-id="5909b-140">如果您必須使用混合模式驗證，則必須建立儲存在 SQL Server 中的 SQL Server 登入。</span><span class="sxs-lookup"><span data-stu-id="5909b-140">If you must use mixed mode authentication, you must create SQL Server logins, which are stored in SQL Server.</span></span> <span data-ttu-id="5909b-141">然後在執行階段時還需要提供 SQL Server 使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="5909b-141">You then have to supply the SQL Server user name and password at run time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5909b-142">SQL Server 會使用名為 `sa` (「系統管理員」的縮寫) 的 SQL Server 登入進行安裝。</span><span class="sxs-lookup"><span data-stu-id="5909b-142">SQL Server installs with a SQL Server login named `sa` (an abbreviation of "system administrator").</span></span> <span data-ttu-id="5909b-143">將強式密碼指派給 `sa` 登入，而不要在您的應用程式中使用 `sa` 登入。</span><span class="sxs-lookup"><span data-stu-id="5909b-143">Assign a strong password to the `sa` login and do not use the `sa` login in your application.</span></span> <span data-ttu-id="5909b-144">`sa` 登入會對應到 `sysadmin` 固定伺服器角色，其在整部伺服器上具有無法撤銷的系統管理認證。</span><span class="sxs-lookup"><span data-stu-id="5909b-144">The `sa` login maps to the `sysadmin` fixed server role, which has irrevocable administrative credentials on the whole server.</span></span> <span data-ttu-id="5909b-145">如果攻擊者取得系統管理員的存取權，對於潛在損害就沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="5909b-145">There are no limits to the potential damage if an attacker gains access as a system administrator.</span></span> <span data-ttu-id="5909b-146">Windows `BUILTIN\Administrators` 群組 (本機系統管理員群組) 的所有成員，都會預設為 `sysadmin` 角色的成員，但可以從該角色移除。</span><span class="sxs-lookup"><span data-stu-id="5909b-146">All members of the Windows `BUILTIN\Administrators` group (the local administrator's group) are members of the `sysadmin` role by default, but can be removed from that role.</span></span>  
  
 <span data-ttu-id="5909b-147">SQL Server 提供 SQL Server 登入的 Windows 密碼原則機制。</span><span class="sxs-lookup"><span data-stu-id="5909b-147">SQL Server provides Windows password policy mechanisms for SQL Server logins.</span></span> <span data-ttu-id="5909b-148">密碼複雜性原則是為了阻止暴力攻擊而設計，方法是盡可能地增加密碼數目。</span><span class="sxs-lookup"><span data-stu-id="5909b-148">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="5909b-149">SQL Server 可以將相同的複雜性和到期原則套用至 SQL Server 內使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="5909b-149">SQL Server can apply the same complexity and expiration policies to passwords used inside SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5909b-150">串連來自使用者輸入的連接字串，可能會讓您容易受到連接字串插入式攻擊。</span><span class="sxs-lookup"><span data-stu-id="5909b-150">Concatenating connection strings from user input can leave you vulnerable to a connection string injection attack.</span></span> <span data-ttu-id="5909b-151">在執行階段，使用 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 來建立語法正確的連接字串。</span><span class="sxs-lookup"><span data-stu-id="5909b-151">Use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="5909b-152">如需詳細資訊，請參閱[連接字串建置器](../connection-string-builders.md)。</span><span class="sxs-lookup"><span data-stu-id="5909b-152">For more information, see [Connection String Builders](../connection-string-builders.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="5909b-153">外部資源</span><span class="sxs-lookup"><span data-stu-id="5909b-153">External Resources</span></span>  
 <span data-ttu-id="5909b-154">如需詳細資訊，請參閱下列資源。</span><span class="sxs-lookup"><span data-stu-id="5909b-154">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="5909b-155">資源</span><span class="sxs-lookup"><span data-stu-id="5909b-155">Resource</span></span>|<span data-ttu-id="5909b-156">描述</span><span class="sxs-lookup"><span data-stu-id="5909b-156">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="5909b-157">Principals</span><span class="sxs-lookup"><span data-stu-id="5909b-157">Principals</span></span>](/sql/relational-databases/security/authentication-access/principals-database-engine)|<span data-ttu-id="5909b-158">說明 SQL Server 中的登入及其他安全性主體。</span><span class="sxs-lookup"><span data-stu-id="5909b-158">Describes logins and other security principals in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5909b-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5909b-159">See also</span></span>

- [<span data-ttu-id="5909b-160">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="5909b-160">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="5909b-161">SQL Server 中的應用程式安全性案例</span><span class="sxs-lookup"><span data-stu-id="5909b-161">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="5909b-162">連接到資料來源</span><span class="sxs-lookup"><span data-stu-id="5909b-162">Connecting to a Data Source</span></span>](../connecting-to-a-data-source.md)
- [<span data-ttu-id="5909b-163">連接字串</span><span class="sxs-lookup"><span data-stu-id="5909b-163">Connection Strings</span></span>](../connection-strings.md)
- <span data-ttu-id="5909b-164">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="5909b-164">[ADO.NET Overview](../ado-net-overview.md)</span></span>
