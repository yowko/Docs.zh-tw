---
title: SQL Server 安全性概觀
ms.date: 03/30/2017
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
ms.openlocfilehash: adc1ce661d49c468de09552ea36a2cd58d6343f1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780946"
---
# <a name="overview-of-sql-server-security"></a><span data-ttu-id="cbb02-102">SQL Server 安全性概觀</span><span class="sxs-lookup"><span data-stu-id="cbb02-102">Overview of SQL Server Security</span></span>
<span data-ttu-id="cbb02-103">具有重疊安全性層的深入防禦策略是抵禦安全性威脅的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="cbb02-103">A defense-in-depth strategy, with overlapping layers of security, is the best way to counter security threats.</span></span> <span data-ttu-id="cbb02-104">SQL Server 提供了一種安全性架構，其設計目的是為了允許資料庫管理員和開發人員建立安全的資料庫應用程式並抵禦威脅。</span><span class="sxs-lookup"><span data-stu-id="cbb02-104">SQL Server provides a security architecture that is designed to allow database administrators and developers to create secure database applications and counter threats.</span></span> <span data-ttu-id="cbb02-105">每個 SQL Server 版本都會透過引進新的特性和功能來改善舊版 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="cbb02-105">Each version of SQL Server has improved on previous versions of SQL Server with the introduction of new features and functionality.</span></span> <span data-ttu-id="cbb02-106">不過，安全性無法一體適用。</span><span class="sxs-lookup"><span data-stu-id="cbb02-106">However, security does not ship in the box.</span></span> <span data-ttu-id="cbb02-107">每個應用程式的安全性需求都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="cbb02-107">Each application is unique in its security requirements.</span></span> <span data-ttu-id="cbb02-108">開發人員必須瞭解哪些特性和功能的組合最適合用來抵禦已知威脅，以及預期未來可能會發生的威脅。</span><span class="sxs-lookup"><span data-stu-id="cbb02-108">Developers need to understand which combination of features and functionality are most appropriate to counter known threats, and to anticipate threats that may arise in the future.</span></span>  
  
 <span data-ttu-id="cbb02-109">SQL Server 執行個體包含階層式實體 (Entity) 集合，從伺服器開始。</span><span class="sxs-lookup"><span data-stu-id="cbb02-109">A SQL Server instance contains a hierarchical collection of entities, starting with the server.</span></span> <span data-ttu-id="cbb02-110">每個伺服器都包含多個資料庫，而每個資料庫都包含安全性實體物件的集合。</span><span class="sxs-lookup"><span data-stu-id="cbb02-110">Each server contains multiple databases, and each database contains a collection of securable objects.</span></span> <span data-ttu-id="cbb02-111">每個 SQL Server 安全性實體都有相關聯的*許可權*，可授與*主體*，也就是授與 SQL Server 存取權的個人、群組或進程。</span><span class="sxs-lookup"><span data-stu-id="cbb02-111">Every SQL Server securable has associated *permissions* that can be granted to a *principal*, which is an individual, group or process granted access to SQL Server.</span></span> <span data-ttu-id="cbb02-112">SQL Server 安全性架構會透過*驗證*和*授權*來管理安全實體的存取權。</span><span class="sxs-lookup"><span data-stu-id="cbb02-112">The SQL Server security framework manages access to securable entities through *authentication* and *authorization*.</span></span>  
  
- <span data-ttu-id="cbb02-113">驗證是指登入 SQL Server 的程序，其中主體會透過提交伺服器評估的認證來要求存取。</span><span class="sxs-lookup"><span data-stu-id="cbb02-113">Authentication is the process of logging on to SQL Server by which a principal requests access by submitting credentials that the server evaluates.</span></span> <span data-ttu-id="cbb02-114">驗證會建立正在進行驗證之使用者或處理序的識別。</span><span class="sxs-lookup"><span data-stu-id="cbb02-114">Authentication establishes the identity of the user or process being authenticated.</span></span>  
  
- <span data-ttu-id="cbb02-115">授權是指決定主體可存取哪些安全性實體資源，以及允許針對這些資源進行哪些作業的程序。</span><span class="sxs-lookup"><span data-stu-id="cbb02-115">Authorization is the process of determining which securable resources a principal can access, and which operations are allowed for those resources.</span></span>  
  
 <span data-ttu-id="cbb02-116">本節中的主題涵蓋了 SQL Server 安全性基本概念，並提供《SQL Server 線上叢書》相關版本中完整文件的連結。</span><span class="sxs-lookup"><span data-stu-id="cbb02-116">The topics in this section cover SQL Server security fundamentals, providing links to the complete documentation in the relevant version of SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cbb02-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="cbb02-117">In This Section</span></span>  
 [<span data-ttu-id="cbb02-118">在 SQL Server 中進行驗證</span><span class="sxs-lookup"><span data-stu-id="cbb02-118">Authentication in SQL Server</span></span>](authentication-in-sql-server.md)  
 <span data-ttu-id="cbb02-119">說明 SQL Server 中的登入和驗證，並提供其他資源的連結。</span><span class="sxs-lookup"><span data-stu-id="cbb02-119">Describes logins and authentication in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="cbb02-120">SQL Server 中的伺服器和資料庫角色</span><span class="sxs-lookup"><span data-stu-id="cbb02-120">Server and Database Roles in SQL Server</span></span>](server-and-database-roles-in-sql-server.md)  
 <span data-ttu-id="cbb02-121">說明固定伺服器和資料庫角色、自訂資料庫角色和內建帳戶，並提供其他資源的連結。</span><span class="sxs-lookup"><span data-stu-id="cbb02-121">Describes fixed server and database roles, custom database roles, and built-in accounts and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="cbb02-122">SQL Server 中的擁有權和使用者結構描述分離</span><span class="sxs-lookup"><span data-stu-id="cbb02-122">Ownership and User-Schema Separation in SQL Server</span></span>](ownership-and-user-schema-separation-in-sql-server.md)  
 <span data-ttu-id="cbb02-123">說明物件擁有權和使用者結構描述分隔，並提供其他資源的連結。</span><span class="sxs-lookup"><span data-stu-id="cbb02-123">Describes object ownership and  user-schema separation and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="cbb02-124">SQL Server 中的授權和權限</span><span class="sxs-lookup"><span data-stu-id="cbb02-124">Authorization and Permissions in SQL Server</span></span>](authorization-and-permissions-in-sql-server.md)  
 <span data-ttu-id="cbb02-125">說明如何使用最小權限的原則來授與權限，並提供其他資源的連結。</span><span class="sxs-lookup"><span data-stu-id="cbb02-125">Describes granting permissions using the principle of least privilege and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="cbb02-126">在 SQL Server 中加密資料</span><span class="sxs-lookup"><span data-stu-id="cbb02-126">Data Encryption in SQL Server</span></span>](data-encryption-in-sql-server.md)  
 <span data-ttu-id="cbb02-127">說明 SQL Server 中的資料加密選項，並提供其他資源的連結。</span><span class="sxs-lookup"><span data-stu-id="cbb02-127">Describes data encryption options in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="cbb02-128">SQL Server 中的 CLR 整合安全性</span><span class="sxs-lookup"><span data-stu-id="cbb02-128">CLR Integration Security in SQL Server</span></span>](clr-integration-security-in-sql-server.md)  
 <span data-ttu-id="cbb02-129">提供 CLR 整合安全性資源的連結。</span><span class="sxs-lookup"><span data-stu-id="cbb02-129">Provides links to CLR integration security resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb02-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbb02-130">See also</span></span>

- [<span data-ttu-id="cbb02-131">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="cbb02-131">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="cbb02-132">SQL Server 安全性</span><span class="sxs-lookup"><span data-stu-id="cbb02-132">SQL Server Security</span></span>](sql-server-security.md)
- [<span data-ttu-id="cbb02-133">SQL Server 中的應用程式安全性案例</span><span class="sxs-lookup"><span data-stu-id="cbb02-133">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="cbb02-134">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="cbb02-134">ADO.NET Overview</span></span>](../ado-net-overview.md)
