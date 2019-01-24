---
title: OracleType
ms.date: 03/30/2017
ms.assetid: 18143304-d5c7-4c95-9995-678088d0c142
ms.openlocfilehash: e849de365fa9922a9c1552f2d25b613d1df01d2b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529434"
---
# <a name="oracletypes"></a><span data-ttu-id="e7319-102">OracleType</span><span class="sxs-lookup"><span data-stu-id="e7319-102">OracleTypes</span></span>
<span data-ttu-id="e7319-103">Oracle 的 .NET Framework 資料提供者包括數個可讓您使用 Oracle 資料型別的結構。</span><span class="sxs-lookup"><span data-stu-id="e7319-103">The .NET Framework Data Provider for Oracle includes several structures you can use to work with Oracle data types.</span></span> <span data-ttu-id="e7319-104">這些結構包括 <xref:System.Data.OracleClient.OracleNumber> 及 <xref:System.Data.OracleClient.OracleString>。</span><span class="sxs-lookup"><span data-stu-id="e7319-104">These include <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7319-105">如需這些結構的完整清單，請參閱 <xref:System.Data.OracleClient>。</span><span class="sxs-lookup"><span data-stu-id="e7319-105">For a complete list of these structures, see <xref:System.Data.OracleClient>.</span></span>  
  
 <span data-ttu-id="e7319-106">下列 C# 範例：</span><span class="sxs-lookup"><span data-stu-id="e7319-106">The following C# examples:</span></span>  
  
-   <span data-ttu-id="e7319-107">建立 Oracle 資料表並為其載入資料。</span><span class="sxs-lookup"><span data-stu-id="e7319-107">Create an Oracle table and load it with data.</span></span>  
  
-   <span data-ttu-id="e7319-108">使用 <xref:System.Data.OracleClient.OracleDataReader> 存取資料，並使用數個 <xref:System.Data.OracleClient.OracleType> 結構顯示資料。</span><span class="sxs-lookup"><span data-stu-id="e7319-108">Use an <xref:System.Data.OracleClient.OracleDataReader> to access the data, and use several <xref:System.Data.OracleClient.OracleType> structures to display the data.</span></span>  
  
## <a name="creating-an-oracle-table"></a><span data-ttu-id="e7319-109">建立 Oracle 資料表</span><span class="sxs-lookup"><span data-stu-id="e7319-109">Creating an Oracle Table</span></span>  
 <span data-ttu-id="e7319-110">此範例建立 Oracle 資料表並為其載入資料。</span><span class="sxs-lookup"><span data-stu-id="e7319-110">This example creates an Oracle table and loads it with data.</span></span> <span data-ttu-id="e7319-111">您必須先執行此範例，才能執行下一個範例。</span><span class="sxs-lookup"><span data-stu-id="e7319-111">You must run this example before running the next example.</span></span>  
  
```csharp  
public void Setup(string connectionString)  
   {  
   OracleConnection conn = new OracleConnection(connectionString);  
   try  
      {  
      conn.Open();  
      OracleCommand cmd = conn.CreateCommand();  
      cmd.CommandText ="CREATE TABLE OracleTypesTable " +  
        "(MyVarchar2 varchar2(3000),MyNumber number(28,4) " +  
        "PRIMARY KEY ,MyDate date, MyRaw raw(255))";  
      cmd.ExecuteNonQuery();  
      cmd.CommandText ="INSERT INTO OracleTypesTable VALUES " +  
        "( 'test', 2, to_date('2000-01-11 12:54:01','yyyy-mm-dd " +  
        "hh24:mi:ss'), '0001020304' )";  
      cmd.ExecuteNonQuery();  
      }  
   catch(Exception)  
   {  
   }  
   finally  
   {  
      conn.Close();  
   }  
}  
```  
  
## <a name="retrieving-data-from-the-oracle-table"></a><span data-ttu-id="e7319-112">從 Oracle 資料表擷取資料</span><span class="sxs-lookup"><span data-stu-id="e7319-112">Retrieving Data from the Oracle Table</span></span>  
 <span data-ttu-id="e7319-113">這個範例會使用**OracleDataReader**存取資料，並使用數個**OracleType**結構顯示資料。</span><span class="sxs-lookup"><span data-stu-id="e7319-113">This example uses an **OracleDataReader** to access the data, and uses several **OracleType** structures to display the data.</span></span>  
  
```csharp  
public void ReadOracleTypesExample(string connectionString)  
   {  
   OracleConnection myConnection =   
      new OracleConnection(connectionString);  
   myConnection.Open();  
   OracleCommand myCommand = myConnection.CreateCommand();  
  
   try  
      {  
      myCommand.CommandText = "SELECT * from OracleTypesTable";  
      OracleDataReader oracledatareader1 = myCommand.ExecuteReader();  
      oracledatareader1.Read();  
  
      //Using the oracle specific getters for each type is faster than  
      //using GetOracleValue.  
  
      //First column, MyVarchar2, is a VARCHAR2 data type in Oracle  
      //Server and maps to OracleString.  
      OracleString oraclestring1 =   
        oracledatareader1.GetOracleString(0);  
      Console.WriteLine("OracleString " + oraclestring1.ToString());  
  
      //Second column, MyNumber, is a NUMBER data type in Oracle Server  
      //and maps to OracleNumber.  
      OracleNumber oraclenumber1 =   
        oracledatareader1.GetOracleNumber(1);  
      Console.WriteLine("OracleNumber " + oraclenumber1.ToString());  
  
      //Third column, MyDate, is a DATA data type in Oracle Server  
      //and maps to OracleDateTime.  
      OracleDateTime oracledatetime1 =   
        oracledatareader1.GetOracleDateTime(2);  
      Console.WriteLine("OracleDateTime " + oracledatetime1.ToString());  
  
      //Fourth column, MyRaw, is a RAW data type in Oracle Server and  
      //maps to OracleBinary.  
      OracleBinary oraclebinary1 =   
        oracledatareader1.GetOracleBinary(3);  
      //Calling value on a null OracleBinary throws  
      //OracleNullValueException; therefore, check for a null value.  
      if (oraclebinary1.IsNull==false)  
      {  
         foreach(byte b in oraclebinary1.Value)  
         {  
            Console.WriteLine("byte " + b.ToString());  
         }  
      }  
      oracledatareader1.Close();  
   }  
   catch(Exception e)  
   {  
       Console.WriteLine(e.ToString());  
   }  
   finally  
   {  
       myConnection.Close();  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7319-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7319-114">See also</span></span>
- [<span data-ttu-id="e7319-115">Oracle 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e7319-115">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [<span data-ttu-id="e7319-116">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="e7319-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
