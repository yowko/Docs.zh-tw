---
title: 連接字串產生器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: afafe5d1eaddaef3b9f0069908b365e40ea4ed29
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785690"
---
# <a name="connection-string-builders"></a><span data-ttu-id="02cef-102">連接字串產生器</span><span class="sxs-lookup"><span data-stu-id="02cef-102">Connection String Builders</span></span>
<span data-ttu-id="02cef-103">在舊版的 ADO.NET 中，不會發生具有串連字號串值之連接字串的編譯階段檢查，因此在執行時間，不正確的關鍵字會產生<xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="02cef-103">In earlier versions of ADO.NET, compile-time checking of connection strings with concatenated string values did not occur, so that at run time, an incorrect keyword generated an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="02cef-104">.NET Framework 的每個資料提供者都支援不同的連接字串關鍵字語法，這會在手動完成時，讓建立有效的連接字串變得不容易。</span><span class="sxs-lookup"><span data-stu-id="02cef-104">Each of the .NET Framework data providers supported different syntax for connection string keywords, which made constructing valid connection strings difficult if done manually.</span></span> <span data-ttu-id="02cef-105">為了解決這個問題，ADO.NET 2.0 為每個 .NET Framework Data Provider 引進了新的連接字串產生器。</span><span class="sxs-lookup"><span data-stu-id="02cef-105">To address this problem, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="02cef-106">每個資料提供者都具有繼承自 <xref:System.Data.Common.DbConnectionStringBuilder> 強型別連接字串產生器類別。</span><span class="sxs-lookup"><span data-stu-id="02cef-106">Each data provider includes a strongly typed connection string builder class that inherits from <xref:System.Data.Common.DbConnectionStringBuilder>.</span></span> <span data-ttu-id="02cef-107">下表列出 .NET Framework 資料提供者及其相關聯的連接字串產生器類別。</span><span class="sxs-lookup"><span data-stu-id="02cef-107">The following table lists the .NET Framework data providers and their associated connection string builder classes.</span></span>  
  
|<span data-ttu-id="02cef-108">提供者</span><span class="sxs-lookup"><span data-stu-id="02cef-108">Provider</span></span>|<span data-ttu-id="02cef-109">ConnectionStringBuilder 類別</span><span class="sxs-lookup"><span data-stu-id="02cef-109">ConnectionStringBuilder class</span></span>|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a><span data-ttu-id="02cef-110">連接字串插入式攻擊</span><span class="sxs-lookup"><span data-stu-id="02cef-110">Connection String Injection Attacks</span></span>  
 <span data-ttu-id="02cef-111">當使用動態字串串連產生根據使用者輸入而來的連接字串時，就可能發生連接字串隱碼攻擊。</span><span class="sxs-lookup"><span data-stu-id="02cef-111">A connection string injection attack can occur when dynamic string concatenation is used to build connection strings that are based on user input.</span></span> <span data-ttu-id="02cef-112">如果字串未經驗證且未逸出惡意的文字或字元，攻擊者就可能得以存取伺服器上的機密資料或其他資源。</span><span class="sxs-lookup"><span data-stu-id="02cef-112">If the string is not validated and malicious text or characters not escaped, an attacker can potentially access sensitive data or other resources on the server.</span></span> <span data-ttu-id="02cef-113">例如，攻擊者可以藉由提供分號並附加額外的值而掛上 (Mount) 攻擊。</span><span class="sxs-lookup"><span data-stu-id="02cef-113">For example, an attacker could mount an attack by supplying a semicolon and appending an additional value.</span></span> <span data-ttu-id="02cef-114">連接字串會受到「最後一個設定」演算法剖析，而惡意的輸入值會取代合法的值。</span><span class="sxs-lookup"><span data-stu-id="02cef-114">The connection string is parsed by using a "last one wins" algorithm, and the hostile input is substituted for a legitimate value.</span></span>  
  
 <span data-ttu-id="02cef-115">連接字串產生器類別的目的是排除不確定性，並可防止語法錯誤和安全性漏洞。</span><span class="sxs-lookup"><span data-stu-id="02cef-115">The connection string builder classes are designed to eliminate guesswork and protect against syntax errors and security vulnerabilities.</span></span> <span data-ttu-id="02cef-116">此類別所提供的方法和屬性都對應於每個資料提供者所允許的已知索引鍵/值配對。</span><span class="sxs-lookup"><span data-stu-id="02cef-116">They provide methods and properties corresponding to the known key/value pairs permitted by each data provider.</span></span> <span data-ttu-id="02cef-117">每個類別都會維持固定的同義資料表 (Synonym) 集合，且可從同義資料表轉譯為相對應的已知索引鍵名稱。</span><span class="sxs-lookup"><span data-stu-id="02cef-117">Each class maintains a fixed collection of synonyms and can translate from a synonym to the corresponding well-known key name.</span></span> <span data-ttu-id="02cef-118">系統將針對有效的索引鍵/值組執行檢查，無效的索引鍵/值組將擲回例外狀況 (Exception)。</span><span class="sxs-lookup"><span data-stu-id="02cef-118">Checks are performed for valid key/value pairs and an invalid pair throws an exception.</span></span> <span data-ttu-id="02cef-119">此外，插入的值也會以安全的方式處理。</span><span class="sxs-lookup"><span data-stu-id="02cef-119">In addition, injected values are handled in a safe manner.</span></span>  
  
 <span data-ttu-id="02cef-120">下列範例示範 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 如何針對 `Initial Catalog` 設定而處理插入的額外值。</span><span class="sxs-lookup"><span data-stu-id="02cef-120">The following example demonstrates how the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handles an inserted extra value for the `Initial Catalog` setting.</span></span>  
  
```vb  
Dim builder As New System.Data.SqlClient.SqlConnectionStringBuilder  
builder("Data Source") = "(local)"  
builder("Integrated Security") = True  
builder("Initial Catalog") = "AdventureWorks;NewValue=Bad"  
Console.WriteLine(builder.ConnectionString)  
```  
  
```csharp  
System.Data.SqlClient.SqlConnectionStringBuilder builder =  
  new System.Data.SqlClient.SqlConnectionStringBuilder();  
builder["Data Source"] = "(local)";  
builder["integrated Security"] = true;  
builder["Initial Catalog"] = "AdventureWorks;NewValue=Bad";  
Console.WriteLine(builder.ConnectionString);  
```  
  
 <span data-ttu-id="02cef-121">輸出顯示上述情況的正確處理方式：<xref:System.Data.SqlClient.SqlConnectionStringBuilder> 以雙引號溢出額外值，而非以新的索引鍵/值組將該值附加到連接字串。</span><span class="sxs-lookup"><span data-stu-id="02cef-121">The output shows that the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handled this correctly by escaping the extra value in double quotation marks instead of appending it to the connection string as a new key/value pair.</span></span>  
  
```  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a><span data-ttu-id="02cef-122">從組態檔建置連接字串</span><span class="sxs-lookup"><span data-stu-id="02cef-122">Building Connection Strings from Configuration Files</span></span>  
 <span data-ttu-id="02cef-123">如果事先知道連接字串的特定項目，就可以先將其儲存在組態檔中，執行階段時再進行擷取，用以建構完整的連接字串。</span><span class="sxs-lookup"><span data-stu-id="02cef-123">If certain elements of a connection string are known beforehand, they can be stored in a configuration file and retrieved at run time to construct a complete connection string.</span></span> <span data-ttu-id="02cef-124">例如，您可能會預先知道資料庫的名稱，但不知道伺服器的名稱；</span><span class="sxs-lookup"><span data-stu-id="02cef-124">For example, the name of the database might be known in advance, but not the name of the server.</span></span> <span data-ttu-id="02cef-125">或者，也可以讓使用者在執行階段提供名稱和密碼，但不能將其他值插入連接字串。</span><span class="sxs-lookup"><span data-stu-id="02cef-125">Or you might want a user to supply a name and password at run time without being able to inject other values into the connection string.</span></span>  
  
 <span data-ttu-id="02cef-126">連接字串產生器其中一個多載建構函式會採用 <xref:System.String> 做為引數，這可讓您先提供部分連接字串，然後藉由使用者輸入完成。</span><span class="sxs-lookup"><span data-stu-id="02cef-126">One of the overloaded constructors for a connection string builder takes a <xref:System.String> as an argument, which enables you to supply a partial connection string that can then be completed from user input.</span></span> <span data-ttu-id="02cef-127">部分連接字串可以儲存在組態檔中，並在執行階段進行擷取。</span><span class="sxs-lookup"><span data-stu-id="02cef-127">The partial connection string can be stored in a configuration file and retrieved at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02cef-128"><xref:System.Configuration> 命名空間可讓您以程式設計方式存取使用 <xref:System.Web.Configuration.WebConfigurationManager> (Web 應用程式) 和 <xref:System.Configuration.ConfigurationManager> (Windows 應用程式) 的組態檔。</span><span class="sxs-lookup"><span data-stu-id="02cef-128">The <xref:System.Configuration> namespace allows programmatic access to configuration files that use the <xref:System.Web.Configuration.WebConfigurationManager> for Web applications and the <xref:System.Configuration.ConfigurationManager> for Windows applications.</span></span> <span data-ttu-id="02cef-129">如需使用連接字串和設定檔的詳細資訊，請參閱[連接字串和設定檔](connection-strings-and-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="02cef-129">For more information about working with connection strings and configuration files, see [Connection Strings and Configuration Files](connection-strings-and-configuration-files.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="02cef-130">範例</span><span class="sxs-lookup"><span data-stu-id="02cef-130">Example</span></span>  
 <span data-ttu-id="02cef-131">這個範例示範如何從組態檔擷取部分的連接字串，然後藉由設定 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> 的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>、<xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> 和 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 屬性加以完成。</span><span class="sxs-lookup"><span data-stu-id="02cef-131">This example demonstrates retrieving a partial connection string from a configuration file and completing it by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, and <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> properties of the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span> <span data-ttu-id="02cef-132">組態檔的定義如下。</span><span class="sxs-lookup"><span data-stu-id="02cef-132">The configuration file is defined as follows.</span></span>  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"   
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
> <span data-ttu-id="02cef-133">您必須在專案中將參考設定至 `System.Configuration.dll`，程式碼才能執行。</span><span class="sxs-lookup"><span data-stu-id="02cef-133">You must set a reference to the `System.Configuration.dll` in your project for the code to run.</span></span>  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="02cef-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02cef-134">See also</span></span>

- [<span data-ttu-id="02cef-135">連接字串</span><span class="sxs-lookup"><span data-stu-id="02cef-135">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="02cef-136">隱私權和資料安全性</span><span class="sxs-lookup"><span data-stu-id="02cef-136">Privacy and Data Security</span></span>](privacy-and-data-security.md)
- [<span data-ttu-id="02cef-137">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="02cef-137">ADO.NET Overview</span></span>](ado-net-overview.md)
