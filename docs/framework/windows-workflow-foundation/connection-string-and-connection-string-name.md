---
title: 連接字串與連接字串名稱
ms.date: 03/30/2017
ms.assetid: 473e7a3c-c88a-4a01-914a-bea82ba42866
ms.openlocfilehash: 5352dbac09565e872493581a2809409b156d1300
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248860"
---
# <a name="connection-string-and-connection-string-name"></a><span data-ttu-id="4776e-102">連接字串與連接字串名稱</span><span class="sxs-lookup"><span data-stu-id="4776e-102">Connection String and Connection String Name</span></span>

<span data-ttu-id="4776e-103">**連接字串** 屬性會指定 SQL 工作流程實例存放區用來連接至持續性資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="4776e-103">**Connection String** property specifies the connection string that the SQL Workflow Instance Store should use to connect to a persistence database.</span></span> <span data-ttu-id="4776e-104">這個參數是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="4776e-104">This parameter is an optional parameter.</span></span> <span data-ttu-id="4776e-105">[**連接字串名稱**] 屬性會指定 SQL 工作流程實例存放區用來連接持續性資料庫的命名連接字串名稱。</span><span class="sxs-lookup"><span data-stu-id="4776e-105">**Connection String Name** property specifies the name of the named connection string that the SQL Workflow Instance Store should use to connect to the persistence database.</span></span> <span data-ttu-id="4776e-106">這個參數是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="4776e-106">This parameter is an optional parameter.</span></span> <span data-ttu-id="4776e-107">如果您不想讓 SQL 工作流程實例存放區使用預設的命名連接字串 **DefaultSqlWorkflowInstanceStoreConnectionString**，則應該指定 [連接字串名稱] 屬性的值或 [連接字串] 屬性。</span><span class="sxs-lookup"><span data-stu-id="4776e-107">You should specify a value for the Connection String Name property or the Connection String property if you do not want the SQL Workflow Instance Store to use the default named connection string **DefaultSqlWorkflowInstanceStoreConnectionString**.</span></span>
