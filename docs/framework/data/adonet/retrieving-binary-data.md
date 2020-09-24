---
title: 擷取二進位資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: 11f7a81bc0d4b0e2a8d66387410d9a24503c7519
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150657"
---
# <a name="retrieving-binary-data"></a><span data-ttu-id="69fe6-102">擷取二進位資料</span><span class="sxs-lookup"><span data-stu-id="69fe6-102">Retrieving Binary Data</span></span>

<span data-ttu-id="69fe6-103">根據預設，如果有一整個資料列可供使用， **DataReader** 就會將傳入的資料載入為數據列。</span><span class="sxs-lookup"><span data-stu-id="69fe6-103">By default, the **DataReader** loads incoming data as a row as soon as an entire row of data is available.</span></span> <span data-ttu-id="69fe6-104">但是二進位大型物件 (BLOB) 需要不同的處理方式，因為它們所包含的資料可能高達數 GB，無法包含在單一資料列內。</span><span class="sxs-lookup"><span data-stu-id="69fe6-104">Binary large objects (BLOBs) need different treatment, however, because they can contain gigabytes of data that cannot be contained in a single row.</span></span> <span data-ttu-id="69fe6-105">**Command.Exe的 cuteReader**方法具有多載，其會採用 <xref:System.Data.CommandBehavior> 引數來修改**DataReader**的預設行為。</span><span class="sxs-lookup"><span data-stu-id="69fe6-105">The **Command.ExecuteReader** method has an overload that will take a <xref:System.Data.CommandBehavior> argument to modify the default behavior of the **DataReader**.</span></span> <span data-ttu-id="69fe6-106">您可以傳遞 <xref:System.Data.CommandBehavior.SequentialAccess> 至 **ExecuteReader** 方法來修改 **DataReader** 的預設行為，如此就不會載入資料列，而是會在收到資料時依序載入資料。</span><span class="sxs-lookup"><span data-stu-id="69fe6-106">You can pass <xref:System.Data.CommandBehavior.SequentialAccess> to the **ExecuteReader** method to modify the default behavior of the **DataReader** so that instead of loading rows of data, it will load data sequentially as it is received.</span></span> <span data-ttu-id="69fe6-107">這種方式相當適於載入 BLOB 或其他大型資料結構。</span><span class="sxs-lookup"><span data-stu-id="69fe6-107">This is ideal for loading BLOBs or other large data structures.</span></span> <span data-ttu-id="69fe6-108">請注意，這個行為取決於您的資料來源。</span><span class="sxs-lookup"><span data-stu-id="69fe6-108">Note that this behavior may depend on your data source.</span></span> <span data-ttu-id="69fe6-109">例如，從 Microsoft Access 傳回 BLOB 會將整個正在載入的 BLOB 載入記憶體，而不是在接收時循序載入。</span><span class="sxs-lookup"><span data-stu-id="69fe6-109">For example, returning a BLOB from Microsoft Access will load the entire BLOB being loaded into memory, rather than sequentially as it is received.</span></span>  
  
 <span data-ttu-id="69fe6-110">將 **DataReader** 設定為使用 **SequentialAccess**時，請務必記下存取所傳回欄位的順序。</span><span class="sxs-lookup"><span data-stu-id="69fe6-110">When setting the **DataReader** to use **SequentialAccess**, it is important to note the sequence in which you access the fields returned.</span></span> <span data-ttu-id="69fe6-111">**DataReader**的預設行為（如果有的話，會立即載入整個資料列），可讓您存取以任何順序傳回的欄位，直到下一個資料列被讀取為止。</span><span class="sxs-lookup"><span data-stu-id="69fe6-111">The default behavior of the **DataReader**, which loads an entire row as soon as it is available, allows you to access the fields returned in any order until the next row is read.</span></span> <span data-ttu-id="69fe6-112">不過，使用 **SequentialAccess** 時，您必須依序存取 **DataReader** 傳回的欄位。</span><span class="sxs-lookup"><span data-stu-id="69fe6-112">When using **SequentialAccess** however, you must access the fields returned by the **DataReader** in order.</span></span> <span data-ttu-id="69fe6-113">例如，如果您的查詢傳回三個資料行，而第三個是 BLOB，則您必須在存取第三個欄位內的 BLOB 資料前，先把第一和第二個欄位的值傳回。</span><span class="sxs-lookup"><span data-stu-id="69fe6-113">For example, if your query returns three columns, the third of which is a BLOB, you must return the values of the first and second fields before accessing the BLOB data in the third field.</span></span> <span data-ttu-id="69fe6-114">如果您在尚未存取第一和第二個欄位前先存取第三個欄位，便無法再使用第一和第二個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="69fe6-114">If you access the third field before the first or second fields, the first and second field values are no longer available.</span></span> <span data-ttu-id="69fe6-115">這是因為 **SequentialAccess** 已修改 **datareader** 以依序傳回資料，而 **datareader** 讀取後，資料無法使用。</span><span class="sxs-lookup"><span data-stu-id="69fe6-115">This is because **SequentialAccess** has modified the **DataReader** to return data in sequence and the data is not available after the **DataReader** has read past it.</span></span>  
  
 <span data-ttu-id="69fe6-116">存取 BLOB 欄位中的資料時，請使用**DataReader**的**GetBytes**或**GetChars**具類型存取子，這會將資料填入陣列。</span><span class="sxs-lookup"><span data-stu-id="69fe6-116">When accessing the data in the BLOB field, use the **GetBytes** or **GetChars** typed accessors of the **DataReader**, which fill an array with data.</span></span> <span data-ttu-id="69fe6-117">您也可以對字元資料使用 **GetString** ;然而。</span><span class="sxs-lookup"><span data-stu-id="69fe6-117">You can also use **GetString** for character data; however.</span></span> <span data-ttu-id="69fe6-118">為了節省系統資統，您可能不想要將整個 BLOB 值載入單一字串變數。</span><span class="sxs-lookup"><span data-stu-id="69fe6-118">to conserve system resources you might not want to load an entire BLOB value into a single string variable.</span></span> <span data-ttu-id="69fe6-119">您可以指定傳回資料的特定緩衝區大小，以及從傳回資料讀取的第一個位元組或字元的開始位置。</span><span class="sxs-lookup"><span data-stu-id="69fe6-119">You can instead specify a specific buffer size of data to be returned, and a starting location for the first byte or character to be read from the returned data.</span></span> <span data-ttu-id="69fe6-120">**GetBytes** 和 **GetChars** 會 `long` 傳回值，代表傳回的位元組數目或字元數。</span><span class="sxs-lookup"><span data-stu-id="69fe6-120">**GetBytes** and **GetChars** will return a `long` value, which represents the number of bytes or characters returned.</span></span> <span data-ttu-id="69fe6-121">如果您將 null 陣列傳遞給 **GetBytes** 或 **GetChars**，則傳回的長數值將會是 BLOB 中的位元組總數或字元數。</span><span class="sxs-lookup"><span data-stu-id="69fe6-121">If you pass a null array to **GetBytes** or **GetChars**, the long value returned will be the total number of bytes or characters in the BLOB.</span></span> <span data-ttu-id="69fe6-122">您可以選擇將陣列內的索引指定為要讀取資料的開始位置。</span><span class="sxs-lookup"><span data-stu-id="69fe6-122">You can optionally specify an index in the array as a starting position for the data being read.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69fe6-123">範例</span><span class="sxs-lookup"><span data-stu-id="69fe6-123">Example</span></span>  

 <span data-ttu-id="69fe6-124">下列範例會從 Microsoft SQL Server 中的 **pubs** 範例資料庫，傳回發行者識別碼和標誌。</span><span class="sxs-lookup"><span data-stu-id="69fe6-124">The following example returns the publisher ID and logo from the **pubs** sample database in Microsoft SQL Server.</span></span> <span data-ttu-id="69fe6-125">發行者識別碼 (`pub_id`) 是一個字元欄位，而商標則是 BLOB 影像。</span><span class="sxs-lookup"><span data-stu-id="69fe6-125">The publisher ID (`pub_id`) is a character field, and the logo is an image, which is a BLOB.</span></span> <span data-ttu-id="69fe6-126">由於 **標誌** 欄位是點陣圖，因此範例會使用 **GetBytes**傳回二進位資料。</span><span class="sxs-lookup"><span data-stu-id="69fe6-126">Because the **logo** field is a bitmap, the example returns binary data using **GetBytes**.</span></span> <span data-ttu-id="69fe6-127">請注意，由於欄位必須被循序存取，所以您要先存取目前資料列的發行者 ID，再存取標誌。</span><span class="sxs-lookup"><span data-stu-id="69fe6-127">Notice that the publisher ID is accessed for the current row of data before the logo, because the fields must be accessed sequentially.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="69fe6-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69fe6-128">See also</span></span>

- [<span data-ttu-id="69fe6-129">SQL Server 二進位和大數值資料</span><span class="sxs-lookup"><span data-stu-id="69fe6-129">SQL Server Binary and Large-Value Data</span></span>](./sql/sql-server-binary-and-large-value-data.md)
- <span data-ttu-id="69fe6-130">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="69fe6-130">[ADO.NET Overview](ado-net-overview.md)</span></span>
