---
title: CLR 使用者定義類型
ms.date: 03/30/2017
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
ms.openlocfilehash: b946a87e49d8bf496fb215eb95f9db9cb453c13c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878094"
---
# <a name="clr-user-defined-types"></a><span data-ttu-id="a4415-102">CLR 使用者定義類型</span><span class="sxs-lookup"><span data-stu-id="a4415-102">CLR User-Defined Types</span></span>
<span data-ttu-id="a4415-103">Microsoft SQL Server 可支援以 Microsoft .NET Framework Common Language Runtime (CLR) 實作的使用者定義型別 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="a4415-103">Microsoft SQL Server provides support for user-defined types (UDTs) implemented with the Microsoft .NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="a4415-104">這項將 CLR 整合進 SQL Server 的機制可讓您擴充資料庫的型別系統。</span><span class="sxs-lookup"><span data-stu-id="a4415-104">The CLR is integrated into SQL Server, and this mechanism enables you to extend the type system of the database.</span></span> <span data-ttu-id="a4415-105">UDT 可讓使用者擴充 SQL Server 資料型別系統，以及定義複雜的結構化型別。</span><span class="sxs-lookup"><span data-stu-id="a4415-105">UDTs provide user extensibility of the SQL Server data type system, and also the ability to define complex structured types.</span></span>  
  
 <span data-ttu-id="a4415-106">從應用程式架構的角度來看，UDT 有兩個主要優點：</span><span class="sxs-lookup"><span data-stu-id="a4415-106">UDTs can provide two key benefits from an application architecture perspective:</span></span>  
  
-   <span data-ttu-id="a4415-107">(在用戶端及伺服器上) 強式封裝內部狀態與外部行為。</span><span class="sxs-lookup"><span data-stu-id="a4415-107">Strong encapsulation (both in the client and the server) between the internal state and the external behaviors.</span></span>  
  
-   <span data-ttu-id="a4415-108">與其他相關伺服器功能深度整合。</span><span class="sxs-lookup"><span data-stu-id="a4415-108">Deep integration with other related server features.</span></span> <span data-ttu-id="a4415-109">定義自己的 UDT 後，您可在 SQL Server 中所有可以使用系統型別的內容中使用它，包括資料行定義以及做為變數、參數、函式結果、游標、觸發程序及複寫。</span><span class="sxs-lookup"><span data-stu-id="a4415-109">Once you define your own UDT, you can use it in all contexts where you can use a system type in SQL Server, including column definitions, and as variables, parameters, function results, cursors, triggers, and replication.</span></span>  
  
 <span data-ttu-id="a4415-110">如需詳細資訊，請參閱 < [SQL Server 文件](/sql)您使用的 SQL Server 的版本。</span><span class="sxs-lookup"><span data-stu-id="a4415-110">For more detailed information, see the [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="a4415-111">**SQL Server 文件**</span><span class="sxs-lookup"><span data-stu-id="a4415-111">**SQL Server documentation**</span></span>
  
1. [<span data-ttu-id="a4415-112">CLR 使用者定義類型</span><span class="sxs-lookup"><span data-stu-id="a4415-112">CLR User-Defined Types</span></span>](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="see-also"></a><span data-ttu-id="a4415-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4415-113">See also</span></span>

- [<span data-ttu-id="a4415-114">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="a4415-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
