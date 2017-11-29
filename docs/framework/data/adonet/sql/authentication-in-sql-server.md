---
title: "在 SQL Server 中進行驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e3b597d04ee53a094d9c50dff406f57e5fd57b00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="authentication-in-sql-server"></a><span data-ttu-id="c5dea-102">在 SQL Server 中進行驗證</span><span class="sxs-lookup"><span data-stu-id="c5dea-102">Authentication in SQL Server</span></span>
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="c5dea-103"> 支援兩種驗證模式：Windows 驗證模式和混合模式。</span><span class="sxs-lookup"><span data-stu-id="c5dea-103"> supports two authentication modes, Windows authentication mode and mixed mode.</span></span>  
  
-   <span data-ttu-id="c5dea-104">Windows 驗證是預設設定，也經常稱為整合式安全性，因為這個 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 安全性模型會與 Windows 緊密整合。</span><span class="sxs-lookup"><span data-stu-id="c5dea-104">Windows authentication is the default, and is often referred to as integrated security because this [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] security model is tightly integrated with Windows.</span></span> <span data-ttu-id="c5dea-105">特定的 Windows 使用者和群組帳戶會受信任而可登入 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="c5dea-105">Specific Windows user and group accounts are trusted to log in to SQL Server.</span></span> <span data-ttu-id="c5dea-106">已經過驗證的 Windows 使用者不必再提供額外認證資料。</span><span class="sxs-lookup"><span data-stu-id="c5dea-106">Windows users who have already been authenticated do not have to present additional credentials.</span></span>  
  
-   <span data-ttu-id="c5dea-107">混合模式支援 Windows 和 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 提供的驗證。</span><span class="sxs-lookup"><span data-stu-id="c5dea-107">Mixed mode supports authentication both by Windows and by [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c5dea-108">使用者名稱和密碼組會在 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 內進行維護。</span><span class="sxs-lookup"><span data-stu-id="c5dea-108">User name and password pairs are maintained within [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c5dea-109">建議盡量使用「Windows 驗證」。</span><span class="sxs-lookup"><span data-stu-id="c5dea-109">We recommend using Windows authentication wherever possible.</span></span> <span data-ttu-id="c5dea-110">Windows 驗證會使用一系列的加密訊息在 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 中驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="c5dea-110">Windows authentication uses a series of encrypted messages to authenticate users in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c5dea-111">使用 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 登入時，[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 登入名稱及密碼會透過網路傳遞，因而降低其安全性。</span><span class="sxs-lookup"><span data-stu-id="c5dea-111">When [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] logins are used, [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] login names and passwords are passed across the network, which makes them less secure.</span></span>  
  
 <span data-ttu-id="c5dea-112">使用 Windows 驗證的好處是因為使用者已登入 Windows，所以不必再另行登入 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c5dea-112">With Windows authentication, users are already logged onto Windows and do not have to log on separately to [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c5dea-113">下列 `SqlConnection.ConnectionString` 可指定 Windows 驗證，且不需要使用者名稱或密碼。</span><span class="sxs-lookup"><span data-stu-id="c5dea-113">The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring the a user name or password.</span></span>  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
>  <span data-ttu-id="c5dea-114">登入不同於資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="c5dea-114">Logins are distinct from database users.</span></span> <span data-ttu-id="c5dea-115">您必須藉由個別作業，將登入或 Windows 群組對應到資料庫使用者或角色。</span><span class="sxs-lookup"><span data-stu-id="c5dea-115">You must map logins or Windows groups to database users or roles in a separate operation.</span></span> <span data-ttu-id="c5dea-116">接著再將存取資料庫物件的權限授與使用者或角色。</span><span class="sxs-lookup"><span data-stu-id="c5dea-116">You then grant permissions to users or roles to access database objects.</span></span>  
  
## <a name="authentication-scenarios"></a><span data-ttu-id="c5dea-117">驗證案例</span><span class="sxs-lookup"><span data-stu-id="c5dea-117">Authentication Scenarios</span></span>  
 <span data-ttu-id="c5dea-118">在下列情況中，Windows 驗證通常是最佳選擇：</span><span class="sxs-lookup"><span data-stu-id="c5dea-118">Windows authentication is usually the best choice in the following situations:</span></span>  
  
-   <span data-ttu-id="c5dea-119">有網域控制站存在。</span><span class="sxs-lookup"><span data-stu-id="c5dea-119">There is a domain controller.</span></span>  
  
-   <span data-ttu-id="c5dea-120">應用程式和資料庫位於相同的電腦。</span><span class="sxs-lookup"><span data-stu-id="c5dea-120">The application and the database are on the same computer.</span></span>  
  
-   <span data-ttu-id="c5dea-121">您使用的是 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express 或 LocalDB 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c5dea-121">You are using an instance of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express or LocalDB.</span></span>  
  
 <span data-ttu-id="c5dea-122">SQL Server 登入通常用於以下狀況：</span><span class="sxs-lookup"><span data-stu-id="c5dea-122">SQL Server logins are often used in the following situations:</span></span>  
  
-   <span data-ttu-id="c5dea-123">如果您擁有工作群組。</span><span class="sxs-lookup"><span data-stu-id="c5dea-123">If you have a workgroup.</span></span>  
  
-   <span data-ttu-id="c5dea-124">使用者是自不同的非受信任網域進行連接。</span><span class="sxs-lookup"><span data-stu-id="c5dea-124">Users connect from different, non-trusted domains.</span></span>  
  
-   <span data-ttu-id="c5dea-125">網際網路應用程式，例如 [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c5dea-125">Internet applications, such as [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5dea-126">指定 Windows 驗證並不會停用 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="c5dea-126">Specifying Windows authentication does not disable [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] logins.</span></span> <span data-ttu-id="c5dea-127">請使用 ALTER LOGIN DISABLE [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] 陳述式來停用具有高權限的 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="c5dea-127">Use the ALTER LOGIN DISABLE [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statement to disable highly-privileged [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] logins.</span></span>  
  
## <a name="login-types"></a><span data-ttu-id="c5dea-128">登入類型</span><span class="sxs-lookup"><span data-stu-id="c5dea-128">Login Types</span></span>  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="c5dea-129"> 支援三種登入型別：</span><span class="sxs-lookup"><span data-stu-id="c5dea-129"> supports three types of logins:</span></span>  
  
-   <span data-ttu-id="c5dea-130">本機 Windows 使用者帳戶或受信任的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="c5dea-130">A local Windows user account or trusted domain account.</span></span> [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="c5dea-131"> 會仰賴 Windows 來驗證 Windows 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="c5dea-131"> relies on Windows to authenticate the Windows user accounts.</span></span>  
  
-   <span data-ttu-id="c5dea-132">Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="c5dea-132">Windows group.</span></span> <span data-ttu-id="c5dea-133">如果授與存取權給 Windows 群組，則也會授權給全部該群組成員的 Windows 使用者登入。</span><span class="sxs-lookup"><span data-stu-id="c5dea-133">Granting access to a Windows group grants access to all Windows user logins that are members of the group.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="c5dea-134"> 登入。</span><span class="sxs-lookup"><span data-stu-id="c5dea-134"> login.</span></span> [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="c5dea-135"> 會將使用者名稱和密碼雜湊儲存在 master 資料庫，並使用內部驗證方法確認登入作業。</span><span class="sxs-lookup"><span data-stu-id="c5dea-135"> stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="c5dea-136"> 提供從憑證建立的登入或非對稱金鑰，這些只能用於程式碼簽章，</span><span class="sxs-lookup"><span data-stu-id="c5dea-136"> provides logins created from certificates or asymmetric keys that are used only for code signing.</span></span> <span data-ttu-id="c5dea-137">而不會用來連接至 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c5dea-137">They cannot be used to connect to [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="mixed-mode-authentication"></a><span data-ttu-id="c5dea-138">混合模式驗證</span><span class="sxs-lookup"><span data-stu-id="c5dea-138">Mixed Mode Authentication</span></span>  
 <span data-ttu-id="c5dea-139">如果您必須使用混合模式驗證，則必須建立儲存在 SQL Server 中的 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="c5dea-139">If you must use mixed mode authentication, you must create [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] logins, which are stored in SQL Server.</span></span> <span data-ttu-id="c5dea-140">然後在執行階段時還需要提供 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="c5dea-140">You then have to supply the [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] user name and password at run time.</span></span>  
  
> [!IMPORTANT]
>  [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="c5dea-141"> 會使用名為 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] (「系統管理員」的縮寫) 的 `sa` 登入來進行安裝。</span><span class="sxs-lookup"><span data-stu-id="c5dea-141"> installs with a [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] login named `sa` (an abbreviation of "system administrator").</span></span> <span data-ttu-id="c5dea-142">請指派強式密碼給 `sa` 登入，且不要在應用程式中使用 `sa` 登入。</span><span class="sxs-lookup"><span data-stu-id="c5dea-142">Assign a strong password to the `sa` login and do not use the `sa` login in your application.</span></span> <span data-ttu-id="c5dea-143">`sa` 登入對應的是 `sysadmin` 固定伺服器角色，對於整個伺服器具有不可變更之管理權限。</span><span class="sxs-lookup"><span data-stu-id="c5dea-143">The `sa` login maps to the `sysadmin` fixed server role, which has irrevocable administrative credentials on the whole server.</span></span> <span data-ttu-id="c5dea-144">如果攻擊者取得系統管理員的存取權，就可以大肆破壞而毫不受限。</span><span class="sxs-lookup"><span data-stu-id="c5dea-144">There are no limits to the potential damage if an attacker gains access as a system administrator.</span></span> <span data-ttu-id="c5dea-145">Windows `BUILTIN\Administrators` 群組 (本機系統管理員群組) 的所有成員，都會預設為 `sysadmin` 角色的成員，但可以從該角色移除。</span><span class="sxs-lookup"><span data-stu-id="c5dea-145">All members of the Windows `BUILTIN\Administrators` group (the local administrator's group) are members of the `sysadmin` role by default, but can be removed from that role.</span></span>  
  
 <span data-ttu-id="c5dea-146">當 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 是在 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 或更新版本上執行時，就可以提供 [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] 登入適用的 Windows 密碼原則機制。</span><span class="sxs-lookup"><span data-stu-id="c5dea-146">[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] provides Windows password policy mechanisms for [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] logins when it is running on [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] or later versions.</span></span> <span data-ttu-id="c5dea-147">密碼複雜性原則是為了阻止暴力攻擊而設計，方法是盡可能地增加密碼數目。</span><span class="sxs-lookup"><span data-stu-id="c5dea-147">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="c5dea-148"> 可以將 [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] 中所使用的相同複雜度與期限原則套用至 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 內所使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="c5dea-148"> can apply the same complexity and expiration policies used in [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] to passwords used inside [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c5dea-149">串連來自使用者輸入的連接字串，可能會使您易遭受連接字串插入式攻擊。</span><span class="sxs-lookup"><span data-stu-id="c5dea-149">Concatenating connection strings from user input can leave you vulnerable to a connection string injection attack.</span></span> <span data-ttu-id="c5dea-150">請使用 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 在執行階段建立語法有效的連接字串。</span><span class="sxs-lookup"><span data-stu-id="c5dea-150">Use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="c5dea-151">如需詳細資訊，請參閱[連接字串產生器](../../../../../docs/framework/data/adonet/connection-string-builders.md)。</span><span class="sxs-lookup"><span data-stu-id="c5dea-151">For more information, see [Connection String Builders](../../../../../docs/framework/data/adonet/connection-string-builders.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="c5dea-152">外部資源</span><span class="sxs-lookup"><span data-stu-id="c5dea-152">External Resources</span></span>  
 <span data-ttu-id="c5dea-153">如需詳細資訊，請參閱下列資源。</span><span class="sxs-lookup"><span data-stu-id="c5dea-153">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="c5dea-154">資源</span><span class="sxs-lookup"><span data-stu-id="c5dea-154">Resource</span></span>|<span data-ttu-id="c5dea-155">說明</span><span class="sxs-lookup"><span data-stu-id="c5dea-155">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="c5dea-156">[主體](http://msdn.microsoft.com/library/bb543165.aspx)中[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]線上叢書 》</span><span class="sxs-lookup"><span data-stu-id="c5dea-156">[Principals](http://msdn.microsoft.com/library/bb543165.aspx) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online</span></span>|<span data-ttu-id="c5dea-157">說明 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 中的登入和其他安全性主體。</span><span class="sxs-lookup"><span data-stu-id="c5dea-157">Describes logins and other security principals in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5dea-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5dea-158">See Also</span></span>  
 [<span data-ttu-id="c5dea-159">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="c5dea-159">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="c5dea-160">SQL Server 中的應用程式安全性案例</span><span class="sxs-lookup"><span data-stu-id="c5dea-160">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="c5dea-161">連接至資料來源</span><span class="sxs-lookup"><span data-stu-id="c5dea-161">Connecting to a Data Source</span></span>](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="c5dea-162">連接字串</span><span class="sxs-lookup"><span data-stu-id="c5dea-162">Connection Strings</span></span>](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="c5dea-163">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="c5dea-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
