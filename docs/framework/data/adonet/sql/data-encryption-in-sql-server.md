---
title: "在 SQL Server 中加密資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83b992f7-b351-4678-b4b9-f4ffd58134cc
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4ea062a65f250a3532249783b0c7b147ed460317
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="data-encryption-in-sql-server"></a><span data-ttu-id="9963f-102">在 SQL Server 中加密資料</span><span class="sxs-lookup"><span data-stu-id="9963f-102">Data Encryption in SQL Server</span></span>
<span data-ttu-id="9963f-103">SQL Server 提供使用憑證、非對稱金鑰或對稱金鑰來加密及解密資料的功能，</span><span class="sxs-lookup"><span data-stu-id="9963f-103">SQL Server provides functions to encrypt and decrypt data using a certificate, asymmetric key, or symmetric key.</span></span> <span data-ttu-id="9963f-104">而且可在內部的憑證存放區內管理上述所有項目。</span><span class="sxs-lookup"><span data-stu-id="9963f-104">It manages all of these in an internal certificate store.</span></span> <span data-ttu-id="9963f-105">此存放區會使用加密階層，藉由階層中的上層層級來確保下層層級的憑證及金鑰。</span><span class="sxs-lookup"><span data-stu-id="9963f-105">The store uses an encryption hierarchy that secures certificates and keys at one level with the layer above it in the hierarchy.</span></span> <span data-ttu-id="9963f-106">SQL Server 的此功能區也稱為「秘密儲存區」(Secret Storage)。</span><span class="sxs-lookup"><span data-stu-id="9963f-106">This feature area of SQL Server is called Secret Storage.</span></span>  
  
 <span data-ttu-id="9963f-107">由加密功能所支援的最快加密模式是對稱金鑰加密。</span><span class="sxs-lookup"><span data-stu-id="9963f-107">The fastest mode of encryption supported by the encryption functions is symmetric key encryption.</span></span> <span data-ttu-id="9963f-108">此模式適合用來處理大量的資料。</span><span class="sxs-lookup"><span data-stu-id="9963f-108">This mode is suitable for handling large volumes of data.</span></span> <span data-ttu-id="9963f-109">對稱金鑰可以藉由憑證、密碼或其他對稱金鑰進行加密。</span><span class="sxs-lookup"><span data-stu-id="9963f-109">The symmetric keys can be encrypted by certificates, passwords or other symmetric keys.</span></span>  
  
## <a name="keys-and-algorithms"></a><span data-ttu-id="9963f-110">金鑰和演算法</span><span class="sxs-lookup"><span data-stu-id="9963f-110">Keys and Algorithms</span></span>  
 <span data-ttu-id="9963f-111">SQL Server 支援數種對稱金鑰加密演算法，包括 DES、Triple DES、RC2、RC4、128 位元 RC4、DESX、128 位元 AES、192 位元 AES 和 256 位元 AES 等，</span><span class="sxs-lookup"><span data-stu-id="9963f-111">SQL Server supports several symmetric key encryption algorithms, including DES, Triple DES, RC2, RC4, 128-bit RC4, DESX, 128-bit AES, 192-bit AES, and 256-bit AES.</span></span> <span data-ttu-id="9963f-112">這些演算法是使用 Windows Crypto API 來實作。</span><span class="sxs-lookup"><span data-stu-id="9963f-112">The algorithms are implemented using the Windows Crypto API.</span></span>  
  
 <span data-ttu-id="9963f-113">SQL Server 可在資料庫連接的範圍內維護多個開放式的對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="9963f-113">Within the scope of a database connection, SQL Server can maintain multiple open symmetric keys.</span></span> <span data-ttu-id="9963f-114">您可從存放區擷取開放式金鑰，並將其用於解密資料。</span><span class="sxs-lookup"><span data-stu-id="9963f-114">An open key is retrieved from the store and is available for decrypting data.</span></span> <span data-ttu-id="9963f-115">在資料解密後，就不需指定要使用的對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="9963f-115">When a piece of data is decrypted, there is no need to specify the symmetric key to use.</span></span> <span data-ttu-id="9963f-116">每個加密的值都包含加密時所使用金鑰的識別碼 (金鑰 GUID)。</span><span class="sxs-lookup"><span data-stu-id="9963f-116">Each encrypted value contains the key identifier (key GUID) of the key used to encrypt it.</span></span> <span data-ttu-id="9963f-117">如果已解密並開啟了正確的金鑰，則引擎會比對加密的位元組資料流與開放式對稱金鑰，</span><span class="sxs-lookup"><span data-stu-id="9963f-117">The engine matches the encrypted byte stream to an open symmetric key, if the correct key has been decrypted and is open.</span></span> <span data-ttu-id="9963f-118">然後再使用此金鑰來執行解密作業並傳回資料。</span><span class="sxs-lookup"><span data-stu-id="9963f-118">This key is then used to perform decryption and return the data.</span></span> <span data-ttu-id="9963f-119">如果沒有開啟正確的金鑰，則會傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="9963f-119">If the correct key is not open, NULL is returned.</span></span>  
  
 <span data-ttu-id="9963f-120">如需示範如何使用資料庫中的加密資料的範例，請參閱[如何： 加密資料行的資料](http://go.microsoft.com/fwlink/?LinkID=128559)SQL Server 線上叢書 》 中。</span><span class="sxs-lookup"><span data-stu-id="9963f-120">For an example that shows how to work with encrypted data in a database, see [How to: Encrypt a Column of Data](http://go.microsoft.com/fwlink/?LinkID=128559) in SQL Server Books Online.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="9963f-121">外部資源</span><span class="sxs-lookup"><span data-stu-id="9963f-121">External Resources</span></span>  
 <span data-ttu-id="9963f-122">如需有關資料加密的詳細資訊，請參閱下列資源。</span><span class="sxs-lookup"><span data-stu-id="9963f-122">For more information on data encryption, see the following resources.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9963f-123">[SQL Server 加密](http://msdn.microsoft.com/library/bb510663.aspx)SQL Server 線上叢書中</span><span class="sxs-lookup"><span data-stu-id="9963f-123">[SQL Server Encryption](http://msdn.microsoft.com/library/bb510663.aspx) in SQL Server Books Online</span></span>|<span data-ttu-id="9963f-124">提供 SQL Server 中的加密概觀。</span><span class="sxs-lookup"><span data-stu-id="9963f-124">Provides an overview of encryption in SQL Serve.</span></span> <span data-ttu-id="9963f-125">此主題包含其他主題和「如何」文件的連結。</span><span class="sxs-lookup"><span data-stu-id="9963f-125">This topic includes links to additional topics and how-to's.</span></span>|  
|<span data-ttu-id="9963f-126">[加密階層](http://msdn.microsoft.com/library/ms189586.aspx)和[加密的如何主題](http://msdn.microsoft.com/library/aa337557.aspx)SQL Server 線上叢書中</span><span class="sxs-lookup"><span data-stu-id="9963f-126">[Encryption Hierarchy](http://msdn.microsoft.com/library/ms189586.aspx) and [Encryption How-to Topics](http://msdn.microsoft.com/library/aa337557.aspx) in SQL Server Books Online</span></span>|<span data-ttu-id="9963f-127">提供 SQL Server 中的加密概觀。</span><span class="sxs-lookup"><span data-stu-id="9963f-127">Provides an overview of encryption in SQL Server.</span></span> <span data-ttu-id="9963f-128">此主題包含其他主題和「如何」文件的連結。</span><span class="sxs-lookup"><span data-stu-id="9963f-128">This topic provides links to additional topics and how-to's.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9963f-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="9963f-129">See Also</span></span>  
 [<span data-ttu-id="9963f-130">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="9963f-130">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="9963f-131">SQL Server 中的應用程式安全性案例</span><span class="sxs-lookup"><span data-stu-id="9963f-131">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="9963f-132">在 SQL Server 中進行驗證</span><span class="sxs-lookup"><span data-stu-id="9963f-132">Authentication in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [<span data-ttu-id="9963f-133">SQL Server 中的伺服器和資料庫角色</span><span class="sxs-lookup"><span data-stu-id="9963f-133">Server and Database Roles in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [<span data-ttu-id="9963f-134">SQL Server 中的擁有權和使用者結構描述分離</span><span class="sxs-lookup"><span data-stu-id="9963f-134">Ownership and User-Schema Separation in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [<span data-ttu-id="9963f-135">SQL Server 中的授權和權限</span><span class="sxs-lookup"><span data-stu-id="9963f-135">Authorization and Permissions in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [<span data-ttu-id="9963f-136">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="9963f-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
