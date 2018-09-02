---
title: REF CURSOR 範例
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: 803c921b76369aa9268c7fd34d1f15dd51bb17f3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406054"
---
# <a name="ref-cursor-examples"></a><span data-ttu-id="649f6-102">REF CURSOR 範例</span><span class="sxs-lookup"><span data-stu-id="649f6-102">REF CURSOR Examples</span></span>
<span data-ttu-id="649f6-103">REF CURSOR 範例包括下列三個 Microsoft Visual Basic 範例，示範如何使用 REF CURSOR：</span><span class="sxs-lookup"><span data-stu-id="649f6-103">The REF CURSOR examples are comprised of the following three Microsoft Visual Basic examples that demonstrate using REF CURSORs.</span></span>  
  
|<span data-ttu-id="649f6-104">範例</span><span class="sxs-lookup"><span data-stu-id="649f6-104">Sample</span></span>|<span data-ttu-id="649f6-105">描述</span><span class="sxs-lookup"><span data-stu-id="649f6-105">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="649f6-106">OracleDataReader 中的 REF CURSOR 參數</span><span class="sxs-lookup"><span data-stu-id="649f6-106">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)|<span data-ttu-id="649f6-107">此範例執行可傳回 REF CURSOR 參數的 PL/SQL 預存程序，並以 <xref:System.Data.OracleClient.OracleDataReader> 讀取值。</span><span class="sxs-lookup"><span data-stu-id="649f6-107">This example executes a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>|  
|[<span data-ttu-id="649f6-108">使用 OracleDataReader 從多個 REF CURSOR 擷取資料</span><span class="sxs-lookup"><span data-stu-id="649f6-108">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)|<span data-ttu-id="649f6-109">此範例執行傳回兩個 REF CURSOR 參數，並讀取使用的值的 PL/SQL 預存程序**OracleDataReader**。</span><span class="sxs-lookup"><span data-stu-id="649f6-109">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>|  
|[<span data-ttu-id="649f6-110">使用一或多個 REF CURSOR 填入資料集</span><span class="sxs-lookup"><span data-stu-id="649f6-110">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)|<span data-ttu-id="649f6-111">此範例執行可傳回兩個 REF CURSOR 參數的 PL/SQL 預存程序，並使用傳回的資料列填入 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="649f6-111">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>|  
  
 <span data-ttu-id="649f6-112">若要使用這些範例，您可能需要建立 Oracle 資料表，且必須建立 PL/SQL 封裝及封裝主體。</span><span class="sxs-lookup"><span data-stu-id="649f6-112">To use these examples, you may need to create the Oracle tables, and you must create a PL/SQL package and package body.</span></span>  
  
## <a name="creating-the-oracle-tables"></a><span data-ttu-id="649f6-113">建立 Oracle 資料表</span><span class="sxs-lookup"><span data-stu-id="649f6-113">Creating the Oracle Tables</span></span>  
 <span data-ttu-id="649f6-114">這些範例使用定義在 Oracle Scott/Tiger 結構描述中的資料表。</span><span class="sxs-lookup"><span data-stu-id="649f6-114">These examples use tables that are defined in the Oracle Scott/Tiger schema.</span></span> <span data-ttu-id="649f6-115">大多數 Oracle 安裝都包含 Oracle Scott/Tiger 結構描述。</span><span class="sxs-lookup"><span data-stu-id="649f6-115">The Oracle Scott/Tiger schema is included with most Oracle installations.</span></span> <span data-ttu-id="649f6-116">如果此結構描述不存在，則可使用 {OracleHome}\rdbms\admin\scott.sql 中的 SQL 命令檔案，來建立這些範例所使用的資料表及索引。</span><span class="sxs-lookup"><span data-stu-id="649f6-116">If this schema does not exist, you can use the SQL commands file in {OracleHome}\rdbms\admin\scott.sql to create the tables and indexes used by these examples.</span></span>  
  
## <a name="creating-the-oracle-package-and-package-body"></a><span data-ttu-id="649f6-117">建立 Oracle 封裝及封裝主體</span><span class="sxs-lookup"><span data-stu-id="649f6-117">Creating the Oracle Package and Package Body</span></span>  
 <span data-ttu-id="649f6-118">這些範例需要伺服器上的下列 PL/SQL 封裝及封裝主體。</span><span class="sxs-lookup"><span data-stu-id="649f6-118">These examples require the following PL/SQL package and package body on your server.</span></span> <span data-ttu-id="649f6-119">在 Oracle 伺服器上建立下列 Oracle 封裝。</span><span class="sxs-lookup"><span data-stu-id="649f6-119">Create the following Oracle package on the Oracle server.</span></span>  
  
```  
CREATE OR REPLACE PACKAGE CURSPKG AS   
    TYPE T_CURSOR IS REF CURSOR;   
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,   
                               IO_CURSOR IN OUT T_CURSOR);   
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
                                DEPTCURSOR OUT T_CURSOR);  
END CURSPKG;  
/   
```  
  
 <span data-ttu-id="649f6-120">在 Oracle 伺服器上建立下列 Oracle Package 內容。</span><span class="sxs-lookup"><span data-stu-id="649f6-120">Create the following Oracle package body on the Oracle server.</span></span>  
  
```  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS  
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,  
                               IO_CURSOR IN OUT T_CURSOR)  
    IS   
        V_CURSOR T_CURSOR;   
    BEGIN   
        IF N_EMPNO <> 0   
        THEN  
             OPEN V_CURSOR FOR   
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME   
                  FROM EMP, DEPT   
                  WHERE EMP.DEPTNO = DEPT.DEPTNO   
                  AND EMP.EMPNO = N_EMPNO;  
  
        ELSE   
             OPEN V_CURSOR FOR   
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME   
                  FROM EMP, DEPT   
                  WHERE EMP.DEPTNO = DEPT.DEPTNO;  
  
        END IF;  
        IO_CURSOR := V_CURSOR;   
    END OPEN_ONE_CURSOR;   
  
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,  
                                DEPTCURSOR OUT T_CURSOR)  
    IS   
        V_CURSOR1 T_CURSOR;   
        V_CURSOR2 T_CURSOR;   
    BEGIN   
        OPEN V_CURSOR1 FOR SELECT * FROM EMP;  
        OPEN V_CURSOR2 FOR SELECT * FROM DEPT;  
        EMPCURSOR  := V_CURSOR1;   
        DEPTCURSOR := V_CURSOR2;   
    END OPEN_TWO_CURSORS;   
END CURSPKG;  
/  
```  
  
## <a name="see-also"></a><span data-ttu-id="649f6-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="649f6-121">See Also</span></span>  
 [<span data-ttu-id="649f6-122">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="649f6-122">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 [<span data-ttu-id="649f6-123">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="649f6-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
