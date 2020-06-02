---
title: 日期和時間資料
description: 深入瞭解資料類型，以便在 SQL Server 的 .NET Framework Data Provider 中處理日期和時間資訊。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: 9345e995dcb1179e7d0a86f62737f9fda5889f42
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286490"
---
# <a name="date-and-time-data"></a><span data-ttu-id="e5f17-103">日期和時間資料</span><span class="sxs-lookup"><span data-stu-id="e5f17-103">Date and Time Data</span></span>
<span data-ttu-id="e5f17-104">SQL Server 2008 引進了新的資料類型來處理日期和時間資訊。</span><span class="sxs-lookup"><span data-stu-id="e5f17-104">SQL Server 2008 introduces new data types for handling date and time information.</span></span> <span data-ttu-id="e5f17-105">新的資料類型包含適用於日期和時間的個別類型，以及具有更大範圍、精確度和時區感知的已擴充資料類型。</span><span class="sxs-lookup"><span data-stu-id="e5f17-105">The new data types include separate types for date and time, and expanded data types with greater range, precision, and time-zone awareness.</span></span> <span data-ttu-id="e5f17-106">從 .NET Framework 3.5 版 Service Pack (SP) 1 開始，.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) 就會針對 SQL Server 2008 Database Engine 的所有新功能提供完整支援。</span><span class="sxs-lookup"><span data-stu-id="e5f17-106">Starting with the .NET Framework version 3.5 Service Pack (SP) 1, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides full support for all the new features of the SQL Server 2008 Database Engine.</span></span> <span data-ttu-id="e5f17-107">您必須安裝 .NET Framework 3.5 SP1 (或更新版本) 才能使用這些新功能搭配 SqlClient。</span><span class="sxs-lookup"><span data-stu-id="e5f17-107">You must install the .NET Framework 3.5 SP1 (or later) to use these new features with SqlClient.</span></span>  
  
 <span data-ttu-id="e5f17-108">早於 SQL Server 2008 的 SQL Server 版本，只有兩種資料類型可用來處理日期和時間值：`datetime` 和 `smalldatetime`。</span><span class="sxs-lookup"><span data-stu-id="e5f17-108">Versions of SQL Server earlier than SQL Server 2008 only had two data types for working with date and time values: `datetime` and `smalldatetime`.</span></span> <span data-ttu-id="e5f17-109">這兩種資料類型都同時包含日期值和時間值，所以很難只使用日期或是時間值。</span><span class="sxs-lookup"><span data-stu-id="e5f17-109">Both of these data types contain both the date value and a time value, which makes it difficult to work with only date or only time values.</span></span> <span data-ttu-id="e5f17-110">此外，這些資料類型僅支援 1753 年在英國引進西曆之後的日期。</span><span class="sxs-lookup"><span data-stu-id="e5f17-110">Also, these data types only support dates that occur after the introduction of the Gregorian calendar in England in 1753.</span></span> <span data-ttu-id="e5f17-111">另一個限制是這些較舊的資料類型不是時區感知的，因此很難處理源自多個時區的資料。</span><span class="sxs-lookup"><span data-stu-id="e5f17-111">Another limitation is that these older data types are not time-zone aware, which makes it difficult to work with data that originates from multiple time zones.</span></span>  
  
 <span data-ttu-id="e5f17-112">《SQL Server 線上叢書》提供 SQL Server 資料類型的完整文件。</span><span class="sxs-lookup"><span data-stu-id="e5f17-112">Complete documentation for SQL Server data types is available in SQL Server Books Online.</span></span> <span data-ttu-id="e5f17-113">下表將列出日期和時間資料的版本特有入門級主題。</span><span class="sxs-lookup"><span data-stu-id="e5f17-113">The following table lists the version-specific entry-level topics for date and time data.</span></span>  
  
 <span data-ttu-id="e5f17-114">**SQL Server 檔**</span><span class="sxs-lookup"><span data-stu-id="e5f17-114">**SQL Server documentation**</span></span>  
  
1. <span data-ttu-id="e5f17-115">[使用日期和時間資料](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="e5f17-115">[Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span></span>  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a><span data-ttu-id="e5f17-116">SQL Server 2008 所導入的日期/時間資料型別</span><span class="sxs-lookup"><span data-stu-id="e5f17-116">Date/Time Data Types Introduced in SQL Server 2008</span></span>  
 <span data-ttu-id="e5f17-117">下表描述新的日期和時間資料類型。</span><span class="sxs-lookup"><span data-stu-id="e5f17-117">The following table describes the new date and time data types.</span></span>  
  
|<span data-ttu-id="e5f17-118">SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="e5f17-118">SQL Server data type</span></span>|<span data-ttu-id="e5f17-119">描述</span><span class="sxs-lookup"><span data-stu-id="e5f17-119">Description</span></span>|  
|--------------------------|-----------------|  
|`date`|<span data-ttu-id="e5f17-120">`date` 資料類型的範圍從 01 年 1 月 1 日到 9999 年 12 月 31 日，精確度為 1 日。</span><span class="sxs-lookup"><span data-stu-id="e5f17-120">The `date` data type has a range of January 1, 01 through December 31, 9999 with an accuracy of 1 day.</span></span> <span data-ttu-id="e5f17-121">預設值為 1900 年 1 月 1 日。</span><span class="sxs-lookup"><span data-stu-id="e5f17-121">The default value is January 1, 1900.</span></span> <span data-ttu-id="e5f17-122">儲存體大小是 3 位元組。</span><span class="sxs-lookup"><span data-stu-id="e5f17-122">The storage size is 3 bytes.</span></span>|  
|`time`|<span data-ttu-id="e5f17-123">`time` 資料類型只會根據 24 小時制來儲存時間值。</span><span class="sxs-lookup"><span data-stu-id="e5f17-123">The `time` data type stores time values only, based on a 24-hour clock.</span></span> <span data-ttu-id="e5f17-124">`time` 資料類型的範圍從 00:00:00.0000000 到 23:59:59.9999999，精確度為 100 奈秒。</span><span class="sxs-lookup"><span data-stu-id="e5f17-124">The `time` data type has a range of 00:00:00.0000000 through 23:59:59.9999999 with an accuracy of 100 nanoseconds.</span></span> <span data-ttu-id="e5f17-125">預設值是 00:00:00.0000000 (午夜)。</span><span class="sxs-lookup"><span data-stu-id="e5f17-125">The default value is 00:00:00.0000000 (midnight).</span></span> <span data-ttu-id="e5f17-126">`time` 資料類型支援使用者定義的小數點後第二位的精確度，儲存大小則從 3 到 6 位元組不等，依指定的精確度而定。</span><span class="sxs-lookup"><span data-stu-id="e5f17-126">The `time` data type supports user-defined fractional second precision, and the storage size varies from 3 to 6 bytes, based on the precision specified.</span></span>|  
|`datetime2`|<span data-ttu-id="e5f17-127">`datetime2` 資料類型會將 `date` 和 `time` 資料類型的範圍和精確度結合成單一資料類型。</span><span class="sxs-lookup"><span data-stu-id="e5f17-127">The `datetime2` data type combines the range and precision of the `date` and `time` data types into a single data type.</span></span><br /><br /> <span data-ttu-id="e5f17-128">預設值和字串常值格式會與 `date` 和 `time` 資料類型中所定義的相同。</span><span class="sxs-lookup"><span data-stu-id="e5f17-128">The default values and string literal formats are the same as those defined in the `date` and `time` data types.</span></span>|  
|`datetimeoffset`|<span data-ttu-id="e5f17-129">`datetimeoffset` 資料類型具有 `datetime2` 的所有功能，且具有額外的時區位移。</span><span class="sxs-lookup"><span data-stu-id="e5f17-129">The `datetimeoffset` data type has all the features of `datetime2` with an additional time zone offset.</span></span> <span data-ttu-id="e5f17-130">時區位移會以 [+&#124;-] HH:MM 表示。</span><span class="sxs-lookup"><span data-stu-id="e5f17-130">The time zone offset is represented as [+&#124;-] HH:MM.</span></span> <span data-ttu-id="e5f17-131">HH 表示時區位移中的 2 位數時數，範圍介於 00 至 14 之間。</span><span class="sxs-lookup"><span data-stu-id="e5f17-131">HH is 2 digits ranging from 00 to 14 that represent the number of hours in the time zone offset.</span></span> <span data-ttu-id="e5f17-132">MM 是代表時區位移中額外分鐘數的 2 位數，範圍介於 00 至 59 之間。</span><span class="sxs-lookup"><span data-stu-id="e5f17-132">MM is 2 digits ranging from 00 to 59 that represent the number of additional minutes in the time zone offset.</span></span> <span data-ttu-id="e5f17-133">時間格式可支援到 100 奈秒。</span><span class="sxs-lookup"><span data-stu-id="e5f17-133">Time formats are supported to 100 nanoseconds.</span></span> <span data-ttu-id="e5f17-134">強制性的 + 或 - 符號指出是否要從 UTC (世界標準時間或格林威治標準時間) 增加或扣除時區位移，以取得當地時間。</span><span class="sxs-lookup"><span data-stu-id="e5f17-134">The mandatory + or - sign indicates whether the time zone offset is added or subtracted from UTC (Universal Time Coordinate or Greenwich Mean Time) to obtain the local time.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="e5f17-135">如需使用 `Type System Version` 關鍵字的詳細資訊，請參閱 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="e5f17-135">For more information about using the `Type System Version` keyword, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
## <a name="date-format-and-date-order"></a><span data-ttu-id="e5f17-136">日期格式和日期順序</span><span class="sxs-lookup"><span data-stu-id="e5f17-136">Date Format and Date Order</span></span>  
 <span data-ttu-id="e5f17-137">SQL Server 剖析日期和時間值的方式，不僅取決於類型系統版本和伺服器版本，也會根據伺服器的預設語言和格式設定而定。</span><span class="sxs-lookup"><span data-stu-id="e5f17-137">How SQL Server parses date and time values depends not only on the type system version and server version, but also on the server's default language and format settings.</span></span> <span data-ttu-id="e5f17-138">如果查詢會透過使用不同語言和日期格式設定的連線來執行，則可能無法辨識適用於某種語言之日期格式的日期字串。</span><span class="sxs-lookup"><span data-stu-id="e5f17-138">A date string that works for the date formats of one language might be unrecognizable if the query is executed by a connection that uses a different language and date format setting.</span></span>  
  
 <span data-ttu-id="e5f17-139">Transact-SQL SET LANGUAGE 陳述式會隱含地設定 DATEFORMAT，以決定日期部分的順序。</span><span class="sxs-lookup"><span data-stu-id="e5f17-139">The Transact-SQL SET LANGUAGE statement implicitly sets the DATEFORMAT that determines the order of the date parts.</span></span> <span data-ttu-id="e5f17-140">您可以利用 MDY、DMY、YMD、YDM、MYD 或 DYM 順序來排序日期部分，以在連線上使用 SET DATEFORMAT Transact-SQL 陳述式來釐清日期值。</span><span class="sxs-lookup"><span data-stu-id="e5f17-140">You can use the SET DATEFORMAT Transact-SQL statement on a connection to disambiguate date values by ordering the date parts in MDY, DMY, YMD, YDM, MYD, or DYM order.</span></span>  
  
 <span data-ttu-id="e5f17-141">如果您未針對連線指定任何 DATEFORMAT，SQL Server 就會使用與連線相關聯的預設語言。</span><span class="sxs-lookup"><span data-stu-id="e5f17-141">If you do not specify any DATEFORMAT for the connection, SQL Server uses the default language associated with the connection.</span></span> <span data-ttu-id="e5f17-142">例如，在語言設定為「美式英文」的伺服器上，會將 '01/02/03' 的日期字串解讀為 MDY (2003 年 1 月 2 日)，而在語言設定為「英式英文」的伺服器上則會解譯為 DMY (2003 年 2 月 1 日)。</span><span class="sxs-lookup"><span data-stu-id="e5f17-142">For example, a date string of '01/02/03' would be interpreted as MDY (January 2, 2003) on a server with a language setting of United States English, and as DMY (February 1, 2003) on a server with a language setting of British English.</span></span> <span data-ttu-id="e5f17-143">年份會使用 SQL Server 的截止年份規則來決定，這會定義用來指派世紀值的截止日期。</span><span class="sxs-lookup"><span data-stu-id="e5f17-143">The year is determined by using SQL Server's cutoff year rule, which defines the cutoff date for assigning the century value.</span></span> <span data-ttu-id="e5f17-144">如需詳細資訊，請參閱[兩位數年份的截止選項](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option)。</span><span class="sxs-lookup"><span data-stu-id="e5f17-144">For more information, see [two digit year cutoff Option](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5f17-145">從字串格式轉換為 `date`、`time`、`datetime2` 或 `datetimeoffset` 時，不支援 YDM 日期格式。</span><span class="sxs-lookup"><span data-stu-id="e5f17-145">The YDM date format is not supported when converting from a string format to `date`, `time`, `datetime2`, or `datetimeoffset`.</span></span>  
  
 <span data-ttu-id="e5f17-146">如需 SQL Server 如何解讀日期和時間資料的詳細資訊，請參閱[使用日期和時間資料](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))。</span><span class="sxs-lookup"><span data-stu-id="e5f17-146">For more information about how SQL Server interprets date and time data, see [Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100)).</span></span>  
  
## <a name="datetime-data-types-and-parameters"></a><span data-ttu-id="e5f17-147">日期/時間資料型別和參數</span><span class="sxs-lookup"><span data-stu-id="e5f17-147">Date/Time Data Types and Parameters</span></span>  
 <span data-ttu-id="e5f17-148"><xref:System.Data.SqlDbType> 中新增了以下列舉來支援新的日期和時間資料類型。</span><span class="sxs-lookup"><span data-stu-id="e5f17-148">The following enumerations have been added to <xref:System.Data.SqlDbType> to support the new date and time data types.</span></span>  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

<span data-ttu-id="e5f17-149">您可以使用上述其中一個 <xref:System.Data.SqlDbType> 列舉來指定 <xref:System.Data.SqlClient.SqlParameter> 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e5f17-149">You can specify the data type of a <xref:System.Data.SqlClient.SqlParameter> by using one of the preceding <xref:System.Data.SqlDbType> enumerations.</span></span>

> [!NOTE]
> <span data-ttu-id="e5f17-150">您無法將 `SqlParameter` 的 `DbType` 屬性設定為 `SqlDbType.Date`。</span><span class="sxs-lookup"><span data-stu-id="e5f17-150">You cannot set the `DbType` property of a `SqlParameter` to `SqlDbType.Date`.</span></span>

 <span data-ttu-id="e5f17-151">您也可以藉由將 `SqlParameter` 物件的 <xref:System.Data.SqlClient.SqlParameter.DbType%2A> 屬性設定為特定的 <xref:System.Data.DbType> 列舉值，以一般的方法指定 <xref:System.Data.SqlClient.SqlParameter> 的類型。</span><span class="sxs-lookup"><span data-stu-id="e5f17-151">You can also specify the type of a <xref:System.Data.SqlClient.SqlParameter> generically by setting the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> property of a `SqlParameter` object to a particular <xref:System.Data.DbType> enumeration value.</span></span> <span data-ttu-id="e5f17-152"><xref:System.Data.DbType> 中新增了以下列舉值，以支援 `datetime2` 和 `datetimeoffset` 資料類型：</span><span class="sxs-lookup"><span data-stu-id="e5f17-152">The following enumeration values have been added to <xref:System.Data.DbType> to support the `datetime2` and `datetimeoffset` data types:</span></span>  
  
- <span data-ttu-id="e5f17-153">DbType.DateTime2</span><span class="sxs-lookup"><span data-stu-id="e5f17-153">DbType.DateTime2</span></span>  
  
- <span data-ttu-id="e5f17-154">DbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="e5f17-154">DbType.DateTimeOffset</span></span>  
  
 <span data-ttu-id="e5f17-155">這些新的列舉型別補充了存在舊版 .NET Framework 中的 `Date`、`Time` 和 `DateTime` 列舉型別。</span><span class="sxs-lookup"><span data-stu-id="e5f17-155">These new enumerations supplement the `Date`, `Time`, and `DateTime` enumerations, which existed in earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="e5f17-156">您可以從參數物件之值的 .NET Framework 型別，或從參數物件的 `DbType` 推斷出參數物件的 .NET Framework 資料提供者型別。</span><span class="sxs-lookup"><span data-stu-id="e5f17-156">The .NET Framework data provider type of a parameter object is inferred from the .NET Framework type of the value of the parameter object, or from the `DbType` of the parameter object.</span></span> <span data-ttu-id="e5f17-157">尚未引進任何新的 <xref:System.Data.SqlTypes> 資料類型來支援新的日期和時間資料類型。</span><span class="sxs-lookup"><span data-stu-id="e5f17-157">No new <xref:System.Data.SqlTypes> data types have been introduced to support the new date and time data types.</span></span> <span data-ttu-id="e5f17-158">下表描述 SQL Server 2008 日期和時間資料類型與 CLR 資料類型之間的對應。</span><span class="sxs-lookup"><span data-stu-id="e5f17-158">The following table describes the mappings between the SQL Server 2008 date and time data types and the CLR data types.</span></span>  
  
|<span data-ttu-id="e5f17-159">SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="e5f17-159">SQL Server data type</span></span>|<span data-ttu-id="e5f17-160">.NET Framework 類型</span><span class="sxs-lookup"><span data-stu-id="e5f17-160">.NET Framework type</span></span>|<span data-ttu-id="e5f17-161">System.Data.SqlDbType</span><span class="sxs-lookup"><span data-stu-id="e5f17-161">System.Data.SqlDbType</span></span>|<span data-ttu-id="e5f17-162">System.Data.DbType</span><span class="sxs-lookup"><span data-stu-id="e5f17-162">System.Data.DbType</span></span>|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|<span data-ttu-id="e5f17-163">date</span><span class="sxs-lookup"><span data-stu-id="e5f17-163">date</span></span>|<span data-ttu-id="e5f17-164">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="e5f17-164">System.DateTime</span></span>|<span data-ttu-id="e5f17-165">日期</span><span class="sxs-lookup"><span data-stu-id="e5f17-165">Date</span></span>|<span data-ttu-id="e5f17-166">日期</span><span class="sxs-lookup"><span data-stu-id="e5f17-166">Date</span></span>|  
|<span data-ttu-id="e5f17-167">time</span><span class="sxs-lookup"><span data-stu-id="e5f17-167">time</span></span>|<span data-ttu-id="e5f17-168">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="e5f17-168">System.TimeSpan</span></span>|<span data-ttu-id="e5f17-169">時間</span><span class="sxs-lookup"><span data-stu-id="e5f17-169">Time</span></span>|<span data-ttu-id="e5f17-170">時間</span><span class="sxs-lookup"><span data-stu-id="e5f17-170">Time</span></span>|  
|<span data-ttu-id="e5f17-171">datetime2</span><span class="sxs-lookup"><span data-stu-id="e5f17-171">datetime2</span></span>|<span data-ttu-id="e5f17-172">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="e5f17-172">System.DateTime</span></span>|<span data-ttu-id="e5f17-173">DateTime2</span><span class="sxs-lookup"><span data-stu-id="e5f17-173">DateTime2</span></span>|<span data-ttu-id="e5f17-174">DateTime2</span><span class="sxs-lookup"><span data-stu-id="e5f17-174">DateTime2</span></span>|  
|<span data-ttu-id="e5f17-175">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="e5f17-175">datetimeoffset</span></span>|<span data-ttu-id="e5f17-176">System.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="e5f17-176">System.DateTimeOffset</span></span>|<span data-ttu-id="e5f17-177">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="e5f17-177">DateTimeOffset</span></span>|<span data-ttu-id="e5f17-178">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="e5f17-178">DateTimeOffset</span></span>|  
|<span data-ttu-id="e5f17-179">Datetime</span><span class="sxs-lookup"><span data-stu-id="e5f17-179">datetime</span></span>|<span data-ttu-id="e5f17-180">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="e5f17-180">System.DateTime</span></span>|<span data-ttu-id="e5f17-181">Datetime</span><span class="sxs-lookup"><span data-stu-id="e5f17-181">DateTime</span></span>|<span data-ttu-id="e5f17-182">Datetime</span><span class="sxs-lookup"><span data-stu-id="e5f17-182">DateTime</span></span>|  
|<span data-ttu-id="e5f17-183">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="e5f17-183">smalldatetime</span></span>|<span data-ttu-id="e5f17-184">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="e5f17-184">System.DateTime</span></span>|<span data-ttu-id="e5f17-185">Datetime</span><span class="sxs-lookup"><span data-stu-id="e5f17-185">DateTime</span></span>|<span data-ttu-id="e5f17-186">Datetime</span><span class="sxs-lookup"><span data-stu-id="e5f17-186">DateTime</span></span>|  
  
### <a name="sqlparameter-properties"></a><span data-ttu-id="e5f17-187">SqlParameter 屬性</span><span class="sxs-lookup"><span data-stu-id="e5f17-187">SqlParameter Properties</span></span>  
 <span data-ttu-id="e5f17-188">下表描述與日期和時間資料類型相關的 `SqlParameter` 屬性。</span><span class="sxs-lookup"><span data-stu-id="e5f17-188">The following table describes `SqlParameter` properties that are relevant to date and time data types.</span></span>  
  
|<span data-ttu-id="e5f17-189">屬性</span><span class="sxs-lookup"><span data-stu-id="e5f17-189">Property</span></span>|<span data-ttu-id="e5f17-190">描述</span><span class="sxs-lookup"><span data-stu-id="e5f17-190">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|<span data-ttu-id="e5f17-191">取得或設定值是否可為 Null。</span><span class="sxs-lookup"><span data-stu-id="e5f17-191">Gets or sets whether a value is nullable.</span></span> <span data-ttu-id="e5f17-192">當您將 Null 參數值傳送到伺服器時，必須指定 <xref:System.DBNull>，而不是 `null` (在 Visual Basic 中為 `Nothing`)。</span><span class="sxs-lookup"><span data-stu-id="e5f17-192">When you send a null parameter value to the server, you must specify <xref:System.DBNull>, rather than `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="e5f17-193">如需資料庫 null 的詳細資訊，請參閱[處理 Null 值](handling-null-values.md)。</span><span class="sxs-lookup"><span data-stu-id="e5f17-193">For more information about database nulls, see [Handling Null Values](handling-null-values.md).</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|<span data-ttu-id="e5f17-194">取得或設定用來表示值的最大位數。</span><span class="sxs-lookup"><span data-stu-id="e5f17-194">Gets or sets the maximum number of digits used to represent the value.</span></span> <span data-ttu-id="e5f17-195">系統會針對日期和時間資料類型忽略此設定。</span><span class="sxs-lookup"><span data-stu-id="e5f17-195">This setting is ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|<span data-ttu-id="e5f17-196">取得或設定針對 `Time`、`DateTime2` 和 `DateTimeOffset` 解析之值時間部分的小數點位數。</span><span class="sxs-lookup"><span data-stu-id="e5f17-196">Gets or sets the number of decimal places to which the time portion of the value is resolved for `Time`, `DateTime2`,and `DateTimeOffset`.</span></span> <span data-ttu-id="e5f17-197">預設值為 0，表示會從值推斷實際的小數值，並傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="e5f17-197">The default value is 0, which means that the actual scale is inferred from the value and sent to the server.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="e5f17-198">已針對日期和時間資料類型加以忽略。</span><span class="sxs-lookup"><span data-stu-id="e5f17-198">Ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="e5f17-199">取得或設定參數值。</span><span class="sxs-lookup"><span data-stu-id="e5f17-199">Gets or sets the parameter value.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="e5f17-200">取得或設定參數值。</span><span class="sxs-lookup"><span data-stu-id="e5f17-200">Gets or sets the parameter value.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="e5f17-201">小於零或者大於或等於 24 小時的時間值將會擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="e5f17-201">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
### <a name="creating-parameters"></a><span data-ttu-id="e5f17-202">建立參數</span><span class="sxs-lookup"><span data-stu-id="e5f17-202">Creating Parameters</span></span>  
 <span data-ttu-id="e5f17-203">您可以使用 <xref:System.Data.SqlClient.SqlParameter> 物件的建構函式 (Constructor)，或將它加入至 <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> 集合 (透過呼叫 `Add` 的 <xref:System.Data.SqlClient.SqlParameterCollection> 方法)，藉以建立此物件。</span><span class="sxs-lookup"><span data-stu-id="e5f17-203">You can create a <xref:System.Data.SqlClient.SqlParameter> object by using its constructor, or by adding it to a <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection by calling the `Add` method of the <xref:System.Data.SqlClient.SqlParameterCollection>.</span></span> <span data-ttu-id="e5f17-204">`Add` 方法將會取得建構函式引數或現有參數物件作為輸入。</span><span class="sxs-lookup"><span data-stu-id="e5f17-204">The `Add` method will take as input either constructor arguments or an existing parameter object.</span></span>  
  
 <span data-ttu-id="e5f17-205">此主題的後續小節將提供如何指定日期和時間參數的範例。</span><span class="sxs-lookup"><span data-stu-id="e5f17-205">The next sections in this topic provide examples of how to specify date and time parameters.</span></span> <span data-ttu-id="e5f17-206">如需使用參數的其他範例，請參閱設定[參數和參數資料類型](../configuring-parameters-and-parameter-data-types.md)和[DataAdapter 參數](../dataadapter-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="e5f17-206">For additional examples of working with parameters, see [Configuring Parameters and Parameter Data Types](../configuring-parameters-and-parameter-data-types.md) and [DataAdapter Parameters](../dataadapter-parameters.md).</span></span>  
  
### <a name="date-example"></a><span data-ttu-id="e5f17-207">Date 範例</span><span class="sxs-lookup"><span data-stu-id="e5f17-207">Date Example</span></span>  
 <span data-ttu-id="e5f17-208">下列程式碼片段將示範如何指定 `date` 參數。</span><span class="sxs-lookup"><span data-stu-id="e5f17-208">The following code fragment demonstrates how to specify a `date` parameter.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Date"  
parameter.SqlDbType = SqlDbType.Date  
parameter.Value = "2007/12/1"  
```  
  
### <a name="time-example"></a><span data-ttu-id="e5f17-209">Time 範例</span><span class="sxs-lookup"><span data-stu-id="e5f17-209">Time Example</span></span>  
 <span data-ttu-id="e5f17-210">下列程式碼片段將示範如何指定 `time` 參數。</span><span class="sxs-lookup"><span data-stu-id="e5f17-210">The following code fragment demonstrates how to specify a `time` parameter.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Time"  
parameter.SqlDbType = SqlDbType.Time  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a><span data-ttu-id="e5f17-211">Datetime2 範例</span><span class="sxs-lookup"><span data-stu-id="e5f17-211">Datetime2 Example</span></span>  
 <span data-ttu-id="e5f17-212">下列程式碼片段將示範如何指定同時具備日期和時間部分的 `datetime2` 參數。</span><span class="sxs-lookup"><span data-stu-id="e5f17-212">The following code fragment demonstrates how to specify a `datetime2` parameter with both the date and time parts.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Datetime2"  
parameter.SqlDbType = SqlDbType.DateTime2  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a><span data-ttu-id="e5f17-213">DateTimeOffSet 範例</span><span class="sxs-lookup"><span data-stu-id="e5f17-213">DateTimeOffSet Example</span></span>  
 <span data-ttu-id="e5f17-214">下列程式碼片段將示範如何指定具備日期、時間且時區位移為 0 的 `DateTimeOffSet` 參數。</span><span class="sxs-lookup"><span data-stu-id="e5f17-214">The following code fragment demonstrates how to specify a `DateTimeOffSet` parameter with a date, a time, and a time zone offset of 0.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@DateTimeOffSet"  
parameter.SqlDbType = SqlDbType.DateTimeOffSet  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a><span data-ttu-id="e5f17-215">AddWithValue</span><span class="sxs-lookup"><span data-stu-id="e5f17-215">AddWithValue</span></span>  
 <span data-ttu-id="e5f17-216">您也可以使用 <xref:System.Data.SqlClient.SqlCommand> 的 `AddWithValue` 方法來提供參數，如下列程式碼片段所示。</span><span class="sxs-lookup"><span data-stu-id="e5f17-216">You can also supply parameters by using the `AddWithValue` method of a <xref:System.Data.SqlClient.SqlCommand>, as shown in the following code fragment.</span></span> <span data-ttu-id="e5f17-217">不過，`AddWithValue` 方法不允許您針對參數指定 <xref:System.Data.SqlClient.SqlParameter.DbType%2A> 或 <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A>。</span><span class="sxs-lookup"><span data-stu-id="e5f17-217">However, the `AddWithValue` method does not allow you to specify the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> or <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> for the parameter.</span></span>  
  
```csharp  
command.Parameters.AddWithValue(
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 <span data-ttu-id="e5f17-218">`@date` 參數可對應至伺服器上的 `date`、`datetime` 或 `datetime2` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="e5f17-218">The `@date` parameter could map to a `date`, `datetime`, or `datetime2` data type on the server.</span></span> <span data-ttu-id="e5f17-219">使用新的 `datetime` 資料類型時，您必須將參數的 <xref:System.Data.SqlDbType> 屬性明確設定為執行個體的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e5f17-219">When working with the new `datetime` data types, you must explicitly set the parameter's <xref:System.Data.SqlDbType> property to the data type of the instance.</span></span> <span data-ttu-id="e5f17-220">使用 <xref:System.Data.SqlDbType.Variant> 或隱含提供參數值可能會導致與 `datetime` 和 `smalldatetime` 資料類型的回溯相容性問題。</span><span class="sxs-lookup"><span data-stu-id="e5f17-220">Using <xref:System.Data.SqlDbType.Variant> or implicitly supplying parameter values can cause problems with backward compatibility with the `datetime` and `smalldatetime` data types.</span></span>  
  
 <span data-ttu-id="e5f17-221">下表顯示可從哪些 CLR 類型推斷出哪些 `SqlDbTypes`：</span><span class="sxs-lookup"><span data-stu-id="e5f17-221">The following table shows which `SqlDbTypes` are inferred from which CLR types:</span></span>  
  
|<span data-ttu-id="e5f17-222">CLR 類型</span><span class="sxs-lookup"><span data-stu-id="e5f17-222">CLR type</span></span>|<span data-ttu-id="e5f17-223">推斷的 SqlDbType</span><span class="sxs-lookup"><span data-stu-id="e5f17-223">Inferred SqlDbType</span></span>|  
|--------------|------------------------|  
|<span data-ttu-id="e5f17-224">Datetime</span><span class="sxs-lookup"><span data-stu-id="e5f17-224">DateTime</span></span>|<span data-ttu-id="e5f17-225">SqlDbType.DateTime</span><span class="sxs-lookup"><span data-stu-id="e5f17-225">SqlDbType.DateTime</span></span>|  
|<span data-ttu-id="e5f17-226">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="e5f17-226">TimeSpan</span></span>|<span data-ttu-id="e5f17-227">SqlDbType.Time</span><span class="sxs-lookup"><span data-stu-id="e5f17-227">SqlDbType.Time</span></span>|  
|<span data-ttu-id="e5f17-228">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="e5f17-228">DateTimeOffset</span></span>|<span data-ttu-id="e5f17-229">SqlDbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="e5f17-229">SqlDbType.DateTimeOffset</span></span>|  
  
## <a name="retrieving-date-and-time-data"></a><span data-ttu-id="e5f17-230">擷取日期和時間資料</span><span class="sxs-lookup"><span data-stu-id="e5f17-230">Retrieving Date and Time Data</span></span>  
 <span data-ttu-id="e5f17-231">下表說明用來擷取 SQL Server 2008 日期和時間值的方法。</span><span class="sxs-lookup"><span data-stu-id="e5f17-231">The following table describes methods that are used to retrieve SQL Server 2008 date and time values.</span></span>  
  
|<span data-ttu-id="e5f17-232">SqlClient 方法</span><span class="sxs-lookup"><span data-stu-id="e5f17-232">SqlClient method</span></span>|<span data-ttu-id="e5f17-233">描述</span><span class="sxs-lookup"><span data-stu-id="e5f17-233">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|<span data-ttu-id="e5f17-234">擷取指定的資料行值作為 <xref:System.DateTime> 結構。</span><span class="sxs-lookup"><span data-stu-id="e5f17-234">Retrieves the specified column value as a <xref:System.DateTime> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|<span data-ttu-id="e5f17-235">擷取指定的資料行值作為 <xref:System.DateTimeOffset> 結構。</span><span class="sxs-lookup"><span data-stu-id="e5f17-235">Retrieves the specified column value as a <xref:System.DateTimeOffset> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|<span data-ttu-id="e5f17-236">傳回類型，其為欄位的底層提供者特定類型。</span><span class="sxs-lookup"><span data-stu-id="e5f17-236">Returns the type that is the underlying provider-specific type for the field.</span></span> <span data-ttu-id="e5f17-237">針對新的日期和時間類型，傳回與 `GetFieldType` 相同的類型。</span><span class="sxs-lookup"><span data-stu-id="e5f17-237">Returns the same types as `GetFieldType` for new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|<span data-ttu-id="e5f17-238">擷取指定資料行的值。</span><span class="sxs-lookup"><span data-stu-id="e5f17-238">Retrieves the value of the specified column.</span></span> <span data-ttu-id="e5f17-239">針對新的日期和時間類型，傳回與 `GetValue` 相同的類型。</span><span class="sxs-lookup"><span data-stu-id="e5f17-239">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|<span data-ttu-id="e5f17-240">擷取指定陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="e5f17-240">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<span data-ttu-id="e5f17-241">以 <xref:System.Data.SqlTypes.SqlString> 形式擷取資料行值。</span><span class="sxs-lookup"><span data-stu-id="e5f17-241">Retrieves the column value as a <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="e5f17-242">如果無法將資料表示為 `SqlString`，就會發生 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="e5f17-242">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a `SqlString`.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|<span data-ttu-id="e5f17-243">擷取資料行資料作為其預設 `SqlDbType`。</span><span class="sxs-lookup"><span data-stu-id="e5f17-243">Retrieves column data as its default `SqlDbType`.</span></span> <span data-ttu-id="e5f17-244">針對新的日期和時間類型，傳回與 `GetValue` 相同的類型。</span><span class="sxs-lookup"><span data-stu-id="e5f17-244">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|<span data-ttu-id="e5f17-245">擷取指定陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="e5f17-245">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|<span data-ttu-id="e5f17-246">如果 Type System Version 是設為 SQL Server 2005，則擷取資料行的值作為字串。</span><span class="sxs-lookup"><span data-stu-id="e5f17-246">Retrieves the column value as a string if the Type System Version is set to SQL Server 2005.</span></span> <span data-ttu-id="e5f17-247">如果無法將資料表示為字串，就會發生 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="e5f17-247">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a string.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|<span data-ttu-id="e5f17-248">擷取指定的資料行值作為 <xref:System.TimeSpan> 結構。</span><span class="sxs-lookup"><span data-stu-id="e5f17-248">Retrieves the specified column value as a <xref:System.TimeSpan> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|<span data-ttu-id="e5f17-249">擷取指定的資料行值作為其底層 CLR 類型。</span><span class="sxs-lookup"><span data-stu-id="e5f17-249">Retrieves the specified column value as its underlying CLR type.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|<span data-ttu-id="e5f17-250">擷取陣列中的資料行值。</span><span class="sxs-lookup"><span data-stu-id="e5f17-250">Retrieves column values in an array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|<span data-ttu-id="e5f17-251">傳回 <xref:System.Data.DataTable>，其會描述結果集的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e5f17-251">Returns a <xref:System.Data.DataTable> that describes the metadata of the result set.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="e5f17-252">目前正在 SQL Server 處理序中執行的程式碼不支援新的日期和時間 `SqlDbTypes`。</span><span class="sxs-lookup"><span data-stu-id="e5f17-252">The new date and time `SqlDbTypes` are not supported for code that is executing in-process in SQL Server.</span></span> <span data-ttu-id="e5f17-253">如果將這其中一個類型傳遞至伺服器，就會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e5f17-253">An exception will be raised if one of these types is passed to the server.</span></span>  
  
## <a name="specifying-date-and-time-values-as-literals"></a><span data-ttu-id="e5f17-254">將日期和時間值指定為常值</span><span class="sxs-lookup"><span data-stu-id="e5f17-254">Specifying Date and Time Values as Literals</span></span>  
 <span data-ttu-id="e5f17-255">您可以使用各種不同的常值字串格式來指定日期和時間資料類型，然後 SQL Server 會在執行階段進行評估，以將它們轉換成內部日期/時間結構。</span><span class="sxs-lookup"><span data-stu-id="e5f17-255">You can specify date and time data types by using a variety of different literal string formats, which SQL Server then evaluates at run time, converting them to internal date/time structures.</span></span> <span data-ttu-id="e5f17-256">SQL Server 可以辨識括在單引號 (') 中的日期和時間資料。</span><span class="sxs-lookup"><span data-stu-id="e5f17-256">SQL Server recognizes date and time data that is enclosed in single quotation marks (').</span></span> <span data-ttu-id="e5f17-257">下列範例示範一些格式：</span><span class="sxs-lookup"><span data-stu-id="e5f17-257">The following examples demonstrate some formats:</span></span>  
  
- <span data-ttu-id="e5f17-258">字母日期格式，例如 `'October 15, 2006'`。</span><span class="sxs-lookup"><span data-stu-id="e5f17-258">Alphabetic date formats, such as `'October 15, 2006'`.</span></span>  
  
- <span data-ttu-id="e5f17-259">數值日期格式，例如 `'10/15/2006'`。</span><span class="sxs-lookup"><span data-stu-id="e5f17-259">Numeric date formats, such as `'10/15/2006'`.</span></span>  
  
- <span data-ttu-id="e5f17-260">未分隔的字串格式，例如 `'20061015'`，如果您使用 ISO 標準日期格式，則會將其解譯為 2006 年 10 月 15 日。</span><span class="sxs-lookup"><span data-stu-id="e5f17-260">Unseparated string formats, such as `'20061015'`, which would be interpreted as October 15, 2006 if you are using the ISO standard date format.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5f17-261">您可以在《SQL Server 線上叢書》中找到所有常值字串格式及日期和時間資料類型之其他功能的完整文件。</span><span class="sxs-lookup"><span data-stu-id="e5f17-261">You can find complete documentation for all of the literal string formats and other features of the date and time data types in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="e5f17-262">小於零或者大於或等於 24 小時的時間值將會擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="e5f17-262">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="e5f17-263">《SQL Server 線上叢書》中的資源</span><span class="sxs-lookup"><span data-stu-id="e5f17-263">Resources in SQL Server Books Online</span></span>  
 <span data-ttu-id="e5f17-264">如需在 SQL Server 中使用日期和時間值的詳細資訊，請參閱 SQL Server 線上叢書中的下列資源。</span><span class="sxs-lookup"><span data-stu-id="e5f17-264">For more information about working with date and time values in SQL Server, see the following resources in SQL Server Books Online.</span></span>  
  
|<span data-ttu-id="e5f17-265">主題</span><span class="sxs-lookup"><span data-stu-id="e5f17-265">Topic</span></span>|<span data-ttu-id="e5f17-266">描述</span><span class="sxs-lookup"><span data-stu-id="e5f17-266">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e5f17-267">日期和時間資料類型與函數 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e5f17-267">Date and Time Data Types and Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|<span data-ttu-id="e5f17-268">提供所有 Transact-SQL 日期和間資料類型與函式的概觀。</span><span class="sxs-lookup"><span data-stu-id="e5f17-268">Provides an overview of all Transact-SQL date and time data types and functions.</span></span>|  
|<span data-ttu-id="e5f17-269">[使用日期和時間資料](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="e5f17-269">[Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span></span>|<span data-ttu-id="e5f17-270">提供日期和時間資料類型與函式的詳細資訊，以及使用範例。</span><span class="sxs-lookup"><span data-stu-id="e5f17-270">Provides information about the date and time data types and functions, and examples of using them.</span></span>|  
|[<span data-ttu-id="e5f17-271">資料類型（Transact-sql）</span><span class="sxs-lookup"><span data-stu-id="e5f17-271">Data Types (Transact-SQL)</span></span>](/sql/t-sql/data-types/data-types-transact-sql)|<span data-ttu-id="e5f17-272">描述 SQL Server 中的系統資料類型。</span><span class="sxs-lookup"><span data-stu-id="e5f17-272">Describes system data types in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5f17-273">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5f17-273">See also</span></span>

- [<span data-ttu-id="e5f17-274">SQL Server 資料類型對應</span><span class="sxs-lookup"><span data-stu-id="e5f17-274">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="e5f17-275">設定參數和參數資料類型</span><span class="sxs-lookup"><span data-stu-id="e5f17-275">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="e5f17-276">SQL Server 資料類型和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e5f17-276">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- <span data-ttu-id="e5f17-277">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="e5f17-277">[ADO.NET Overview](../ado-net-overview.md)</span></span>
