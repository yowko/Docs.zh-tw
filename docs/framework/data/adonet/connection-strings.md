---
title: ADO.NET 中的連接字串
ms.date: 03/30/2017
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 1e6e2b6870195c99279639e1f4576a30b7126d4d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583682"
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="1c3db-102">ADO.NET 中的連接字串</span><span class="sxs-lookup"><span data-stu-id="1c3db-102">Connection Strings in ADO.NET</span></span>
<span data-ttu-id="1c3db-103">.NET Framework 2.0 導入了使用連接字串的新功能，包括在連接字串產生器 (Builder) 類別 (Class) 中引入新的關鍵字，這麼做可在執行階段建立有效的連接字串。</span><span class="sxs-lookup"><span data-stu-id="1c3db-103">The .NET Framework 2.0 introduced new capabilities for working with connection strings, including the introduction of new keywords to the connection string builder classes, which facilitate creating valid connection strings at run time.</span></span>  
  
<span data-ttu-id="1c3db-104">連接字串 (Connection String) 包含可當做參數從資料提供者 (Data Provider) 傳遞至資料來源的初始化資訊。</span><span class="sxs-lookup"><span data-stu-id="1c3db-104">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="1c3db-105">此語法會因資料提供者而不同，而且連接字串會在嘗試開啟連接期間進行剖析。</span><span class="sxs-lookup"><span data-stu-id="1c3db-105">The syntax depends on the data provider, and the connection string is parsed during the attempt to open a connection.</span></span> <span data-ttu-id="1c3db-106">語法錯誤會產生執行階段例外狀況 (Exception)，但其他錯誤只會發生在資料來源接收連接資訊之後。</span><span class="sxs-lookup"><span data-stu-id="1c3db-106">Syntax errors generate a run-time exception, but other errors occur only after the data source receives connection information.</span></span> <span data-ttu-id="1c3db-107">經過驗證後，資料來源便可套用在連接字串中指定的選項並開啟連接。</span><span class="sxs-lookup"><span data-stu-id="1c3db-107">Once validated, the data source applies the options specified in the connection string and opens the connection.</span></span>
  
<span data-ttu-id="1c3db-108">連接字串的格式是分號分隔的索引鍵/值參數組清單：</span><span class="sxs-lookup"><span data-stu-id="1c3db-108">The format of a connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>
  
    keyword1=value; keyword2=value;
  
<span data-ttu-id="1c3db-109">關鍵字不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="1c3db-109">Keywords are not case-sensitive.</span></span> <span data-ttu-id="1c3db-110">值，不過，可能會區分大小寫，根據資料來源。</span><span class="sxs-lookup"><span data-stu-id="1c3db-110">Values, however, may be case-sensitive, depending on the data source.</span></span> <span data-ttu-id="1c3db-111">關鍵字和值可能會包含[空白字元](https://en.wikipedia.org/wiki/Whitespace_character#Unicode)，但忽略關鍵字中並不具引號的開頭和尾端空白字元的值。</span><span class="sxs-lookup"><span data-stu-id="1c3db-111">Both keywords and values may contain [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character#Unicode), although leading and trailing whitespace is ignored in keywords and unquoted values.</span></span>

<span data-ttu-id="1c3db-112">如果值包含分號[Unicode 控制字元](https://en.wikipedia.org/wiki/Unicode_control_characters)、 開頭或結尾的空白字元，它必須以單引號或雙引號括住，例如：</span><span class="sxs-lookup"><span data-stu-id="1c3db-112">If a value contains the semicolon, [Unicode control characters](https://en.wikipedia.org/wiki/Unicode_control_characters), leading or trailing whitespace it must be enclosed in single or double quotation marks, e.g.:</span></span>

    Keyword=" whitespace  ";
    Keyword='special;character';

<span data-ttu-id="1c3db-113">封入字元可能不會發生在其所包圍的值。</span><span class="sxs-lookup"><span data-stu-id="1c3db-113">The enclosing character may not occur within the value it encloses.</span></span> <span data-ttu-id="1c3db-114">因此，只有在雙引號，反之亦然，可以用包含單引號的值：</span><span class="sxs-lookup"><span data-stu-id="1c3db-114">Therefore, a value containing single quotation marks can be enclosed only in double quotation marks and vice versa:</span></span>

    Keyword='double"quotation;mark';
    Keyword="single'quotation;mark";

<span data-ttu-id="1c3db-115">引號本身，以及在等號，不需要逸出，因此下列連接字串是有效：</span><span class="sxs-lookup"><span data-stu-id="1c3db-115">The quotation marks themselves, as well as the equals sign, do not require escaping, so the following connection strings are valid:</span></span>

    Keyword=no "escaping" 'required';
    Keyword=a=b=c

<span data-ttu-id="1c3db-116">直到下一步 以分號或字串的結尾會讀取每個值，因為第二個範例中的值是`a=b=c`，最後的分號則是選擇性。</span><span class="sxs-lookup"><span data-stu-id="1c3db-116">Since each value is read till the next semicolon or the end of string, the value in the latter example is `a=b=c`, and the final semicolon is optional.</span></span>

<span data-ttu-id="1c3db-117">有效的連接字串語法隨提供者而異，且是從早期的 API (如 ODBC) 經過多年不斷發展而來的。</span><span class="sxs-lookup"><span data-stu-id="1c3db-117">Valid connection string syntax depends on the provider, and has evolved over the years from earlier APIs like ODBC.</span></span> <span data-ttu-id="1c3db-118">.NET Framework Data Provider for SQL Server (SqlClient) 納入了許多舊式語法項目，而且對一般連接字串語法通常都可接受。</span><span class="sxs-lookup"><span data-stu-id="1c3db-118">The .NET Framework Data Provider for SQL Server (SqlClient) incorporates many elements from older syntax and is generally more flexible with common connection string syntax.</span></span> <span data-ttu-id="1c3db-119">連接字串語法項目經常會有同等效力的同義資料表 (Synonym)，但某些語法和拼字錯誤可能會導致問題。</span><span class="sxs-lookup"><span data-stu-id="1c3db-119">There are frequently equally valid synonyms for connection string syntax elements, but some syntax and spelling errors can cause problems.</span></span> <span data-ttu-id="1c3db-120">例如，"`Integrated Security=true`" 有效，"`IntegratedSecurity=true`" 則會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="1c3db-120">For example, "`Integrated Security=true`" is valid, whereas "`IntegratedSecurity=true`" causes an error.</span></span> <span data-ttu-id="1c3db-121">此外，在執行階段自未經驗證的使用者輸入所建構的連接字串可能會導致字串插入式攻擊，進而危及資料來源的安全性。</span><span class="sxs-lookup"><span data-stu-id="1c3db-121">In addition, connection strings constructed at run time from unvalidated user input can lead to string injection attacks, jeopardizing security at the data source.</span></span>
  
<span data-ttu-id="1c3db-122">為了解決這些問題，ADO.NET 2.0 針對每個 .NET Framework 資料提供者導入新的連接字串產生器。</span><span class="sxs-lookup"><span data-stu-id="1c3db-122">To address these problems, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="1c3db-123">關鍵字會以屬性的方式公開 (Expose)，如此就可在將連接字串提交至資料來源之前先驗證字串語法。</span><span class="sxs-lookup"><span data-stu-id="1c3db-123">Keywords are exposed as properties, enabling connection string syntax to be validated before submission to the data source.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="1c3db-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="1c3db-124">In This Section</span></span>  
 [<span data-ttu-id="1c3db-125">連接字串產生器</span><span class="sxs-lookup"><span data-stu-id="1c3db-125">Connection String Builders</span></span>](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 <span data-ttu-id="1c3db-126">示範如何使用 `ConnectionStringBuilder` 類別在執行階段建構有效的連接字串。</span><span class="sxs-lookup"><span data-stu-id="1c3db-126">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>
  
 [<span data-ttu-id="1c3db-127">連接字串和組態檔</span><span class="sxs-lookup"><span data-stu-id="1c3db-127">Connection Strings and Configuration Files</span></span>](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 <span data-ttu-id="1c3db-128">示範如何在組態檔中儲存及擷取連接字串。</span><span class="sxs-lookup"><span data-stu-id="1c3db-128">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>
  
 [<span data-ttu-id="1c3db-129">連接字串語法</span><span class="sxs-lookup"><span data-stu-id="1c3db-129">Connection String Syntax</span></span>](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 <span data-ttu-id="1c3db-130">說明如何針對`SqlClient`、`OracleClient`、`OleDb` 和 `Odbc` 設定提供者專用的連接字串。</span><span class="sxs-lookup"><span data-stu-id="1c3db-130">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>
  
 [<span data-ttu-id="1c3db-131">保護連線資訊</span><span class="sxs-lookup"><span data-stu-id="1c3db-131">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 <span data-ttu-id="1c3db-132">示範的技術可保護用於連接至資料來源的資訊。</span><span class="sxs-lookup"><span data-stu-id="1c3db-132">Demonstrates techniques for protecting information used to connect to a data source.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1c3db-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c3db-133">See Also</span></span>  
 [<span data-ttu-id="1c3db-134">連接至資料來源</span><span class="sxs-lookup"><span data-stu-id="1c3db-134">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)  
 [<span data-ttu-id="1c3db-135">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="1c3db-135">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
