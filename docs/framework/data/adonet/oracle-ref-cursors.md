---
title: Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 7cd29a6a20015c7ce4475b0211cb07f7ee78b530
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794879"
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="9da9e-102">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="9da9e-102">Oracle REF CURSORs</span></span>
<span data-ttu-id="9da9e-103">Oracle 的 .NET Framework Data Provider 支援 Oracle **REF CURSOR**資料類型。</span><span class="sxs-lookup"><span data-stu-id="9da9e-103">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="9da9e-104">透過資料提供者使用 Oracle REF CURSOR 時，您應考量下列行為。</span><span class="sxs-lookup"><span data-stu-id="9da9e-104">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9da9e-105">某些行為與 Oracle 的 Microsoft OLE DB 提供者 (MSDAORA) 的行為不同。</span><span class="sxs-lookup"><span data-stu-id="9da9e-105">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
- <span data-ttu-id="9da9e-106">基於效能的考慮，除非您明確指定，否則 Oracle 的 Data Provider 不會自動系結**REF CURSOR**資料類型（如 MSDAORA 所示）。</span><span class="sxs-lookup"><span data-stu-id="9da9e-106">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
- <span data-ttu-id="9da9e-107">該資料提供者不支援任何 ODBC 逸出序列，包括用來指定 REF CURSOR 參數的 {resultset} 逸出。</span><span class="sxs-lookup"><span data-stu-id="9da9e-107">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
- <span data-ttu-id="9da9e-108">若要執行可傳回 REF 資料指標的預存程式<xref:System.Data.OracleClient.OracleParameterCollection> ，您必須<xref:System.Data.OracleClient.OracleType>使用資料**指標**的和<xref:System.Data.OracleClient.OracleParameter.Direction%2A> **輸出**的來定義中的參數。</span><span class="sxs-lookup"><span data-stu-id="9da9e-108">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="9da9e-109">資料提供者僅支援將 REF CURSOR 繫結為輸出參數。</span><span class="sxs-lookup"><span data-stu-id="9da9e-109">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="9da9e-110">提供者不支援 REF CURSOR 做為輸入參數。</span><span class="sxs-lookup"><span data-stu-id="9da9e-110">The provider does not support REF CURSORs as input parameters.</span></span>  
  
- <span data-ttu-id="9da9e-111">不支援從參數值取得 <xref:System.Data.OracleClient.OracleDataReader>。</span><span class="sxs-lookup"><span data-stu-id="9da9e-111">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="9da9e-112">命令執行後，值的型別為 <xref:System.DBNull>。</span><span class="sxs-lookup"><span data-stu-id="9da9e-112">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
- <span data-ttu-id="9da9e-113">唯一可搭配 REF 資料指標使用的**CommandBehavior**列舉值（例如，呼叫<xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>時）為**CloseConnection**; 所有其他專案都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="9da9e-113">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
- <span data-ttu-id="9da9e-114">**OracleDataReader**中 REF 資料指標的順序取決於**OracleParameterCollection**中參數的順序。</span><span class="sxs-lookup"><span data-stu-id="9da9e-114">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="9da9e-115">忽略 <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="9da9e-115">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
- <span data-ttu-id="9da9e-116">不支援 PL/SQL**資料表**資料類型。</span><span class="sxs-lookup"><span data-stu-id="9da9e-116">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="9da9e-117">然而，REF CURSOR 更有效率。</span><span class="sxs-lookup"><span data-stu-id="9da9e-117">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="9da9e-118">如果您必須使用**資料表**資料類型，請使用 OLE DB .net DATA PROVIDER 搭配 MSDAORA。</span><span class="sxs-lookup"><span data-stu-id="9da9e-118">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9da9e-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="9da9e-119">In This Section</span></span>  
 [<span data-ttu-id="9da9e-120">REF CURSOR 範例</span><span class="sxs-lookup"><span data-stu-id="9da9e-120">REF CURSOR Examples</span></span>](ref-cursor-examples.md)  
 <span data-ttu-id="9da9e-121">包含示範如何使用 REF CURSOR 的三個範例。</span><span class="sxs-lookup"><span data-stu-id="9da9e-121">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="9da9e-122">OracleDataReader 中的 REF CURSOR 參數</span><span class="sxs-lookup"><span data-stu-id="9da9e-122">REF CURSOR Parameters in an OracleDataReader</span></span>](ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="9da9e-123">示範如何執行會傳回 REF CURSOR 參數的 PL/SQL 預存程式，並以**OracleDataReader**的形式讀取該值。</span><span class="sxs-lookup"><span data-stu-id="9da9e-123">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="9da9e-124">使用 OracleDataReader 從多個 REF CURSOR 擷取資料</span><span class="sxs-lookup"><span data-stu-id="9da9e-124">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="9da9e-125">示範如何執行會傳回兩個 REF CURSOR 參數的 PL/SQL 預存程式，並使用**OracleDataReader**來讀取值。</span><span class="sxs-lookup"><span data-stu-id="9da9e-125">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="9da9e-126">使用一或多個 REF CURSOR 填入資料集</span><span class="sxs-lookup"><span data-stu-id="9da9e-126">Filling a DataSet Using One or More REF CURSORs</span></span>](filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="9da9e-127">示範如何執行傳回兩個 REF CURSOR 參數的 PL/SQL 預存程序，並使用傳回的資料列填入 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="9da9e-127">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9da9e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9da9e-128">See also</span></span>

- [<span data-ttu-id="9da9e-129">Oracle 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9da9e-129">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="9da9e-130">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="9da9e-130">ADO.NET Overview</span></span>](ado-net-overview.md)
