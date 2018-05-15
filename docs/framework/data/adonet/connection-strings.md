---
title: ADO.NET 中的連接字串
ms.date: 03/30/2017
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 03d768430139fa1078f39b470403abcf75dd83a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="5ec26-102">ADO.NET 中的連接字串</span><span class="sxs-lookup"><span data-stu-id="5ec26-102">Connection Strings in ADO.NET</span></span>
<span data-ttu-id="5ec26-103">.NET Framework 2.0 導入了使用連接字串的新功能，包括在連接字串產生器 (Builder) 類別 (Class) 中引入新的關鍵字，這麼做可在執行階段建立有效的連接字串。</span><span class="sxs-lookup"><span data-stu-id="5ec26-103">The .NET Framework 2.0 introduced new capabilities for working with connection strings, including the introduction of new keywords to the connection string builder classes, which facilitate creating valid connection strings at run time.</span></span>  
  
 <span data-ttu-id="5ec26-104">連接字串 (Connection String) 包含可當做參數從資料提供者 (Data Provider) 傳遞至資料來源的初始化資訊。</span><span class="sxs-lookup"><span data-stu-id="5ec26-104">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="5ec26-105">此語法會因資料提供者而不同，而且連接字串會在嘗試開啟連接期間進行剖析。</span><span class="sxs-lookup"><span data-stu-id="5ec26-105">The syntax depends on the data provider, and the connection string is parsed during the attempt to open a connection.</span></span> <span data-ttu-id="5ec26-106">語法錯誤會產生執行階段例外狀況 (Exception)，但其他錯誤只會發生在資料來源接收連接資訊之後。</span><span class="sxs-lookup"><span data-stu-id="5ec26-106">Syntax errors generate a run-time exception, but other errors occur only after the data source receives connection information.</span></span> <span data-ttu-id="5ec26-107">經過驗證後，資料來源便可套用在連接字串中指定的選項並開啟連接。</span><span class="sxs-lookup"><span data-stu-id="5ec26-107">Once validated, the data source applies the options specified in the connection string and opens the connection.</span></span>  
  
 <span data-ttu-id="5ec26-108">連接字串的格式是分號分隔的索引鍵/值參數組清單：</span><span class="sxs-lookup"><span data-stu-id="5ec26-108">The format of a connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>  
  
 `keyword1=value; keyword2=value;`  
  
 <span data-ttu-id="5ec26-109">關鍵字不區分大小寫，而且索引鍵/值組之間的空格會被忽略。</span><span class="sxs-lookup"><span data-stu-id="5ec26-109">Keywords are not case sensitive, and spaces between key/value pairs are ignored.</span></span> <span data-ttu-id="5ec26-110">不過，依照資料來源的不同，值可能會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="5ec26-110">However, values may be case sensitive, depending on the data source.</span></span> <span data-ttu-id="5ec26-111">所有包含分號、單引號或雙引號的值，都必須用雙引號括住。</span><span class="sxs-lookup"><span data-stu-id="5ec26-111">Any values containing a semicolon, single quotation marks, or double quotation marks must be enclosed in double quotation marks.</span></span>  
  
 <span data-ttu-id="5ec26-112">有效的連接字串語法隨提供者而異，且是從早期的 API (如 ODBC) 經過多年不斷發展而來的。</span><span class="sxs-lookup"><span data-stu-id="5ec26-112">Valid connection string syntax depends on the provider, and has evolved over the years from earlier APIs like ODBC.</span></span> <span data-ttu-id="5ec26-113">.NET Framework Data Provider for SQL Server (SqlClient) 納入了許多舊式語法項目，而且對一般連接字串語法通常都可接受。</span><span class="sxs-lookup"><span data-stu-id="5ec26-113">The .NET Framework Data Provider for SQL Server (SqlClient) incorporates many elements from older syntax and is generally more flexible with common connection string syntax.</span></span> <span data-ttu-id="5ec26-114">連接字串語法項目經常會有同等效力的同義資料表 (Synonym)，但某些語法和拼字錯誤可能會導致問題。</span><span class="sxs-lookup"><span data-stu-id="5ec26-114">There are frequently equally valid synonyms for connection string syntax elements, but some syntax and spelling errors can cause problems.</span></span> <span data-ttu-id="5ec26-115">例如，"`Integrated Security=true`" 有效，"`IntegratedSecurity=true`" 則會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="5ec26-115">For example, "`Integrated Security=true`" is valid, whereas "`IntegratedSecurity=true`" causes an error.</span></span> <span data-ttu-id="5ec26-116">此外，在執行階段自未經驗證的使用者輸入所建構的連接字串可能會導致字串插入式攻擊，進而危及資料來源的安全性。</span><span class="sxs-lookup"><span data-stu-id="5ec26-116">In addition, connection strings constructed at run time from unvalidated user input can lead to string injection attacks, jeopardizing security at the data source.</span></span>  
  
 <span data-ttu-id="5ec26-117">為了解決這些問題，ADO.NET 2.0 針對每個 .NET Framework 資料提供者導入新的連接字串產生器。</span><span class="sxs-lookup"><span data-stu-id="5ec26-117">To address these problems, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="5ec26-118">關鍵字會以屬性的方式公開 (Expose)，如此就可在將連接字串提交至資料來源之前先驗證字串語法。</span><span class="sxs-lookup"><span data-stu-id="5ec26-118">Keywords are exposed as properties, enabling connection string syntax to be validated before submission to the data source.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ec26-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="5ec26-119">In This Section</span></span>  
 [<span data-ttu-id="5ec26-120">連接字串產生器</span><span class="sxs-lookup"><span data-stu-id="5ec26-120">Connection String Builders</span></span>](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 <span data-ttu-id="5ec26-121">示範如何使用 `ConnectionStringBuilder` 類別在執行階段建構有效的連接字串。</span><span class="sxs-lookup"><span data-stu-id="5ec26-121">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>  
  
 [<span data-ttu-id="5ec26-122">連接字串和組態檔</span><span class="sxs-lookup"><span data-stu-id="5ec26-122">Connection Strings and Configuration Files</span></span>](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 <span data-ttu-id="5ec26-123">示範如何在組態檔中儲存及擷取連接字串。</span><span class="sxs-lookup"><span data-stu-id="5ec26-123">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>  
  
 [<span data-ttu-id="5ec26-124">連接字串語法</span><span class="sxs-lookup"><span data-stu-id="5ec26-124">Connection String Syntax</span></span>](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 <span data-ttu-id="5ec26-125">說明如何針對`SqlClient`、`OracleClient`、`OleDb` 和 `Odbc` 設定提供者專用的連接字串。</span><span class="sxs-lookup"><span data-stu-id="5ec26-125">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>  
  
 [<span data-ttu-id="5ec26-126">保護連線資訊</span><span class="sxs-lookup"><span data-stu-id="5ec26-126">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 <span data-ttu-id="5ec26-127">示範的技術可保護用於連接至資料來源的資訊。</span><span class="sxs-lookup"><span data-stu-id="5ec26-127">Demonstrates techniques for protecting information used to connect to a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ec26-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ec26-128">See Also</span></span>  
 [<span data-ttu-id="5ec26-129">連接至資料來源</span><span class="sxs-lookup"><span data-stu-id="5ec26-129">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)  
 [<span data-ttu-id="5ec26-130">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="5ec26-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
