---
title: SQL Server 安全性
ms.date: 03/30/2017
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
ms.openlocfilehash: 5db14e681b5a9445c034be60993661a61a038e08
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177302"
---
# <a name="sql-server-security"></a><span data-ttu-id="634fe-102">SQL Server 安全性</span><span class="sxs-lookup"><span data-stu-id="634fe-102">SQL Server Security</span></span>

<span data-ttu-id="634fe-103">SQL Server 具有許多功能，可支援安全資料庫應用程式的建立。</span><span class="sxs-lookup"><span data-stu-id="634fe-103">SQL Server has many features that support creating secure database applications.</span></span>  
  
 <span data-ttu-id="634fe-104">資料竊取或破壞等一般的安全性考量，則適用於所使用的 SQL Server 版本。</span><span class="sxs-lookup"><span data-stu-id="634fe-104">Common security considerations, such as data theft or vandalism, apply regardless of the version of SQL Server you are using.</span></span> <span data-ttu-id="634fe-105">資料完整性也應被視為安全性問題。</span><span class="sxs-lookup"><span data-stu-id="634fe-105">Data integrity should also be considered as a security issue.</span></span> <span data-ttu-id="634fe-106">若資料未受到保護，那麼，如果允許進行特定的資料操作，並且利用不正確的值意外或惡意地修改資料或將其完全刪除，則它可能就會變得毫無價值。</span><span class="sxs-lookup"><span data-stu-id="634fe-106">If data is not protected, it is possible that it could become worthless if ad hoc data manipulation is permitted and the data is inadvertently or maliciously modified with incorrect values or deleted entirely.</span></span> <span data-ttu-id="634fe-107">此外，通常還必須遵守法律需求，例如正確儲存機密資訊。</span><span class="sxs-lookup"><span data-stu-id="634fe-107">In addition, there are often legal requirements that must be adhered to, such as the correct storage of confidential information.</span></span> <span data-ttu-id="634fe-108">視特定管轄區所適用的法律而定，會完全禁止儲存某些類型的個人資料。</span><span class="sxs-lookup"><span data-stu-id="634fe-108">Storing some kinds of personal data is proscribed entirely, depending on the laws that apply in a particular jurisdiction.</span></span>  
  
 <span data-ttu-id="634fe-109">每個 SQL Server 版本和每個 Windows 版本一樣，都具有不同的安全性功能，而越新的版本功能越強。</span><span class="sxs-lookup"><span data-stu-id="634fe-109">Each version of SQL Server has different security features, as does each version of Windows, with later versions having enhanced functionality over earlier ones.</span></span> <span data-ttu-id="634fe-110">請務必了解，安全性功能本身無法保證安全的資料庫應用程式。</span><span class="sxs-lookup"><span data-stu-id="634fe-110">It is important to understand that security features alone cannot guarantee a secure database application.</span></span> <span data-ttu-id="634fe-111">每個資料庫應用程式在其需求、執行環境、部署模型、實體位置及使用者群體中都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="634fe-111">Each database application is unique in its requirements, execution environment, deployment model, physical location, and user population.</span></span> <span data-ttu-id="634fe-112">範圍內的某些本機應用程式可能只需要最低的安全性，而透過網際網路部署的其他本機應用程式或應用程式可能就需要嚴格的安全性措施以及持續的監視和評估。</span><span class="sxs-lookup"><span data-stu-id="634fe-112">Some applications that are local in scope may need only minimal security whereas other local applications or applications deployed over the Internet may require stringent security measures and ongoing monitoring and evaluation.</span></span>  
  
 <span data-ttu-id="634fe-113">您應該在設計階段就考量 SQL Server 資料庫應用程式的安全性需求，而不是事後才加以考量。</span><span class="sxs-lookup"><span data-stu-id="634fe-113">The security requirements of a SQL Server database application should be considered at design time, not as an afterthought.</span></span> <span data-ttu-id="634fe-114">在開發週期的早期評估威脅，可讓您有機會減輕偵測到弱點之處所受到的潛在損害。</span><span class="sxs-lookup"><span data-stu-id="634fe-114">Evaluating threats early in the development cycle gives you the opportunity to mitigate potential damage wherever a vulnerability is detected.</span></span>  
  
 <span data-ttu-id="634fe-115">即使應用程式的初始設計很健全，但隨著系統的發展，可能就會出現新的威脅。</span><span class="sxs-lookup"><span data-stu-id="634fe-115">Even if the initial design of an application is sound, new threats may emerge as the system evolves.</span></span> <span data-ttu-id="634fe-116">藉由在資料庫周圍建立多道防線，您就能將安全性缺口所造成的損害降到最低。</span><span class="sxs-lookup"><span data-stu-id="634fe-116">By creating multiple lines of defense around your database, you can minimize the damage inflicted by a security breach.</span></span> <span data-ttu-id="634fe-117">您的第一道防線是減少受攻擊面的範圍，除非絕對必要，否則不要授與權限。</span><span class="sxs-lookup"><span data-stu-id="634fe-117">Your first line of defense is to reduce the attack surface area by never to granting more permissions than are absolutely necessary.</span></span>  
  
 <span data-ttu-id="634fe-118">本節中的主題簡要說明與開發人員相關的 SQL Server 安全性功能，並提供連結至《SQL Server 線上叢書》中相關主題的連結，以及提供更深入探討的其他資源。</span><span class="sxs-lookup"><span data-stu-id="634fe-118">The topics in this section briefly describe the security features in SQL Server that are relevant for developers, with links to relevant topics in SQL Server Books Online and other resources that provide more detailed coverage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="634fe-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="634fe-119">In This Section</span></span>  

 [<span data-ttu-id="634fe-120">SQL Server 安全性概觀</span><span class="sxs-lookup"><span data-stu-id="634fe-120">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)  
 <span data-ttu-id="634fe-121">說明 SQL Server 的架構和安全性功能。</span><span class="sxs-lookup"><span data-stu-id="634fe-121">Describes the architecture and security features of SQL Server.</span></span>  
  
 [<span data-ttu-id="634fe-122">SQL Server 中的應用程式安全性案例</span><span class="sxs-lookup"><span data-stu-id="634fe-122">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)  
 <span data-ttu-id="634fe-123">包含討論 ADO.NET 和 SQL Server 應用程式之各種應用程式安全性案例的主題。</span><span class="sxs-lookup"><span data-stu-id="634fe-123">Contains topics discussing various application security scenarios for ADO.NET and SQL Server applications.</span></span>  
  
 [<span data-ttu-id="634fe-124">SQL Server Express 安全性</span><span class="sxs-lookup"><span data-stu-id="634fe-124">SQL Server Express Security</span></span>](sql-server-express-security.md)  
 <span data-ttu-id="634fe-125">說明 SQL Server Express 的安全性考量。</span><span class="sxs-lookup"><span data-stu-id="634fe-125">Describes security considerations for SQL Server Express.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="634fe-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="634fe-126">Related Sections</span></span>  

[<span data-ttu-id="634fe-127">SQL Server Database Engine 和 Azure SQL Database 的資訊安全中心</span><span class="sxs-lookup"><span data-stu-id="634fe-127">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
<span data-ttu-id="634fe-128">描述 SQL Server 和 Azure SQL Database 的安全性考量。</span><span class="sxs-lookup"><span data-stu-id="634fe-128">Describes security considerations for SQL Server and Azure SQL Database.</span></span>

[<span data-ttu-id="634fe-129">SQL Server 安裝的安全性考量</span><span class="sxs-lookup"><span data-stu-id="634fe-129">Security Considerations for a SQL Server Installation</span></span>](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
<span data-ttu-id="634fe-130">描述安裝 SQL Server 之前要考慮的安全性考量。</span><span class="sxs-lookup"><span data-stu-id="634fe-130">Describes security concerns to consider before installing SQL Server.</span></span>

## <a name="see-also"></a><span data-ttu-id="634fe-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="634fe-131">See also</span></span>

- [<span data-ttu-id="634fe-132">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="634fe-132">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- <span data-ttu-id="634fe-133">[SQL Server and ADO.NET](index.md) (SQL Server 和 ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="634fe-133">[SQL Server and ADO.NET](index.md)</span></span>
