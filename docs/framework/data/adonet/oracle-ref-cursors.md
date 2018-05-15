---
title: Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 7aae9b2e4b39cf164a93ba82212b5705f583d761
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="0fe11-102">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="0fe11-102">Oracle REF CURSORs</span></span>
<span data-ttu-id="0fe11-103">.NET Framework Data Provider for Oracle 支援 Oracle **REF CURSOR**資料型別。</span><span class="sxs-lookup"><span data-stu-id="0fe11-103">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="0fe11-104">透過資料提供者使用 Oracle REF CURSOR 時，您應考量下列行為。</span><span class="sxs-lookup"><span data-stu-id="0fe11-104">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0fe11-105">某些行為與 Oracle 的 Microsoft OLE DB 提供者 (MSDAORA) 的行為不同。</span><span class="sxs-lookup"><span data-stu-id="0fe11-105">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
-   <span data-ttu-id="0fe11-106">基於效能考量，Oracle 的資料提供者不會自動繫結**REF CURSOR**的資料類型，如 MSDAORA 一樣，除非您明確指定。</span><span class="sxs-lookup"><span data-stu-id="0fe11-106">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
-   <span data-ttu-id="0fe11-107">該資料提供者不支援任何 ODBC 逸出序列，包括用來指定 REF CURSOR 參數的 {resultset} 逸出。</span><span class="sxs-lookup"><span data-stu-id="0fe11-107">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
-   <span data-ttu-id="0fe11-108">若要執行傳回 REF Cursor 的預存程序，您必須定義中的參數<xref:System.Data.OracleClient.OracleParameterCollection>與<xref:System.Data.OracleClient.OracleType>的**游標**和<xref:System.Data.OracleClient.OracleParameter.Direction%2A>的**輸出**。</span><span class="sxs-lookup"><span data-stu-id="0fe11-108">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="0fe11-109">資料提供者僅支援將 REF CURSOR 繫結為輸出參數。</span><span class="sxs-lookup"><span data-stu-id="0fe11-109">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="0fe11-110">提供者不支援 REF CURSOR 做為輸入參數。</span><span class="sxs-lookup"><span data-stu-id="0fe11-110">The provider does not support REF CURSORs as input parameters.</span></span>  
  
-   <span data-ttu-id="0fe11-111">不支援從參數值取得 <xref:System.Data.OracleClient.OracleDataReader>。</span><span class="sxs-lookup"><span data-stu-id="0fe11-111">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="0fe11-112">命令執行後，值的型別為 <xref:System.DBNull>。</span><span class="sxs-lookup"><span data-stu-id="0fe11-112">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
-   <span data-ttu-id="0fe11-113">唯一**CommandBehavior** REF Cursor 的運作方式的列舉值 (例如，當呼叫<xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) 是**CloseConnection**; 忽略所有其他的。</span><span class="sxs-lookup"><span data-stu-id="0fe11-113">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
-   <span data-ttu-id="0fe11-114">中的 REF Cursor 的順序**OracleDataReader**結餘中的參數取決於**OracleParameterCollection**。</span><span class="sxs-lookup"><span data-stu-id="0fe11-114">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="0fe11-115">忽略 <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="0fe11-115">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
-   <span data-ttu-id="0fe11-116">PL/SQL**資料表**不支援資料類型。</span><span class="sxs-lookup"><span data-stu-id="0fe11-116">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="0fe11-117">然而，REF CURSOR 更有效率。</span><span class="sxs-lookup"><span data-stu-id="0fe11-117">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="0fe11-118">如果您必須使用**資料表**資料類型，使用 MSDAORA OLE DB.NET 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="0fe11-118">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0fe11-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="0fe11-119">In This Section</span></span>  
 [<span data-ttu-id="0fe11-120">REF CURSOR 範例</span><span class="sxs-lookup"><span data-stu-id="0fe11-120">REF CURSOR Examples</span></span>](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 <span data-ttu-id="0fe11-121">包含示範如何使用 REF CURSOR 的三個範例。</span><span class="sxs-lookup"><span data-stu-id="0fe11-121">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="0fe11-122">OracleDataReader 中的 REF CURSOR 參數</span><span class="sxs-lookup"><span data-stu-id="0fe11-122">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="0fe11-123">示範如何執行傳回 REF CURSOR 參數，並讀取做為值的 PL/SQL 預存程序**OracleDataReader**。</span><span class="sxs-lookup"><span data-stu-id="0fe11-123">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="0fe11-124">使用 OracleDataReader 從多個 REF CURSOR 擷取資料</span><span class="sxs-lookup"><span data-stu-id="0fe11-124">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="0fe11-125">示範如何執行傳回兩個 REF CURSOR 參數，並讀取值使用的 PL/SQL 預存程序**OracleDataReader**。</span><span class="sxs-lookup"><span data-stu-id="0fe11-125">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="0fe11-126">使用一或多個 REF CURSOR 填入資料集</span><span class="sxs-lookup"><span data-stu-id="0fe11-126">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="0fe11-127">示範如何執行傳回兩個 REF CURSOR 參數的 PL/SQL 預存程序，並使用傳回的資料列填入 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="0fe11-127">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fe11-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fe11-128">See Also</span></span>  
 [<span data-ttu-id="0fe11-129">Oracle 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0fe11-129">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="0fe11-130">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="0fe11-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
