---
title: SQL Server 安全性概觀
description: 瞭解 SQL Server 的安全性架構，以瞭解哪些功能和功能會影響已知的威脅，以及預測未來的威脅。
ms.date: 03/30/2017
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
ms.openlocfilehash: c423a408e607c51c048ad08b91122a1fe06e31b2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286271"
---
# <a name="overview-of-sql-server-security"></a><span data-ttu-id="cce33-103">SQL Server 安全性概觀</span><span class="sxs-lookup"><span data-stu-id="cce33-103">Overview of SQL Server Security</span></span>
<span data-ttu-id="cce33-104">具有重疊安全性層的深入防禦策略是抵禦安全性威脅的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="cce33-104">A defense-in-depth strategy, with overlapping layers of security, is the best way to counter security threats.</span></span> <span data-ttu-id="cce33-105">SQL Server 提供了一種安全性架構，其設計目的是為了允許資料庫管理員和開發人員建立安全的資料庫應用程式並抵禦威脅。</span><span class="sxs-lookup"><span data-stu-id="cce33-105">SQL Server provides a security architecture that is designed to allow database administrators and developers to create secure database applications and counter threats.</span></span> <span data-ttu-id="cce33-106">每個 SQL Server 版本都會透過引進新的特性和功能來改善舊版 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="cce33-106">Each version of SQL Server has improved on previous versions of SQL Server with the introduction of new features and functionality.</span></span> <span data-ttu-id="cce33-107">不過，安全性無法一體適用。</span><span class="sxs-lookup"><span data-stu-id="cce33-107">However, security does not ship in the box.</span></span> <span data-ttu-id="cce33-108">每個應用程式的安全性需求都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="cce33-108">Each application is unique in its security requirements.</span></span> <span data-ttu-id="cce33-109">開發人員必須瞭解哪些特性和功能的組合最適合用來抵禦已知威脅，以及預期未來可能會發生的威脅。</span><span class="sxs-lookup"><span data-stu-id="cce33-109">Developers need to understand which combination of features and functionality are most appropriate to counter known threats, and to anticipate threats that may arise in the future.</span></span>  
  
 <span data-ttu-id="cce33-110">SQL Server 執行個體包含階層式實體 (Entity) 集合，從伺服器開始。</span><span class="sxs-lookup"><span data-stu-id="cce33-110">A SQL Server instance contains a hierarchical collection of entities, starting with the server.</span></span> <span data-ttu-id="cce33-111">每個伺服器都包含多個資料庫，而每個資料庫都包含安全性實體物件的集合。</span><span class="sxs-lookup"><span data-stu-id="cce33-111">Each server contains multiple databases, and each database contains a collection of securable objects.</span></span> <span data-ttu-id="cce33-112">每個 SQL Server 安全性實體都有相關聯的*許可權*，可授與*主體*，也就是授與 SQL Server 存取權的個人、群組或進程。</span><span class="sxs-lookup"><span data-stu-id="cce33-112">Every SQL Server securable has associated *permissions* that can be granted to a *principal*, which is an individual, group or process granted access to SQL Server.</span></span> <span data-ttu-id="cce33-113">SQL Server 安全性架構會透過*驗證*和*授權*來管理安全實體的存取權。</span><span class="sxs-lookup"><span data-stu-id="cce33-113">The SQL Server security framework manages access to securable entities through *authentication* and *authorization*.</span></span>  
  
- <span data-ttu-id="cce33-114">驗證是指登入 SQL Server 的程序，其中主體會透過提交伺服器評估的認證來要求存取。</span><span class="sxs-lookup"><span data-stu-id="cce33-114">Authentication is the process of logging on to SQL Server by which a principal requests access by submitting credentials that the server evaluates.</span></span> <span data-ttu-id="cce33-115">驗證會建立正在進行驗證之使用者或處理序的識別。</span><span class="sxs-lookup"><span data-stu-id="cce33-115">Authentication establishes the identity of the user or process being authenticated.</span></span>  
  
- <span data-ttu-id="cce33-116">授權是決定主體可存取哪些安全性實體資源，以及可對這些資源執行哪些作業的程序。</span><span class="sxs-lookup"><span data-stu-id="cce33-116">Authorization is the process of determining which securable resources a principal can access, and which operations are allowed for those resources.</span></span>  
  
 <span data-ttu-id="cce33-117">本節中的主題涵蓋了 SQL Server 安全性基本概念，並提供《SQL Server 線上叢書》相關版本中完整文件的連結。</span><span class="sxs-lookup"><span data-stu-id="cce33-117">The topics in this section cover SQL Server security fundamentals, providing links to the complete documentation in the relevant version of SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cce33-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="cce33-118">In This Section</span></span>  
 [<span data-ttu-id="cce33-119">在 SQL Server 中進行驗證</span><span class="sxs-lookup"><span data-stu-id="cce33-119">Authentication in SQL Server</span></span>](authentication-in-sql-server.md)  
 <span data-ttu-id="cce33-120">描述 SQL Server 中的登入和驗證，並提供其他資源的連結。</span><span class="sxs-lookup"><span data-stu-id="cce33-120">Describes logins and authentication in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="cce33-121">SQL Server 中的伺服器和資料庫角色</span><span class="sxs-lookup"><span data-stu-id="cce33-121">Server and Database Roles in SQL Server</span></span>](server-and-database-roles-in-sql-server.md)  
 <span data-ttu-id="cce33-122">說明固定伺服器和資料庫角色、自訂資料庫角色和內建帳戶，並提供其他資源的連結。</span><span class="sxs-lookup"><span data-stu-id="cce33-122">Describes fixed server and database roles, custom database roles, and built-in accounts and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="cce33-123">SQL Server 中的擁有權和使用者結構描述分離</span><span class="sxs-lookup"><span data-stu-id="cce33-123">Ownership and User-Schema Separation in SQL Server</span></span>](ownership-and-user-schema-separation-in-sql-server.md)  
 <span data-ttu-id="cce33-124">說明物件擁有權和使用者結構描述分隔，並提供其他資源的連結。</span><span class="sxs-lookup"><span data-stu-id="cce33-124">Describes object ownership and  user-schema separation and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="cce33-125">SQL Server 中的授權和權限</span><span class="sxs-lookup"><span data-stu-id="cce33-125">Authorization and Permissions in SQL Server</span></span>](authorization-and-permissions-in-sql-server.md)  
 <span data-ttu-id="cce33-126">說明如何使用最小權限的原則來授與權限，並提供其他資源的連結。</span><span class="sxs-lookup"><span data-stu-id="cce33-126">Describes granting permissions using the principle of least privilege and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="cce33-127">在 SQL Server 中加密資料</span><span class="sxs-lookup"><span data-stu-id="cce33-127">Data Encryption in SQL Server</span></span>](data-encryption-in-sql-server.md)  
 <span data-ttu-id="cce33-128">說明 SQL Server 中的資料加密選項，並提供其他資源的連結。</span><span class="sxs-lookup"><span data-stu-id="cce33-128">Describes data encryption options in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="cce33-129">SQL Server 中的 CLR 整合安全性</span><span class="sxs-lookup"><span data-stu-id="cce33-129">CLR Integration Security in SQL Server</span></span>](clr-integration-security-in-sql-server.md)  
 <span data-ttu-id="cce33-130">提供 CLR 整合安全性資源的連結。</span><span class="sxs-lookup"><span data-stu-id="cce33-130">Provides links to CLR integration security resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cce33-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cce33-131">See also</span></span>

- [<span data-ttu-id="cce33-132">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="cce33-132">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="cce33-133">SQL Server 安全性</span><span class="sxs-lookup"><span data-stu-id="cce33-133">SQL Server Security</span></span>](sql-server-security.md)
- [<span data-ttu-id="cce33-134">SQL Server 中的應用程式安全性案例</span><span class="sxs-lookup"><span data-stu-id="cce33-134">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- <span data-ttu-id="cce33-135">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="cce33-135">[ADO.NET Overview](../ado-net-overview.md)</span></span>
