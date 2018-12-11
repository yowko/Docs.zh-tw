---
title: REF CURSOR 範例
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: 7edb9cd41c7949dba6c4a5c24179c30d01309214
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127949"
---
# <a name="ref-cursor-examples"></a>REF CURSOR 範例
REF CURSOR 範例包括下列三個 Microsoft Visual Basic 範例，示範如何使用 REF CURSOR：  
  
|範例|描述|  
|------------|-----------------|  
|[OracleDataReader 中的 REF CURSOR 參數](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)|此範例執行可傳回 REF CURSOR 參數的 PL/SQL 預存程序，並以 <xref:System.Data.OracleClient.OracleDataReader> 讀取值。|  
|[使用 OracleDataReader 從多個 REF CURSOR 擷取資料](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)|此範例執行傳回兩個 REF CURSOR 參數，並讀取使用的值的 PL/SQL 預存程序**OracleDataReader**。|  
|[使用一或多個 REF CURSOR 填入資料集](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)|此範例執行可傳回兩個 REF CURSOR 參數的 PL/SQL 預存程序，並使用傳回的資料列填入 <xref:System.Data.DataSet>。|  
  
 若要使用這些範例，您可能需要建立 Oracle 資料表，且必須建立 PL/SQL 封裝及封裝主體。  
  
## <a name="creating-the-oracle-tables"></a>建立 Oracle 資料表  
 這些範例使用定義在 Oracle Scott/Tiger 結構描述中的資料表。 大多數 Oracle 安裝都包含 Oracle Scott/Tiger 結構描述。 如果此結構描述不存在，則可使用 {OracleHome}\rdbms\admin\scott.sql 中的 SQL 命令檔案，來建立這些範例所使用的資料表及索引。  
  
## <a name="creating-the-oracle-package-and-package-body"></a>建立 Oracle 封裝及封裝主體  
 這些範例需要伺服器上的下列 PL/SQL 封裝及封裝主體。 在 Oracle 伺服器上建立下列 Oracle 封裝。  
  
```sql
CREATE OR REPLACE PACKAGE CURSPKG AS   
    TYPE T_CURSOR IS REF CURSOR;   
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,   
                               IO_CURSOR IN OUT T_CURSOR);   
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
                                DEPTCURSOR OUT T_CURSOR);  
END CURSPKG;  
/   
```  
  
 在 Oracle 伺服器上建立下列 Oracle Package 內容。  
  
```sql
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
  
## <a name="see-also"></a>另請參閱  
 [Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
