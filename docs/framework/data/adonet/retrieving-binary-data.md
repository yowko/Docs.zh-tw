---
title: 擷取二進位資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: c914a9b0780e2e87e177502b0f9faff0e7c4b617
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149046"
---
# <a name="retrieving-binary-data"></a>擷取二進位資料
預設情況下 **，DataReader**在整行資料可用後立即將傳入資料作為行載入。 但是二進位大型物件 (BLOB) 需要不同的處理方式，因為它們所包含的資料可能高達數 GB，無法包含在單一資料列內。 **Command.ExecuteReader**方法具有重載，它將採用<xref:System.Data.CommandBehavior>參數來修改**DataReader**的預設行為。 您可以傳遞到<xref:System.Data.CommandBehavior.SequentialAccess> **ExecuteReader**方法來修改**DataReader**的預設行為，以便資料行在接收時將按順序載入資料，而不是載入資料行。 這種方式相當適於載入 BLOB 或其他大型資料結構。 請注意，這個行為取決於您的資料來源。 例如，從 Microsoft Access 傳回 BLOB 會將整個正在載入的 BLOB 載入記憶體，而不是在接收時循序載入。  
  
 將**DataReader**設置為使用**循序存取**時，請務必注意訪問返回的欄位的順序。 **DataReader**的預設行為（只要行可用就載入整行）允許您訪問以任何順序返回的欄位，直到讀取下一行。 但是，使用**循序存取**時，您必須按循序存取**DataReader**返回的欄位。 例如，如果您的查詢傳回三個資料行，而第三個是 BLOB，則您必須在存取第三個欄位內的 BLOB 資料前，先把第一和第二個欄位的值傳回。 如果您在尚未存取第一和第二個欄位前先存取第三個欄位，便無法再使用第一和第二個欄位的值。 這是因為**循序存取**已修改**DataReader**以按順序返回資料，並且資料在**DataReader**讀取完資料後不可用。  
  
 訪問 BLOB 欄位中的資料時，請使用**GetBytes**或**GetChars**鍵入**的資料讀取器**的訪問器，後者將陣列填充資料。 您還可以對字元資料使用**GetString;** 然而。 為了節省系統資統，您可能不想要將整個 BLOB 值載入單一字串變數。 您可以指定傳回資料的特定緩衝區大小，以及從傳回資料讀取的第一個位元組或字元的開始位置。 **GetBytes**和**GetChars** `long`將返回一個值，該值表示返回的位元組數或字元數。 如果將空陣列傳遞給**GetBytes**或**GetChars，** 則返回的長值將是 BLOB 中的位元組或字元的總數。 您可以選擇將陣列內的索引指定為要讀取資料的開始位置。  
  
## <a name="example"></a>範例  
 下面的示例從 Microsoft SQL Server 中的**pubs**示例資料庫中返回發行者 ID 和徽標。 發行者識別碼 (`pub_id`) 是一個字元欄位，而商標則是 BLOB 影像。 由於**徽標**欄位是點陣圖，因此該示例使用**GetBytes**返回二進位資料。 請注意，由於欄位必須被循序存取，所以您要先存取目前資料列的發行者 ID，再存取標誌。  
  
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
  
## <a name="see-also"></a>另請參閱

- [SQL 伺服器二進位和大值資料](./sql/sql-server-binary-and-large-value-data.md)
- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
