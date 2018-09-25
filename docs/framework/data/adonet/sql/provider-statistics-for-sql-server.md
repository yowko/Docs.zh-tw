---
title: SQL Server 的提供者統計資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: d52c6bfdadf0a53ac4c5f62c37f1056c6702a82c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47080087"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="06488-102">SQL Server 的提供者統計資料</span><span class="sxs-lookup"><span data-stu-id="06488-102">Provider Statistics for SQL Server</span></span>
<span data-ttu-id="06488-103">從 .NET Framework 2.0 版開始，.NET Framework Data Provider for SQL Server 便支援執行階段統計資料。</span><span class="sxs-lookup"><span data-stu-id="06488-103">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="06488-104">建立有效的連接物件後，您必須藉由將 <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> 物件的 <xref:System.Data.SqlClient.SqlConnection> 屬性設為 `True`，以啟用統計資料。</span><span class="sxs-lookup"><span data-stu-id="06488-104">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="06488-105">統計資料啟用後，透過 <xref:System.Collections.IDictionary> 物件的 <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> 方法擷取 <xref:System.Data.SqlClient.SqlConnection> 參考，可以將它們做為「某時間的快照集」進行檢閱。</span><span class="sxs-lookup"><span data-stu-id="06488-105">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="06488-106">您可使用一組名稱/值配對字典項目的形式透過清單列舉。</span><span class="sxs-lookup"><span data-stu-id="06488-106">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="06488-107">這些名稱/值配對沒有排列順序。</span><span class="sxs-lookup"><span data-stu-id="06488-107">These name/value pairs are unordered.</span></span> <span data-ttu-id="06488-108">您可以隨時呼叫 <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> 物件的 <xref:System.Data.SqlClient.SqlConnection> 方法，以重設計數器。</span><span class="sxs-lookup"><span data-stu-id="06488-108">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="06488-109">如果尚未啟用統計資料蒐集，則不會產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="06488-109">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="06488-110">此外，如果呼叫 <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> 時未先呼叫 <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A>，則擷取的值會是每個項目的初始值。</span><span class="sxs-lookup"><span data-stu-id="06488-110">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="06488-111">如果啟用統計資料，並執行應用程式一段時間，然後停用統計資料，則擷取的值會反映到停用統計資料時所收集的值。</span><span class="sxs-lookup"><span data-stu-id="06488-111">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="06488-112">蒐集的所有統計資料值都是以每個連接為基礎。</span><span class="sxs-lookup"><span data-stu-id="06488-112">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="06488-113">可用的統計值</span><span class="sxs-lookup"><span data-stu-id="06488-113">Statistical Values Available</span></span>  
 <span data-ttu-id="06488-114">Microsoft SQL Server 提供者目前有 18 個不同的可用項目。</span><span class="sxs-lookup"><span data-stu-id="06488-114">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="06488-115">可透過存取的可用項目數**計數**屬性<xref:System.Collections.IDictionary>介面所傳回的參考<xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>。</span><span class="sxs-lookup"><span data-stu-id="06488-115">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="06488-116">所有提供者統計資料計數器使用 common language runtime<xref:System.Int64>型別 (**長**C# 和 Visual Basic 中)，這是 64 位元寬。</span><span class="sxs-lookup"><span data-stu-id="06488-116">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="06488-117">最大值**int64**資料類型所定義**int64。MaxValue**欄位中，為 ((2^63) 1))。</span><span class="sxs-lookup"><span data-stu-id="06488-117">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="06488-118">計數器的值達到此最大值時，則不應再將其視為精確值。</span><span class="sxs-lookup"><span data-stu-id="06488-118">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="06488-119">這表示**int64。MaxValue**-1((2^63)-2) 實際上是任何統計資料的最大有效值。</span><span class="sxs-lookup"><span data-stu-id="06488-119">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06488-120">因為傳回之統計資料的數目、名稱及順序將來可能會變更，所以會使用字典來傳回提供者統計資料。</span><span class="sxs-lookup"><span data-stu-id="06488-120">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="06488-121">應用程式不應依賴在字典中發現的特定值，而應檢查該值是否存在，並相應地進行分支。</span><span class="sxs-lookup"><span data-stu-id="06488-121">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="06488-122">下表說明目前可用的統計值。</span><span class="sxs-lookup"><span data-stu-id="06488-122">The following table describes the current statistical values available.</span></span> <span data-ttu-id="06488-123">請注意，個別值的索引鍵名稱並未在 Microsoft .NET Framework 的區域版本中當地語系化。</span><span class="sxs-lookup"><span data-stu-id="06488-123">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="06488-124">索引鍵名稱</span><span class="sxs-lookup"><span data-stu-id="06488-124">Key Name</span></span>|<span data-ttu-id="06488-125">描述</span><span class="sxs-lookup"><span data-stu-id="06488-125">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="06488-126">傳回在應用程式已開始使用提供者並啟用統計資料後，提供者從 SQL Server 接收之表格式資料流 (TDS) 封包的數目。</span><span class="sxs-lookup"><span data-stu-id="06488-126">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="06488-127">傳回在已啟用統計資料後，提供者傳送到 SQL Server 的 TDS 封包數目。</span><span class="sxs-lookup"><span data-stu-id="06488-127">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="06488-128">較大的命令會需要多個緩衝區。</span><span class="sxs-lookup"><span data-stu-id="06488-128">Large commands can require multiple buffers.</span></span> <span data-ttu-id="06488-129">例如，如果將較大的命令傳送至伺服器且其需要六個封包，則 `ServerRoundtrips` 數目會遞增一，而 `BuffersSent` 數目會遞增六。</span><span class="sxs-lookup"><span data-stu-id="06488-129">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="06488-130">傳回在應用程式已開始使用提供者並啟用統計資料後，提供者從 SQL Server 接收之 TDS 封包中的資料位元組數目。</span><span class="sxs-lookup"><span data-stu-id="06488-130">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="06488-131">傳回在應用程式已開始使用提供者並啟用統計資料後，TDS 封包中傳送至 SQL Server 之資料的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="06488-131">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="06488-132">在啟用統計資料後連接已開啟的時間量 (以毫秒為單位；如果統計資料是在開啟連接之前啟用的，則為總連接時間)。</span><span class="sxs-lookup"><span data-stu-id="06488-132">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="06488-133">一旦應用程式已開始使用提供者並啟用統計資料後，傳回透過連接開啟游標的次數。</span><span class="sxs-lookup"><span data-stu-id="06488-133">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="06488-134">請注意，不會將 SELECT 陳述式傳回的唯讀/順向結果視為游標，因此不會影響此計數器。</span><span class="sxs-lookup"><span data-stu-id="06488-134">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="06488-135">一旦啟用統計資料後，傳回提供者在處理作業所耗用的累計時間量 (以毫秒為單位)，包括等待伺服器回覆的時間，以及提供者自身執行程式碼的時間。</span><span class="sxs-lookup"><span data-stu-id="06488-135">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="06488-136">包含執行時間程式碼的類別有：</span><span class="sxs-lookup"><span data-stu-id="06488-136">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="06488-137">SqlConnection</span><span class="sxs-lookup"><span data-stu-id="06488-137">SqlConnection</span></span><br /><br /> <span data-ttu-id="06488-138">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="06488-138">SqlCommand</span></span><br /><br /> <span data-ttu-id="06488-139">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="06488-139">SqlDataReader</span></span><br /><br /> <span data-ttu-id="06488-140">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="06488-140">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="06488-141">SqlTransaction</span><span class="sxs-lookup"><span data-stu-id="06488-141">SqlTransaction</span></span><br /><br /> <span data-ttu-id="06488-142">SqlCommandBuilder</span><span class="sxs-lookup"><span data-stu-id="06488-142">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="06488-143">為了讓對效能有關鍵作用的成員數目儘可能最小，不會對下列成員計時：</span><span class="sxs-lookup"><span data-stu-id="06488-143">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="06488-144">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="06488-144">SqlDataReader</span></span><br /><br /> <span data-ttu-id="06488-145">this[] 運算子 (全部多載)</span><span class="sxs-lookup"><span data-stu-id="06488-145">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="06488-146">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="06488-146">GetBoolean</span></span><br /><br /> <span data-ttu-id="06488-147">GetChar</span><span class="sxs-lookup"><span data-stu-id="06488-147">GetChar</span></span><br /><br /> <span data-ttu-id="06488-148">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="06488-148">GetDateTime</span></span><br /><br /> <span data-ttu-id="06488-149">GetDecimal</span><span class="sxs-lookup"><span data-stu-id="06488-149">GetDecimal</span></span><br /><br /> <span data-ttu-id="06488-150">GetDouble</span><span class="sxs-lookup"><span data-stu-id="06488-150">GetDouble</span></span><br /><br /> <span data-ttu-id="06488-151">GetFloat</span><span class="sxs-lookup"><span data-stu-id="06488-151">GetFloat</span></span><br /><br /> <span data-ttu-id="06488-152">GetGuid</span><span class="sxs-lookup"><span data-stu-id="06488-152">GetGuid</span></span><br /><br /> <span data-ttu-id="06488-153">GetInt16</span><span class="sxs-lookup"><span data-stu-id="06488-153">GetInt16</span></span><br /><br /> <span data-ttu-id="06488-154">GetInt32</span><span class="sxs-lookup"><span data-stu-id="06488-154">GetInt32</span></span><br /><br /> <span data-ttu-id="06488-155">GetInt64</span><span class="sxs-lookup"><span data-stu-id="06488-155">GetInt64</span></span><br /><br /> <span data-ttu-id="06488-156">GetName</span><span class="sxs-lookup"><span data-stu-id="06488-156">GetName</span></span><br /><br /> <span data-ttu-id="06488-157">GetOrdinal</span><span class="sxs-lookup"><span data-stu-id="06488-157">GetOrdinal</span></span><br /><br /> <span data-ttu-id="06488-158">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="06488-158">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="06488-159">GetSqlBoolean </span><span class="sxs-lookup"><span data-stu-id="06488-159">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="06488-160">GetSqlByte </span><span class="sxs-lookup"><span data-stu-id="06488-160">GetSqlByte</span></span><br /><br /> <span data-ttu-id="06488-161">GetSqlDateTime </span><span class="sxs-lookup"><span data-stu-id="06488-161">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="06488-162">GetSqlDecimal </span><span class="sxs-lookup"><span data-stu-id="06488-162">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="06488-163">GetSqlDouble </span><span class="sxs-lookup"><span data-stu-id="06488-163">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="06488-164">GetSqlGuid </span><span class="sxs-lookup"><span data-stu-id="06488-164">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="06488-165">GetSqlInt16 </span><span class="sxs-lookup"><span data-stu-id="06488-165">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="06488-166">GetSqlInt32 </span><span class="sxs-lookup"><span data-stu-id="06488-166">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="06488-167">GetSqlInt64 </span><span class="sxs-lookup"><span data-stu-id="06488-167">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="06488-168">GetSqlMoney </span><span class="sxs-lookup"><span data-stu-id="06488-168">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="06488-169">GetSqlSingle </span><span class="sxs-lookup"><span data-stu-id="06488-169">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="06488-170">GetSqlString </span><span class="sxs-lookup"><span data-stu-id="06488-170">GetSqlString</span></span><br /><br /> <span data-ttu-id="06488-171">GetString</span><span class="sxs-lookup"><span data-stu-id="06488-171">GetString</span></span><br /><br /> <span data-ttu-id="06488-172">IsDBNull</span><span class="sxs-lookup"><span data-stu-id="06488-172">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="06488-173">一旦應用程式已開始使用提供者並啟用統計資料後，傳回透過連接執行之 INSERT、DELETE 及 UPDATE 陳述式的總數。</span><span class="sxs-lookup"><span data-stu-id="06488-173">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="06488-174">一旦應用程式已開始使用提供者並啟用統計資料後，傳回透過連接執行的 INSERT、DELETE 及 UPDATE 陳述式所影響的資料列總數。</span><span class="sxs-lookup"><span data-stu-id="06488-174">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="06488-175">一旦應用程式已開始使用提供者並啟用統計資料後，傳回提供者等待伺服器回覆的累計時間量 (以毫秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="06488-175">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="06488-176">一旦應用程式已開始使用提供者並啟用統計資料後，傳回透過連接執行之預備命令的數目。</span><span class="sxs-lookup"><span data-stu-id="06488-176">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="06488-177">一旦應用程式已開始使用提供者並啟用統計資料後，傳回透過連接預備的陳述式數目。</span><span class="sxs-lookup"><span data-stu-id="06488-177">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="06488-178">一旦應用程式已開始使用提供者並啟用統計資料後，傳回透過連接執行之 SELECT 陳述式的數目。</span><span class="sxs-lookup"><span data-stu-id="06488-178">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="06488-179">這包含從游標擷取資料列的 FETCH 陳述式，且會在達到 <xref:System.Data.SqlClient.SqlDataReader> 的結尾時更新 SELECT 陳述式的計數。</span><span class="sxs-lookup"><span data-stu-id="06488-179">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="06488-180">一旦應用程式已開始使用提供者並啟用統計資料後，傳回選取的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="06488-180">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="06488-181">此計數器會反映 SQL 陳述式產生的所有資料列，甚至包含呼叫端實際上並未使用的資料列。</span><span class="sxs-lookup"><span data-stu-id="06488-181">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="06488-182">例如，在讀取整個結果集之前關閉資料讀取器不會影響計數。</span><span class="sxs-lookup"><span data-stu-id="06488-182">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="06488-183">這會包含透過 FETCH 陳述式從游標擷取的資料列。</span><span class="sxs-lookup"><span data-stu-id="06488-183">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="06488-184">一旦應用程式已開始使用提供者並啟用統計資料後，傳回連接傳送命令至伺服器並取得回覆的次數。</span><span class="sxs-lookup"><span data-stu-id="06488-184">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="06488-185">一旦應用程式已開始使用提供者並啟用統計資料後，傳回已使用的結果集數目。</span><span class="sxs-lookup"><span data-stu-id="06488-185">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="06488-186">例如，這會包含傳回至用戶端的任何結果集。</span><span class="sxs-lookup"><span data-stu-id="06488-186">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="06488-187">對於游標，會將每個擷取或封鎖擷取作業視為獨立的結果集。</span><span class="sxs-lookup"><span data-stu-id="06488-187">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="06488-188">一旦應用程式已開始使用提供者並啟用統計資料後，傳回已啟動的使用者交易數目，包括復原。</span><span class="sxs-lookup"><span data-stu-id="06488-188">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="06488-189">如果連接執行時已啟用自動認可，則會將每個命令視為交易。</span><span class="sxs-lookup"><span data-stu-id="06488-189">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="06488-190">一旦執行 BEGIN TRAN 陳述式，此計數器便會遞增交易計數，而不論是否會認可或稍後復原交易。</span><span class="sxs-lookup"><span data-stu-id="06488-190">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="06488-191">一旦應用程式已開始使用提供者並啟用統計資料後，傳回透過連接執行之取消準備的陳述式數目。</span><span class="sxs-lookup"><span data-stu-id="06488-191">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="06488-192">擷取值</span><span class="sxs-lookup"><span data-stu-id="06488-192">Retrieving a Value</span></span>  
 <span data-ttu-id="06488-193">下列主控台應用程式會顯示如何在連接上啟用統計資料、如何擷取四個個別的統計資料值，以及如何將它們寫入至主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="06488-193">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06488-194">下列範例使用範例**AdventureWorks**隨附於 SQL Server 的資料庫。</span><span class="sxs-lookup"><span data-stu-id="06488-194">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="06488-195">範例程式碼中提供的連接字串假設本機電腦已安裝並可使用資料庫。</span><span class="sxs-lookup"><span data-stu-id="06488-195">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="06488-196">視環境需要修改連接字串。</span><span class="sxs-lookup"><span data-stu-id="06488-196">Modify the connection string as necessary for your environment.</span></span>  
  
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
    ' you can retrive it from a configuration file.  
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
      // you can retrive it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a><span data-ttu-id="06488-197">擷取所有值</span><span class="sxs-lookup"><span data-stu-id="06488-197">Retrieving All Values</span></span>  
 <span data-ttu-id="06488-198">下列主控台應用程式會顯示如何在連接上啟用統計資料、如何使用列舉值擷取所有可用的統計資料值，以及如何將它們寫入至主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="06488-198">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06488-199">下列範例使用範例**AdventureWorks**隨附於 SQL Server 的資料庫。</span><span class="sxs-lookup"><span data-stu-id="06488-199">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="06488-200">範例程式碼中提供的連接字串假設本機電腦已安裝並可使用資料庫。</span><span class="sxs-lookup"><span data-stu-id="06488-200">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="06488-201">視環境需要修改連接字串。</span><span class="sxs-lookup"><span data-stu-id="06488-201">Modify the connection string as necessary for your environment.</span></span>  
  
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
    ' you can retrive it from a configuration file.  
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
      // you can retrive it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="06488-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06488-202">See Also</span></span>  
 [<span data-ttu-id="06488-203">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="06488-203">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="06488-204">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="06488-204">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
