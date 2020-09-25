---
title: 從檔案插入影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 35900aa2-5615-4174-8212-ba184c6b82fb
ms.openlocfilehash: e70576637d44e874532aa06da4fe94115ac8ed9c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194579"
---
# <a name="inserting-an-image-from-a-file"></a><span data-ttu-id="0af50-102">從檔案插入影像</span><span class="sxs-lookup"><span data-stu-id="0af50-102">Inserting an Image from a File</span></span>

<span data-ttu-id="0af50-103">視資料來源的欄位類型而定，您可以將二進位大型物件 (BLOB) 當做二進位或字元資料寫入到資料庫。</span><span class="sxs-lookup"><span data-stu-id="0af50-103">You can write a binary large object (BLOB) to a database as either binary or character data, depending on the type of field at your data source.</span></span> <span data-ttu-id="0af50-104">BLOB 是參考 `text`、`ntext` 與 `image` 資料類型的一般詞彙，通常包含文件與圖片。</span><span class="sxs-lookup"><span data-stu-id="0af50-104">BLOB is a generic term that refers to the `text`, `ntext`, and `image` data types, which typically contain documents and pictures.</span></span>  
  
 <span data-ttu-id="0af50-105">若要將 BLOB 值寫入您的資料庫，請發出適當的 INSERT 或 UPDATE 語句，並以輸入參數的形式傳遞 BLOB 值 (查看) 設定 [參數和參數資料類型](../configuring-parameters-and-parameter-data-types.md) 。</span><span class="sxs-lookup"><span data-stu-id="0af50-105">To write a BLOB value to your database, issue the appropriate INSERT or UPDATE statement and pass the BLOB value as an input parameter (see [Configuring Parameters and Parameter Data Types](../configuring-parameters-and-parameter-data-types.md)).</span></span> <span data-ttu-id="0af50-106">如果您的 BLOB 儲存為文字 (例如 SQL Server `text` 欄位)，您可以將 BLOB 以字串參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="0af50-106">If your BLOB is stored as text, such as a SQL Server `text` field, you can pass the BLOB as a string parameter.</span></span> <span data-ttu-id="0af50-107">如果 BLOB 是以二進位格式 (例如 SQL Server `image` 欄位) 儲存的，您可以將 `byte` 類型的陣列以二進位參數方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="0af50-107">If the BLOB is stored in binary format, such as a SQL Server `image` field, you can pass an array of type `byte` as a binary parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0af50-108">範例</span><span class="sxs-lookup"><span data-stu-id="0af50-108">Example</span></span>  

 <span data-ttu-id="0af50-109">下列程式碼範例會將員工資訊新增到 Northwind 資料庫的 Employees 資料表。</span><span class="sxs-lookup"><span data-stu-id="0af50-109">The following code example adds employee information to the Employees table in the Northwind database.</span></span> <span data-ttu-id="0af50-110">員工的相片會從檔案讀取，並新增至資料表中的 [相片] 欄位，也就是影像欄位。</span><span class="sxs-lookup"><span data-stu-id="0af50-110">A photo of the employee is read from a file and added to the Photo field in the table, which is an image field.</span></span>  
  
```vb  
Public Shared Sub AddEmployee( _  
  lastName As String, _  
  firstName As String, _  
  title As String, _  
  hireDate As DateTime, _  
  reportsTo As Integer, _  
  photoFilePath As String, _  
  connectionString As String)  
  
  Dim photo() as Byte = GetPhoto(photoFilePath)  
  
  Using connection As SqlConnection = New SqlConnection( _  
    connectionString)  
  
  Dim command As SqlCommand = New SqlCommand( _  
    "INSERT INTO Employees (LastName, FirstName, Title, " & _  
    "HireDate, ReportsTo, Photo) " & _  
    "Values(@LastName, @FirstName, @Title, " & _  
    "@HireDate, @ReportsTo, @Photo)", connection)
  
  command.Parameters.Add("@LastName",  _  
    SqlDbType.NVarChar, 20).Value = lastName  
  command.Parameters.Add("@FirstName", _  
    SqlDbType.NVarChar, 10).Value = firstName  
  command.Parameters.Add("@Title", _  
    SqlDbType.NVarChar, 30).Value = title  
  command.Parameters.Add("@HireDate", _  
    SqlDbType.DateTime).Value = hireDate  
  command.Parameters.Add("@ReportsTo", _  
    SqlDbType.Int).Value = reportsTo  
  
  command.Parameters.Add("@Photo", _  
    SqlDbType.Image, photo.Length).Value = photo  
  
  connection.Open()  
  command.ExecuteNonQuery()  
  
  End Using  
End Sub  
  
Public Shared Function GetPhoto(filePath As String) As Byte()  
  Dim stream As FileStream = new FileStream( _  
     filePath, FileMode.Open, FileAccess.Read)  
  Dim reader As BinaryReader = new BinaryReader(stream)  
  
  Dim photo() As Byte = reader.ReadBytes(stream.Length)  
  
  reader.Close()  
  stream.Close()  
  
  Return photo  
End Function  
```  
  
```csharp  
public static void AddEmployee(  
  string lastName,
  string firstName,
  string title,
  DateTime hireDate,
  int reportsTo,
  string photoFilePath,
  string connectionString)  
{  
  byte[] photo = GetPhoto(photoFilePath);  
  
  using (SqlConnection connection = new SqlConnection(  
    connectionString))  
  
  SqlCommand command = new SqlCommand(  
    "INSERT INTO Employees (LastName, FirstName, " +  
    "Title, HireDate, ReportsTo, Photo) " +  
    "Values(@LastName, @FirstName, @Title, " +  
    "@HireDate, @ReportsTo, @Photo)", connection);
  
  command.Parameters.Add("@LastName",
     SqlDbType.NVarChar, 20).Value = lastName;  
  command.Parameters.Add("@FirstName",
      SqlDbType.NVarChar, 10).Value = firstName;  
  command.Parameters.Add("@Title",
      SqlDbType.NVarChar, 30).Value = title;  
  command.Parameters.Add("@HireDate",
       SqlDbType.DateTime).Value = hireDate;  
  command.Parameters.Add("@ReportsTo",
      SqlDbType.Int).Value = reportsTo;  
  
  command.Parameters.Add("@Photo",  
      SqlDbType.Image, photo.Length).Value = photo;  
  
  connection.Open();  
  command.ExecuteNonQuery();  
  }  
}  
  
public static byte[] GetPhoto(string filePath)  
{  
  FileStream stream = new FileStream(  
      filePath, FileMode.Open, FileAccess.Read);  
  BinaryReader reader = new BinaryReader(stream);  
  
  byte[] photo = reader.ReadBytes((int)stream.Length);  
  
  reader.Close();  
  stream.Close();  
  
  return photo;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0af50-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0af50-111">See also</span></span>

- [<span data-ttu-id="0af50-112">使用命令修改資料</span><span class="sxs-lookup"><span data-stu-id="0af50-112">Using Commands to Modify Data</span></span>](../using-commands-to-modify-data.md)
- [<span data-ttu-id="0af50-113">擷取二進位資料</span><span class="sxs-lookup"><span data-stu-id="0af50-113">Retrieving Binary Data</span></span>](../retrieving-binary-data.md)
- [<span data-ttu-id="0af50-114">SQL Server 二進位和大數值資料</span><span class="sxs-lookup"><span data-stu-id="0af50-114">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="0af50-115">SQL Server 資料類型對應</span><span class="sxs-lookup"><span data-stu-id="0af50-115">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- <span data-ttu-id="0af50-116">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="0af50-116">[ADO.NET Overview](../ado-net-overview.md)</span></span>
