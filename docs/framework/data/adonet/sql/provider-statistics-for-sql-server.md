---
title: SQL Server 的提供者統計資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: 21bf7662094d5bc8948a1ce6378c454713cacc62
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183113"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="c4d76-102">SQL Server 的提供者統計資料</span><span class="sxs-lookup"><span data-stu-id="c4d76-102">Provider Statistics for SQL Server</span></span>

<span data-ttu-id="c4d76-103">從 .NET Framework 2.0 版開始，.NET Framework Data Provider for SQL Server 便支援執行階段統計資料。</span><span class="sxs-lookup"><span data-stu-id="c4d76-103">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="c4d76-104">您必須在建立有效的連線物件之後，將 <xref:System.Data.SqlClient.SqlConnection> 物件的 <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> 屬性設定為 `True`，以啟用統計資料。</span><span class="sxs-lookup"><span data-stu-id="c4d76-104">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="c4d76-105">啟用統計資料之後，您可以透過 <xref:System.Data.SqlClient.SqlConnection> 物件的 <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> 方法來擷取 <xref:System.Collections.IDictionary> 參考，以「及時快照集」方式加以檢閱。</span><span class="sxs-lookup"><span data-stu-id="c4d76-105">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="c4d76-106">您可以將清單列舉為一組名稱/值對字典項目。</span><span class="sxs-lookup"><span data-stu-id="c4d76-106">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="c4d76-107">這些名稱/值對並未排序。</span><span class="sxs-lookup"><span data-stu-id="c4d76-107">These name/value pairs are unordered.</span></span> <span data-ttu-id="c4d76-108">您隨時都可以呼叫 <xref:System.Data.SqlClient.SqlConnection> 物件的 <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> 方法來重設計數器。</span><span class="sxs-lookup"><span data-stu-id="c4d76-108">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="c4d76-109">如果尚未啟用統計資料收集功能，就不會產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c4d76-109">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="c4d76-110">此外，如果在未先呼叫 <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> 的情況下呼叫 <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>，擷取的值會是每個項目的初始值。</span><span class="sxs-lookup"><span data-stu-id="c4d76-110">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="c4d76-111">如果您啟用統計資料、執行應用程式一段時間，然後停用統計資料，擷取的值將會反映出直到停用統計資料那一刻為止，所收集到的值。</span><span class="sxs-lookup"><span data-stu-id="c4d76-111">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="c4d76-112">所有收集到的統計值都是以個別連線為基礎。</span><span class="sxs-lookup"><span data-stu-id="c4d76-112">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="c4d76-113">可用的統計值</span><span class="sxs-lookup"><span data-stu-id="c4d76-113">Statistical Values Available</span></span>  

 <span data-ttu-id="c4d76-114">Microsoft SQL Server 提供者目前提供了 18 個不同的項目。</span><span class="sxs-lookup"><span data-stu-id="c4d76-114">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="c4d76-115">可以透過 <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> 傳回之 <xref:System.Collections.IDictionary> 介面參考的 **Count** 屬性，存取可用的項目數目。</span><span class="sxs-lookup"><span data-stu-id="c4d76-115">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="c4d76-116">提供者統計資料的所有計數器均使用 Common Language Runtime <xref:System.Int64> 類型 (C# 及 Visual Basic 中的 **long**)，寬度為 64 位元。</span><span class="sxs-lookup"><span data-stu-id="c4d76-116">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="c4d76-117">如 **int64.MaxValue** 欄位所定義，**int64** 資料類型的最大值是 ((2^63)-1))。</span><span class="sxs-lookup"><span data-stu-id="c4d76-117">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="c4d76-118">當計數器的值達到此最大值時，應該就不會再被視為準確的值。</span><span class="sxs-lookup"><span data-stu-id="c4d76-118">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="c4d76-119">這表示 **int64.MaxValue**-1((2^63)-2) 實際上是任何統計資料的最大有效值。</span><span class="sxs-lookup"><span data-stu-id="c4d76-119">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4d76-120">字典是用來傳回提供者統計資料，因為未來所傳回統計資料的數目、名稱與順序可能會變更。</span><span class="sxs-lookup"><span data-stu-id="c4d76-120">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="c4d76-121">應用程式不應該依賴在字典中找到的特定值，而應該改為檢查值是否存在，並據以進行分支處理。</span><span class="sxs-lookup"><span data-stu-id="c4d76-121">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="c4d76-122">下表說明目前可用的統計值。</span><span class="sxs-lookup"><span data-stu-id="c4d76-122">The following table describes the current statistical values available.</span></span> <span data-ttu-id="c4d76-123">請注意，個別值的索引鍵名稱並未在 Microsoft .NET Framework 的區域版本中當地語系化。</span><span class="sxs-lookup"><span data-stu-id="c4d76-123">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="c4d76-124">金鑰名稱</span><span class="sxs-lookup"><span data-stu-id="c4d76-124">Key Name</span></span>|<span data-ttu-id="c4d76-125">描述</span><span class="sxs-lookup"><span data-stu-id="c4d76-125">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="c4d76-126">傳回應用程式開始使用提供者並啟用統計資料之後，提供者從 SQL Server 接收到的表格式資料流 (TDS) 封包數目。</span><span class="sxs-lookup"><span data-stu-id="c4d76-126">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="c4d76-127">傳回啟用統計資料之後，提供者傳送給 SQL Server 的 TDS 封包數目。</span><span class="sxs-lookup"><span data-stu-id="c4d76-127">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="c4d76-128">大型命令可能會需要多個緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c4d76-128">Large commands can require multiple buffers.</span></span> <span data-ttu-id="c4d76-129">例如，如果將大型命令傳送至伺服器，而且該命令需要 6 個封包，`ServerRoundtrips` 就會遞增 1，`BuffersSent` 會遞增 6。</span><span class="sxs-lookup"><span data-stu-id="c4d76-129">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="c4d76-130">傳回應用程式開始使用提供者並啟用統計資料之後，提供者從 SQL Server 接收到的 TDS 封包中所包含資料的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="c4d76-130">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="c4d76-131">傳回應用程式開始使用提供者並啟用統計資料之後，TDS 封包中傳送給 SQL Server 之資料的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="c4d76-131">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="c4d76-132">在啟用統計資料後連線處於開啟的時間量 (如果統計資料是在開啟連線之前啟用的，則為總連線時間)。</span><span class="sxs-lookup"><span data-stu-id="c4d76-132">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="c4d76-133">傳回應用程式開始使用提供者並啟用統計資料之後，透過連線開啟的資料指標次數。</span><span class="sxs-lookup"><span data-stu-id="c4d76-133">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="c4d76-134">請注意，SELECT 陳述式傳回的唯讀/順向結果不會被視為資料指標，因此不會影響此計數器。</span><span class="sxs-lookup"><span data-stu-id="c4d76-134">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="c4d76-135">傳回啟用統計資料後，提供者在處理作業所耗用的累計時間量 (以毫秒為單位)，包括等待伺服器回覆的時間，以及提供者本身執行程式碼的時間。</span><span class="sxs-lookup"><span data-stu-id="c4d76-135">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="c4d76-136">包含計時程式碼的類別如下：</span><span class="sxs-lookup"><span data-stu-id="c4d76-136">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="c4d76-137">SqlConnection</span><span class="sxs-lookup"><span data-stu-id="c4d76-137">SqlConnection</span></span><br /><br /> <span data-ttu-id="c4d76-138">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="c4d76-138">SqlCommand</span></span><br /><br /> <span data-ttu-id="c4d76-139">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="c4d76-139">SqlDataReader</span></span><br /><br /> <span data-ttu-id="c4d76-140">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="c4d76-140">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="c4d76-141">SqlTransaction</span><span class="sxs-lookup"><span data-stu-id="c4d76-141">SqlTransaction</span></span><br /><br /> <span data-ttu-id="c4d76-142">SqlCommandBuilder</span><span class="sxs-lookup"><span data-stu-id="c4d76-142">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="c4d76-143">為了盡可能減少需要高效能才能正常運作的成員數，不會針對下列成員計時：</span><span class="sxs-lookup"><span data-stu-id="c4d76-143">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="c4d76-144">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="c4d76-144">SqlDataReader</span></span><br /><br /> <span data-ttu-id="c4d76-145">this[] 運算子 (所有多載)</span><span class="sxs-lookup"><span data-stu-id="c4d76-145">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="c4d76-146">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="c4d76-146">GetBoolean</span></span><br /><br /> <span data-ttu-id="c4d76-147">GetChar</span><span class="sxs-lookup"><span data-stu-id="c4d76-147">GetChar</span></span><br /><br /> <span data-ttu-id="c4d76-148">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="c4d76-148">GetDateTime</span></span><br /><br /> <span data-ttu-id="c4d76-149">GetDecimal</span><span class="sxs-lookup"><span data-stu-id="c4d76-149">GetDecimal</span></span><br /><br /> <span data-ttu-id="c4d76-150">GetDouble</span><span class="sxs-lookup"><span data-stu-id="c4d76-150">GetDouble</span></span><br /><br /> <span data-ttu-id="c4d76-151">GetFloat</span><span class="sxs-lookup"><span data-stu-id="c4d76-151">GetFloat</span></span><br /><br /> <span data-ttu-id="c4d76-152">GetGuid</span><span class="sxs-lookup"><span data-stu-id="c4d76-152">GetGuid</span></span><br /><br /> <span data-ttu-id="c4d76-153">GetInt16</span><span class="sxs-lookup"><span data-stu-id="c4d76-153">GetInt16</span></span><br /><br /> <span data-ttu-id="c4d76-154">GetInt32</span><span class="sxs-lookup"><span data-stu-id="c4d76-154">GetInt32</span></span><br /><br /> <span data-ttu-id="c4d76-155">GetInt64</span><span class="sxs-lookup"><span data-stu-id="c4d76-155">GetInt64</span></span><br /><br /> <span data-ttu-id="c4d76-156">GetName</span><span class="sxs-lookup"><span data-stu-id="c4d76-156">GetName</span></span><br /><br /> <span data-ttu-id="c4d76-157">GetOrdinal</span><span class="sxs-lookup"><span data-stu-id="c4d76-157">GetOrdinal</span></span><br /><br /> <span data-ttu-id="c4d76-158">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="c4d76-158">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="c4d76-159">GetSqlBoolean</span><span class="sxs-lookup"><span data-stu-id="c4d76-159">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="c4d76-160">GetSqlByte</span><span class="sxs-lookup"><span data-stu-id="c4d76-160">GetSqlByte</span></span><br /><br /> <span data-ttu-id="c4d76-161">GetSqlDateTime</span><span class="sxs-lookup"><span data-stu-id="c4d76-161">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="c4d76-162">GetSqlDecimal</span><span class="sxs-lookup"><span data-stu-id="c4d76-162">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="c4d76-163">GetSqlDouble</span><span class="sxs-lookup"><span data-stu-id="c4d76-163">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="c4d76-164">GetSqlGuid</span><span class="sxs-lookup"><span data-stu-id="c4d76-164">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="c4d76-165">GetSqlInt16</span><span class="sxs-lookup"><span data-stu-id="c4d76-165">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="c4d76-166">GetSqlInt32</span><span class="sxs-lookup"><span data-stu-id="c4d76-166">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="c4d76-167">GetSqlInt64</span><span class="sxs-lookup"><span data-stu-id="c4d76-167">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="c4d76-168">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="c4d76-168">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="c4d76-169">GetSqlSingle</span><span class="sxs-lookup"><span data-stu-id="c4d76-169">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="c4d76-170">GetSqlString</span><span class="sxs-lookup"><span data-stu-id="c4d76-170">GetSqlString</span></span><br /><br /> <span data-ttu-id="c4d76-171">GetString</span><span class="sxs-lookup"><span data-stu-id="c4d76-171">GetString</span></span><br /><br /> <span data-ttu-id="c4d76-172">IsDBNull</span><span class="sxs-lookup"><span data-stu-id="c4d76-172">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="c4d76-173">傳回應用程式開始使用提供者並啟用統計資料之後，透過連線執行的 INSERT、DELETE 與 UPDATE 陳述式總數。</span><span class="sxs-lookup"><span data-stu-id="c4d76-173">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="c4d76-174">傳回應用程式開始使用提供者並啟用統計資料之後，受透過連線執行的 INSERT、DELETE 與 UPDATE 陳述式所影響的資料列總數。</span><span class="sxs-lookup"><span data-stu-id="c4d76-174">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="c4d76-175">一旦應用程式已開始使用提供者並啟用統計資料後，傳回提供者等待伺服器回覆的累計時間量 (以毫秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="c4d76-175">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="c4d76-176">傳回應用程式開始使用提供者並啟用統計資料後，透過連線所執行的備妥命令數目。</span><span class="sxs-lookup"><span data-stu-id="c4d76-176">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="c4d76-177">傳回應用程式開始使用提供者並啟用統計資料之後，透過連線所備妥陳述式的數目。</span><span class="sxs-lookup"><span data-stu-id="c4d76-177">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="c4d76-178">傳回應用程式已開始使用提供者並啟用統計資料之後，透過連線所執行的 SELECT 陳述式數目。</span><span class="sxs-lookup"><span data-stu-id="c4d76-178">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="c4d76-179">這包括用來從資料指標取出資料列的 FETCH 陳述式，而且在到達 <xref:System.Data.SqlClient.SqlDataReader> 的結尾時，會更新 SELECT 陳述式的計數。</span><span class="sxs-lookup"><span data-stu-id="c4d76-179">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="c4d76-180">傳回應用程式開始使用提供者並啟用統計資料之後，已選取的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="c4d76-180">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="c4d76-181">此計數器會反映 SQL 陳述式產生的所有資料列，即使呼叫者並未實際取用的資料列也算在內。</span><span class="sxs-lookup"><span data-stu-id="c4d76-181">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="c4d76-182">例如，在讀取整個結果集之前關閉資料讀取器並不會影響計數。</span><span class="sxs-lookup"><span data-stu-id="c4d76-182">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="c4d76-183">這包括透過 FETCH 陳述式從資料指標擷取的資料列。</span><span class="sxs-lookup"><span data-stu-id="c4d76-183">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="c4d76-184">傳回應用程式開始使用提供者並啟用統計資料之後，連線傳送命令至伺服器並收到回覆的次數。</span><span class="sxs-lookup"><span data-stu-id="c4d76-184">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="c4d76-185">傳回應用程式開始使用提供者並啟用統計資料之後，已使用的結果集數目。</span><span class="sxs-lookup"><span data-stu-id="c4d76-185">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="c4d76-186">例如，這會包含傳回給用戶端的任何結果集。</span><span class="sxs-lookup"><span data-stu-id="c4d76-186">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="c4d76-187">針對資料指標，系統會將每個擷取或區塊擷取作業都視為獨立結果集。</span><span class="sxs-lookup"><span data-stu-id="c4d76-187">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="c4d76-188">傳回應用程式開始使用提供者並啟用統計資料 (包括復原) 之後，已啟動的使用者交易數目。</span><span class="sxs-lookup"><span data-stu-id="c4d76-188">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="c4d76-189">如果是使用自動認可來執行連線，系統會將每個命令都視為一個交易。</span><span class="sxs-lookup"><span data-stu-id="c4d76-189">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="c4d76-190">只要 BEGIN TRAN 陳述式一執行，此計數器就會遞增交易計數，無論交易之後獲認可或遭復原。</span><span class="sxs-lookup"><span data-stu-id="c4d76-190">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="c4d76-191">傳回應用程式已開始使用提供者並啟用統計資料之後，透過連線所執行的未備妥陳述式數目。</span><span class="sxs-lookup"><span data-stu-id="c4d76-191">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="c4d76-192">擷取值</span><span class="sxs-lookup"><span data-stu-id="c4d76-192">Retrieving a Value</span></span>  

 <span data-ttu-id="c4d76-193">下列主控台應用程式會顯示如何在連線上啟用統計資料、擷取四個獨立統計資料值，並將其寫到主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="c4d76-193">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4d76-194">下列範例使用包含於 SQL Server 的 **AdventureWorks** 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="c4d76-194">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="c4d76-195">範例程式碼中提供的連接字串會假設資料庫安裝在本機電腦且可供使用。</span><span class="sxs-lookup"><span data-stu-id="c4d76-195">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="c4d76-196">請依據環境需求修改連接字串。</span><span class="sxs-lookup"><span data-stu-id="c4d76-196">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a><span data-ttu-id="c4d76-197">擷取所有值</span><span class="sxs-lookup"><span data-stu-id="c4d76-197">Retrieving All Values</span></span>  

 <span data-ttu-id="c4d76-198">下列主控台應用程式會顯示如何在連線上啟用統計資料、使用列舉程式擷取所有可用的統計資料值，並將其寫到主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="c4d76-198">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4d76-199">下列範例使用包含於 SQL Server 的 **AdventureWorks** 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="c4d76-199">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="c4d76-200">範例程式碼中提供的連接字串會假設資料庫安裝在本機電腦且可供使用。</span><span class="sxs-lookup"><span data-stu-id="c4d76-200">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="c4d76-201">請依據環境需求修改連接字串。</span><span class="sxs-lookup"><span data-stu-id="c4d76-201">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4d76-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4d76-202">See also</span></span>

- <span data-ttu-id="c4d76-203">[SQL Server and ADO.NET](index.md) (SQL Server 和 ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c4d76-203">[SQL Server and ADO.NET](index.md)</span></span>
- <span data-ttu-id="c4d76-204">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="c4d76-204">[ADO.NET Overview](../ado-net-overview.md)</span></span>
