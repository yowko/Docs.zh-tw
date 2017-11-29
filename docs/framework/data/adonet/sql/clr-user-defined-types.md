---
title: "CLR 使用者定義類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e81cf54ed9dc516d88b8c7a97c8a5b33b8943d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="clr-user-defined-types"></a><span data-ttu-id="6c4be-102">CLR 使用者定義類型</span><span class="sxs-lookup"><span data-stu-id="6c4be-102">CLR User-Defined Types</span></span>
<span data-ttu-id="6c4be-103">Microsoft SQL Server 可支援以 Microsoft .NET Framework Common Language Runtime (CLR) 實作的使用者定義型別 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="6c4be-103">Microsoft SQL Server provides support for user-defined types (UDTs) implemented with the Microsoft .NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="6c4be-104">這項將 CLR 整合進 SQL Server 的機制可讓您擴充資料庫的型別系統。</span><span class="sxs-lookup"><span data-stu-id="6c4be-104">The CLR is integrated into SQL Server, and this mechanism enables you to extend the type system of the database.</span></span> <span data-ttu-id="6c4be-105">UDT 可讓使用者擴充 SQL Server 資料型別系統，以及定義複雜的結構化型別。</span><span class="sxs-lookup"><span data-stu-id="6c4be-105">UDTs provide user extensibility of the SQL Server data type system, and also the ability to define complex structured types.</span></span>  
  
 <span data-ttu-id="6c4be-106">從應用程式架構的角度來看，UDT 有兩個主要優點：</span><span class="sxs-lookup"><span data-stu-id="6c4be-106">UDTs can provide two key benefits from an application architecture perspective:</span></span>  
  
-   <span data-ttu-id="6c4be-107">(在用戶端及伺服器上) 強式封裝內部狀態與外部行為。</span><span class="sxs-lookup"><span data-stu-id="6c4be-107">Strong encapsulation (both in the client and the server) between the internal state and the external behaviors.</span></span>  
  
-   <span data-ttu-id="6c4be-108">與其他相關伺服器功能深度整合。</span><span class="sxs-lookup"><span data-stu-id="6c4be-108">Deep integration with other related server features.</span></span> <span data-ttu-id="6c4be-109">定義自己的 UDT 後，您可在 SQL Server 中所有可以使用系統型別的內容中使用它，包括資料行定義以及做為變數、參數、函式結果、游標、觸發程序及複寫。</span><span class="sxs-lookup"><span data-stu-id="6c4be-109">Once you define your own UDT, you can use it in all contexts where you can use a system type in SQL Server, including column definitions, and as variables, parameters, function results, cursors, triggers, and replication.</span></span>  
  
 <span data-ttu-id="6c4be-110">如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。</span><span class="sxs-lookup"><span data-stu-id="6c4be-110">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="6c4be-111">**SQL Server 線上叢書**</span><span class="sxs-lookup"><span data-stu-id="6c4be-111">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="6c4be-112">CLR 使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="6c4be-112">CLR User-Defined Types</span></span>](http://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="see-also"></a><span data-ttu-id="6c4be-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c4be-113">See Also</span></span>  
 [<span data-ttu-id="6c4be-114">在 Managed 程式碼中建立 SQL Server 2005 物件</span><span class="sxs-lookup"><span data-stu-id="6c4be-114">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="6c4be-115">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="6c4be-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
