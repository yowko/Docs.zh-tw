---
title: ADO.NET 中的連接字串
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 4dab2656ae8f39976b21f949c9548a3f718dfafc
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347938"
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="27bec-102">ADO.NET 中的連接字串</span><span class="sxs-lookup"><span data-stu-id="27bec-102">Connection Strings in ADO.NET</span></span>

<span data-ttu-id="27bec-103">連接字串 (Connection String) 包含可當做參數從資料提供者 (Data Provider) 傳遞至資料來源的初始化資訊。</span><span class="sxs-lookup"><span data-stu-id="27bec-103">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="27bec-104">此資料提供者接收的連接字串的值為<xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="27bec-104">The data provider receives the connection string as the value of the <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="27bec-105">提供者剖析連接字串，並可確保語法正確，且所支援的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="27bec-105">The provider parses the connection string and ensures that the syntax is correct and that the keywords are supported.</span></span> <span data-ttu-id="27bec-106">則<xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType>方法會將已剖析的連接參數傳遞至資料來源。</span><span class="sxs-lookup"><span data-stu-id="27bec-106">Then the <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> method passes the parsed connection parameters to the data source.</span></span> <span data-ttu-id="27bec-107">資料來源會執行進一步的驗證，以及建立連線。</span><span class="sxs-lookup"><span data-stu-id="27bec-107">The data source performs further validation and establishes a connection.</span></span>

## <a name="connection-string-syntax"></a><span data-ttu-id="27bec-108">連接字串語法</span><span class="sxs-lookup"><span data-stu-id="27bec-108">Connection string syntax</span></span>

<span data-ttu-id="27bec-109">連接字串是以分號分隔清單的索引鍵/值參數組：</span><span class="sxs-lookup"><span data-stu-id="27bec-109">A connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>
  
    keyword1=value; keyword2=value;
  
<span data-ttu-id="27bec-110">關鍵字不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="27bec-110">Keywords are not case-sensitive.</span></span> <span data-ttu-id="27bec-111">值，不過，可能會區分大小寫，根據資料來源。</span><span class="sxs-lookup"><span data-stu-id="27bec-111">Values, however, may be case-sensitive, depending on the data source.</span></span> <span data-ttu-id="27bec-112">關鍵字和值可能會包含[空白字元](https://en.wikipedia.org/wiki/Whitespace_character#Unicode)。</span><span class="sxs-lookup"><span data-stu-id="27bec-112">Both keywords and values may contain [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span></span> <span data-ttu-id="27bec-113">忽略關鍵字開頭和尾端空白且不具引號的值。</span><span class="sxs-lookup"><span data-stu-id="27bec-113">Leading and trailing whitespace is ignored in keywords and unquoted values.</span></span>

<span data-ttu-id="27bec-114">如果值包含分號[Unicode 控制字元](https://en.wikipedia.org/wiki/Unicode_control_characters)，或是開頭或結尾的空白字元，它必須以單引號或雙引號括起來。</span><span class="sxs-lookup"><span data-stu-id="27bec-114">If a value contains the semicolon, [Unicode control characters](https://en.wikipedia.org/wiki/Unicode_control_characters), or leading or trailing whitespace, it must be enclosed in single or double quotation marks.</span></span> <span data-ttu-id="27bec-115">例如: </span><span class="sxs-lookup"><span data-stu-id="27bec-115">For example:</span></span>

    Keyword=" whitespace  ";
    Keyword='special;character';

<span data-ttu-id="27bec-116">封入字元可能不會發生在其所包圍的值。</span><span class="sxs-lookup"><span data-stu-id="27bec-116">The enclosing character may not occur within the value it encloses.</span></span> <span data-ttu-id="27bec-117">因此，只有在雙引號括住，反之亦然，可以用包含單引號的值：</span><span class="sxs-lookup"><span data-stu-id="27bec-117">Therefore, a value containing single quotation marks can be enclosed only in double quotation marks, and vice versa:</span></span>

    Keyword='double"quotation;mark';
    Keyword="single'quotation;mark";

<span data-ttu-id="27bec-118">引號本身，以及在等號，不需要逸出，因此下列連接字串是有效：</span><span class="sxs-lookup"><span data-stu-id="27bec-118">The quotation marks themselves, as well as the equals sign, do not require escaping, so the following connection strings are valid:</span></span>

    Keyword=no "escaping" 'required';
    Keyword=a=b=c

<span data-ttu-id="27bec-119">直到下一步 以分號或字串的結尾會讀取每個值，因為第二個範例中的值是`a=b=c`，最後的分號則是選擇性。</span><span class="sxs-lookup"><span data-stu-id="27bec-119">Since each value is read till the next semicolon or the end of string, the value in the latter example is `a=b=c`, and the final semicolon is optional.</span></span>

<span data-ttu-id="27bec-120">所有連接字串會都共用相同的基本語法，上面所述。</span><span class="sxs-lookup"><span data-stu-id="27bec-120">All connection strings share the same basic syntax described above.</span></span> <span data-ttu-id="27bec-121">提供者而定，不過，可辨識的關鍵字集合，以及發展多年來從早期的 Api 中這類*ODBC*。</span><span class="sxs-lookup"><span data-stu-id="27bec-121">The set of recognized keywords depends on the provider, however, and has evolved over the years from earlier APIs such as *ODBC*.</span></span> <span data-ttu-id="27bec-122">*.NET Framework*資料提供者*SQL Server* (`SqlClient`) 支援許多的關鍵字，從較舊的 Api，但通常較具彈性且接受許多常見的連接字串的同義字關鍵字。</span><span class="sxs-lookup"><span data-stu-id="27bec-122">The *.NET Framework* data provider for *SQL Server* (`SqlClient`) supports many keywords from older APIs, but is generally more flexible and accepts synonyms for many of the common connection string keywords.</span></span>

<span data-ttu-id="27bec-123">輸入錯誤，可能會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="27bec-123">Typing mistakes can cause errors.</span></span> <span data-ttu-id="27bec-124">例如，`Integrated Security=true`有效，但`IntegratedSecurity=true`會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="27bec-124">For example, `Integrated Security=true` is valid, but `IntegratedSecurity=true` causes an error.</span></span>

<span data-ttu-id="27bec-125">從未經驗證的使用者輸入的執行階段以手動方式建構的連接字串受到字串插入式攻擊，並危及安全性，在資料來源。</span><span class="sxs-lookup"><span data-stu-id="27bec-125">Connection strings constructed manually at run time from unvalidated user input are vulnerable to string-injection attacks and jeopardize security at the data source.</span></span> <span data-ttu-id="27bec-126">為了解決這些問題中， *ADO.NET* 2.0 導入了[連接字串產生器](../../../../docs/framework/data/adonet/connection-string-builders.md)每個 *.NET Framework*資料提供者。</span><span class="sxs-lookup"><span data-stu-id="27bec-126">To address these problems, *ADO.NET* 2.0 introduced [connection string builders](../../../../docs/framework/data/adonet/connection-string-builders.md) for each *.NET Framework* data provider.</span></span> <span data-ttu-id="27bec-127">這些連接字串產生器參數為強型別屬性，公開 （expose），並使它能夠傳送到資料來源之前，驗證連接字串。</span><span class="sxs-lookup"><span data-stu-id="27bec-127">These connection string builders expose parameters as strongly-typed properties, and make it possible to validate the connection string before it's sent to the data source.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="27bec-128">本節內容</span><span class="sxs-lookup"><span data-stu-id="27bec-128">In This Section</span></span>  
 [<span data-ttu-id="27bec-129">連接字串產生器</span><span class="sxs-lookup"><span data-stu-id="27bec-129">Connection String Builders</span></span>](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 <span data-ttu-id="27bec-130">示範如何使用 `ConnectionStringBuilder` 類別在執行階段建構有效的連接字串。</span><span class="sxs-lookup"><span data-stu-id="27bec-130">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>
  
 [<span data-ttu-id="27bec-131">連接字串和組態檔</span><span class="sxs-lookup"><span data-stu-id="27bec-131">Connection Strings and Configuration Files</span></span>](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 <span data-ttu-id="27bec-132">示範如何在組態檔中儲存及擷取連接字串。</span><span class="sxs-lookup"><span data-stu-id="27bec-132">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>
  
 [<span data-ttu-id="27bec-133">連接字串語法</span><span class="sxs-lookup"><span data-stu-id="27bec-133">Connection String Syntax</span></span>](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 <span data-ttu-id="27bec-134">說明如何針對`SqlClient`、`OracleClient`、`OleDb` 和 `Odbc` 設定提供者專用的連接字串。</span><span class="sxs-lookup"><span data-stu-id="27bec-134">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>
  
 [<span data-ttu-id="27bec-135">保護連線資訊</span><span class="sxs-lookup"><span data-stu-id="27bec-135">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 <span data-ttu-id="27bec-136">示範的技術可保護用於連接至資料來源的資訊。</span><span class="sxs-lookup"><span data-stu-id="27bec-136">Demonstrates techniques for protecting information used to connect to a data source.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="27bec-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27bec-137">See Also</span></span>  
 [<span data-ttu-id="27bec-138">連接至資料來源</span><span class="sxs-lookup"><span data-stu-id="27bec-138">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)  
 [<span data-ttu-id="27bec-139">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="27bec-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
