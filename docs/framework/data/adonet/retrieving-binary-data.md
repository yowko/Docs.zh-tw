---
title: 擷取二進位資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: 302c26571e9843a4b7c3c440969e4159ef2d10ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362572"
---
# <a name="retrieving-binary-data"></a><span data-ttu-id="990b1-102">擷取二進位資料</span><span class="sxs-lookup"><span data-stu-id="990b1-102">Retrieving Binary Data</span></span>
<span data-ttu-id="990b1-103">根據預設， **DataReader**整列資料可用時，內送資料載入為資料列。</span><span class="sxs-lookup"><span data-stu-id="990b1-103">By default, the **DataReader** loads incoming data as a row as soon as an entire row of data is available.</span></span> <span data-ttu-id="990b1-104">但是二進位大型物件 (BLOB) 需要不同的處理方式，因為它們所包含的資料可能高達數 GB，無法包含在單一資料列內。</span><span class="sxs-lookup"><span data-stu-id="990b1-104">Binary large objects (BLOBs) need different treatment, however, because they can contain gigabytes of data that cannot be contained in a single row.</span></span> <span data-ttu-id="990b1-105">**Command.ExecuteReader**方法具有多載會採用<xref:System.Data.CommandBehavior>引數以修改預設行為**DataReader**。</span><span class="sxs-lookup"><span data-stu-id="990b1-105">The **Command.ExecuteReader** method has an overload that will take a <xref:System.Data.CommandBehavior> argument to modify the default behavior of the **DataReader**.</span></span> <span data-ttu-id="990b1-106">您可以傳遞<xref:System.Data.CommandBehavior.SequentialAccess>至**ExecuteReader**方法，以修改預設行為**DataReader**以便而不是正在載入的資料列，它將會載入資料以循序方式在接收時。</span><span class="sxs-lookup"><span data-stu-id="990b1-106">You can pass <xref:System.Data.CommandBehavior.SequentialAccess> to the **ExecuteReader** method to modify the default behavior of the **DataReader** so that instead of loading rows of data, it will load data sequentially as it is received.</span></span> <span data-ttu-id="990b1-107">這種方式相當適於載入 BLOB 或其他大型資料結構。</span><span class="sxs-lookup"><span data-stu-id="990b1-107">This is ideal for loading BLOBs or other large data structures.</span></span> <span data-ttu-id="990b1-108">請注意，這個行為取決於您的資料來源。</span><span class="sxs-lookup"><span data-stu-id="990b1-108">Note that this behavior may depend on your data source.</span></span> <span data-ttu-id="990b1-109">例如，從 Microsoft Access 傳回 BLOB 會將整個正在載入的 BLOB 載入記憶體，而不是在接收時循序載入。</span><span class="sxs-lookup"><span data-stu-id="990b1-109">For example, returning a BLOB from Microsoft Access will load the entire BLOB being loaded into memory, rather than sequentially as it is received.</span></span>  
  
 <span data-ttu-id="990b1-110">設定時**DataReader**使用**SequentialAccess**，請務必注意存取傳回欄位的順序。</span><span class="sxs-lookup"><span data-stu-id="990b1-110">When setting the **DataReader** to use **SequentialAccess**, it is important to note the sequence in which you access the fields returned.</span></span> <span data-ttu-id="990b1-111">預設行為**DataReader**，並使用，因為載入整個資料列可讓您存取讀取下一個資料列之前，依照任何順序傳回的欄位。</span><span class="sxs-lookup"><span data-stu-id="990b1-111">The default behavior of the **DataReader**, which loads an entire row as soon as it is available, allows you to access the fields returned in any order until the next row is read.</span></span> <span data-ttu-id="990b1-112">當使用**SequentialAccess**不過，您必須存取傳回的欄位**DataReader**順序。</span><span class="sxs-lookup"><span data-stu-id="990b1-112">When using **SequentialAccess** however, you must access the fields returned by the **DataReader** in order.</span></span> <span data-ttu-id="990b1-113">例如，如果您的查詢傳回三個資料行，而第三個是 BLOB，則您必須在存取第三個欄位內的 BLOB 資料前，先把第一和第二個欄位的值傳回。</span><span class="sxs-lookup"><span data-stu-id="990b1-113">For example, if your query returns three columns, the third of which is a BLOB, you must return the values of the first and second fields before accessing the BLOB data in the third field.</span></span> <span data-ttu-id="990b1-114">如果您在尚未存取第一和第二個欄位前先存取第三個欄位，便無法再使用第一和第二個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="990b1-114">If you access the third field before the first or second fields, the first and second field values are no longer available.</span></span> <span data-ttu-id="990b1-115">這是因為**SequentialAccess**已經修改**DataReader**順序和資料中傳回資料不是之後，才能使用**DataReader**讀過。</span><span class="sxs-lookup"><span data-stu-id="990b1-115">This is because **SequentialAccess** has modified the **DataReader** to return data in sequence and the data is not available after the **DataReader** has read past it.</span></span>  
  
 <span data-ttu-id="990b1-116">當存取 BLOB 欄位的資料，請使用**GetBytes**或**GetChars**具類型的存取子**DataReader**，以資料填入陣列。</span><span class="sxs-lookup"><span data-stu-id="990b1-116">When accessing the data in the BLOB field, use the **GetBytes** or **GetChars** typed accessors of the **DataReader**, which fill an array with data.</span></span> <span data-ttu-id="990b1-117">您也可以使用**GetString**字元資料; 不過。</span><span class="sxs-lookup"><span data-stu-id="990b1-117">You can also use **GetString** for character data; however.</span></span> <span data-ttu-id="990b1-118">為了節省系統資統，您可能不想要將整個 BLOB 值載入單一字串變數。</span><span class="sxs-lookup"><span data-stu-id="990b1-118">to conserve system resources you might not want to load an entire BLOB value into a single string variable.</span></span> <span data-ttu-id="990b1-119">您可以指定傳回資料的特定緩衝區大小，以及從傳回資料讀取的第一個位元組或字元的開始位置。</span><span class="sxs-lookup"><span data-stu-id="990b1-119">You can instead specify a specific buffer size of data to be returned, and a starting location for the first byte or character to be read from the returned data.</span></span> <span data-ttu-id="990b1-120">**GetBytes**和**GetChars**會傳回`long`值，表示傳回的字元或位元組數目。</span><span class="sxs-lookup"><span data-stu-id="990b1-120">**GetBytes** and **GetChars** will return a `long` value, which represents the number of bytes or characters returned.</span></span> <span data-ttu-id="990b1-121">如果您傳遞 null 陣列**GetBytes**或**GetChars**，則長傳回值會是位元組或 BLOB 中的字元總數。</span><span class="sxs-lookup"><span data-stu-id="990b1-121">If you pass a null array to **GetBytes** or **GetChars**, the long value returned will be the total number of bytes or characters in the BLOB.</span></span> <span data-ttu-id="990b1-122">您可以選擇將陣列內的索引指定為要讀取資料的開始位置。</span><span class="sxs-lookup"><span data-stu-id="990b1-122">You can optionally specify an index in the array as a starting position for the data being read.</span></span>  
  
## <a name="example"></a><span data-ttu-id="990b1-123">範例</span><span class="sxs-lookup"><span data-stu-id="990b1-123">Example</span></span>  
 <span data-ttu-id="990b1-124">下列範例會傳回發行者 ID 與商標從**pubs** Microsoft SQL Server 中的範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="990b1-124">The following example returns the publisher ID and logo from the **pubs** sample database in Microsoft SQL Server.</span></span> <span data-ttu-id="990b1-125">發行者識別碼 (`pub_id`) 是一個字元欄位，而商標則是 BLOB 影像。</span><span class="sxs-lookup"><span data-stu-id="990b1-125">The publisher ID (`pub_id`) is a character field, and the logo is an image, which is a BLOB.</span></span> <span data-ttu-id="990b1-126">因為**標誌**欄位是點陣圖，此範例會傳回二進位資料使用**GetBytes**。</span><span class="sxs-lookup"><span data-stu-id="990b1-126">Because the **logo** field is a bitmap, the example returns binary data using **GetBytes**.</span></span> <span data-ttu-id="990b1-127">請注意，由於欄位必須被循序存取，所以您要先存取目前資料列的發行者 ID，再存取標誌。</span><span class="sxs-lookup"><span data-stu-id="990b1-127">Notice that the publisher ID is accessed for the current row of data before the logo, because the fields must be accessed sequentially.</span></span>  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim command As SqlCommand = New SqlCommand( _  
  "SELECT pub_id, logo FROM pub_info", connection)  
  
' Writes the BLOB to a file (*.bmp).  
Dim stream As FileStream                   
' Streams the binary data to the FileStream object.  
Dim writer As BinaryWriter                 
' The size of the BLOB buffer.  
Dim bufferSize As Integer = 100        
' The BLOB byte() buffer to be filled by GetBytes.  
Dim outByte(bufferSize - 1) As Byte    
' The bytes returned from GetBytes.  
Dim retval As Long                     
' The starting position in the BLOB output.  
Dim startIndex As Long = 0             
  
' The publisher id to use in the file name.  
Dim pubID As String = ""              
  
' Open the connection and read data into the DataReader.  
connection.Open()  
Dim reader As SqlDataReader = command.ExecuteReader(CommandBehavior.SequentialAccess)  
  
Do While reader.Read()  
  ' Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0)  
  
  ' Create a file to hold the output.  
  stream = New FileStream( _  
    "logo" & pubID & ".bmp", FileMode.OpenOrCreate, FileAccess.Write)  
  writer = New BinaryWriter(stream)  
  
  ' Reset the starting byte for a new BLOB.  
  startIndex = 0  
  
  ' Read bytes into outByte() and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  
  ' Continue while there are bytes beyond the size of the buffer.  
  Do While retval = bufferSize  
    writer.Write(outByte)  
    writer.Flush()  
  
    ' Reposition start index to end of the last buffer and fill buffer.  
    startIndex += bufferSize  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  Loop  
  
  ' Write the remaining buffer.  
  writer.Write(outByte, 0 , retval - 1)  
  writer.Flush()  
  
  ' Close the output file.  
  writer.Close()  
  stream.Close()  
Loop  
  
' Close the reader and the connection.  
reader.Close()  
connection.Close()  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlCommand command = new SqlCommand(  
  "SELECT pub_id, logo FROM pub_info", connection);  
  
// Writes the BLOB to a file (*.bmp).  
FileStream stream;                            
// Streams the BLOB to the FileStream object.  
BinaryWriter writer;                          
  
// Size of the BLOB buffer.  
int bufferSize = 100;                     
// The BLOB byte[] buffer to be filled by GetBytes.  
byte[] outByte = new byte[bufferSize];    
// The bytes returned from GetBytes.  
long retval;                              
// The starting position in the BLOB output.  
long startIndex = 0;                      
  
// The publisher id to use in the file name.  
string pubID = "";                       
  
// Open the connection and read data into the DataReader.  
connection.Open();  
SqlDataReader reader = command.ExecuteReader(CommandBehavior.SequentialAccess);  
  
while (reader.Read())  
{  
  // Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0);    
  
  // Create a file to hold the output.  
  stream = new FileStream(  
    "logo" + pubID + ".bmp", FileMode.OpenOrCreate, FileAccess.Write);  
  writer = new BinaryWriter(stream);  
  
  // Reset the starting byte for the new BLOB.  
  startIndex = 0;  
  
  // Read bytes into outByte[] and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  
  // Continue while there are bytes beyond the size of the buffer.  
  while (retval == bufferSize)  
  {  
    writer.Write(outByte);  
    writer.Flush();  
  
    // Reposition start index to end of last buffer and fill buffer.  
    startIndex += bufferSize;  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  }  
  
  // Write the remaining buffer.  
  writer.Write(outByte, 0, (int)retval);  
  writer.Flush();  
  
  // Close the output file.  
  writer.Close();  
  stream.Close();  
}  
  
// Close the reader and the connection.  
reader.Close();  
connection.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="990b1-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="990b1-128">See Also</span></span>  
 [<span data-ttu-id="990b1-129">使用 Datareader</span><span class="sxs-lookup"><span data-stu-id="990b1-129">Working with DataReaders</span></span>](http://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [<span data-ttu-id="990b1-130">SQL Server 二進位和大量數值資料</span><span class="sxs-lookup"><span data-stu-id="990b1-130">SQL Server Binary and Large-Value Data</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="990b1-131">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="990b1-131">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
