---
title: 連接字串與連接字串名稱
ms.date: 03/30/2017
ms.assetid: 473e7a3c-c88a-4a01-914a-bea82ba42866
ms.openlocfilehash: ab063710dcf5705fdb0055e34ea57fe24da891a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511926"
---
# <a name="connection-string-and-connection-string-name"></a><span data-ttu-id="cce63-102">連接字串與連接字串名稱</span><span class="sxs-lookup"><span data-stu-id="cce63-102">Connection String and Connection String Name</span></span>
<span data-ttu-id="cce63-103">**連接字串**屬性指定 SQL 工作流程執行個體存放區應用於連接持續性資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="cce63-103">**Connection String** property specifies the connection string that the SQL Workflow Instance Store should use to connect to a persistence database.</span></span> <span data-ttu-id="cce63-104">這個參數是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="cce63-104">This parameter is an optional parameter.</span></span> <span data-ttu-id="cce63-105">**連接字串名稱**屬性會指定 SQL 工作流程執行個體存放區應用於連接持續性資料庫之具名的連接字串名稱。</span><span class="sxs-lookup"><span data-stu-id="cce63-105">**Connection String Name** property specifies the name of the named connection string that the SQL Workflow Instance Store should use to connect to the persistence database.</span></span> <span data-ttu-id="cce63-106">這個參數是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="cce63-106">This parameter is an optional parameter.</span></span> <span data-ttu-id="cce63-107">您應該指定連接字串名稱屬性或連接字串屬性的值，如果您不想要使用預設的具名連接字串的 SQL 工作流程執行個體存放區**DefaultSqlWorkflowInstanceStoreConnectionString**.</span><span class="sxs-lookup"><span data-stu-id="cce63-107">You should specify a value for the Connection String Name property or the Connection String property if you do not want the SQL Workflow Instance Store to use the default named connection string **DefaultSqlWorkflowInstanceStoreConnectionString**.</span></span>
