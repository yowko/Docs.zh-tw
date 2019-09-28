---
title: 加密資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET Framework], symmetric
- symmetric encryption
- cryptography [.NET Framework], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d37f7980c3024fa545e5395a4614dcd41a111794
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353195"
---
# <a name="encrypting-data"></a><span data-ttu-id="8c924-102">加密資料</span><span class="sxs-lookup"><span data-stu-id="8c924-102">Encrypting Data</span></span>
<span data-ttu-id="8c924-103">對稱式加密和非對稱式加密是使用不同的程序執行。</span><span class="sxs-lookup"><span data-stu-id="8c924-103">Symmetric encryption and asymmetric encryption are performed using different processes.</span></span> <span data-ttu-id="8c924-104">對稱式加密在資料流上執行，因此適用於加密大量資料。</span><span class="sxs-lookup"><span data-stu-id="8c924-104">Symmetric encryption is performed on streams and is therefore useful to encrypt large amounts of data.</span></span> <span data-ttu-id="8c924-105">非對稱式加密在少數的位元組上執行，因此只適用於小量的資料。</span><span class="sxs-lookup"><span data-stu-id="8c924-105">Asymmetric encryption is performed on a small number of bytes and is therefore useful only for small amounts of data.</span></span>  
  
## <a name="symmetric-encryption"></a><span data-ttu-id="8c924-106">對稱加密</span><span class="sxs-lookup"><span data-stu-id="8c924-106">Symmetric Encryption</span></span>  
 <span data-ttu-id="8c924-107">Managed 對稱式密碼編譯類別可搭配特殊的資料流類別，稱為 <xref:System.Security.Cryptography.CryptoStream> ，它會加密讀入資料流的資料。</span><span class="sxs-lookup"><span data-stu-id="8c924-107">The managed symmetric cryptography classes are used with a special stream class called a <xref:System.Security.Cryptography.CryptoStream> that encrypts data read into the stream.</span></span> <span data-ttu-id="8c924-108">**CryptoStream** 類別初始化時具有 Managed 資料流類別初始化、實作 <xref:System.Security.Cryptography.ICryptoTransform> 介面 (從實作密碼編譯演算法的類別建立) 的類別，以及描述允許對 <xref:System.Security.Cryptography.CryptoStreamMode> CryptoStream **執行之存取類型的**列舉。</span><span class="sxs-lookup"><span data-stu-id="8c924-108">The **CryptoStream** class is initialized with a managed stream class, a class implements the <xref:System.Security.Cryptography.ICryptoTransform> interface (created from a class that implements a cryptographic algorithm), and a <xref:System.Security.Cryptography.CryptoStreamMode> enumeration that describes the type of access permitted to the **CryptoStream**.</span></span> <span data-ttu-id="8c924-109">**CryptoStream** 類別可以使用衍生自 <xref:System.IO.Stream> 類別的任何類別初始化，包括 <xref:System.IO.FileStream>、 <xref:System.IO.MemoryStream>和 <xref:System.Net.Sockets.NetworkStream>。</span><span class="sxs-lookup"><span data-stu-id="8c924-109">The **CryptoStream** class can be initialized using any class that derives from the <xref:System.IO.Stream> class, including <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, and <xref:System.Net.Sockets.NetworkStream>.</span></span> <span data-ttu-id="8c924-110">使用這些類別，您可以在各種不同的資料流物件上執行對稱式加密。</span><span class="sxs-lookup"><span data-stu-id="8c924-110">Using these classes, you can perform symmetric encryption on a variety of stream objects.</span></span>  
  
 <span data-ttu-id="8c924-111">下列範例說明如何建立 <xref:System.Security.Cryptography.RijndaelManaged> 類別的新執行個體，它會實作 Rijndael 加密演算法，並使用它對 **CryptoStream** 類別執行加密。</span><span class="sxs-lookup"><span data-stu-id="8c924-111">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class, which implements the Rijndael encryption algorithm, and use it to perform encryption on a **CryptoStream** class.</span></span> <span data-ttu-id="8c924-112">在此範例中， **CryptoStream** 以稱為 `myStream` 的資料流物件初始化，它是任何類型的 Managed 資料流。</span><span class="sxs-lookup"><span data-stu-id="8c924-112">In this example, the **CryptoStream** is initialized with a stream object called `myStream` that can be any type of managed stream.</span></span> <span data-ttu-id="8c924-113">會傳遞金鑰和加密所用 IV 給來自 **RijndaelManaged** 類別的 **CreateEncryptor** 方法。</span><span class="sxs-lookup"><span data-stu-id="8c924-113">The **CreateEncryptor** method from the **RijndaelManaged** class is passed the key and IV that are used for encryption.</span></span> <span data-ttu-id="8c924-114">在此情況下，會使用從 `rmCrypto` 產生的預設金鑰和 IV。</span><span class="sxs-lookup"><span data-stu-id="8c924-114">In this case, the default key and IV generated from `rmCrypto` are used.</span></span> <span data-ttu-id="8c924-115">最後，會傳遞 **CryptoStreamMode.Write** ，並指定對資料流的寫入權限。</span><span class="sxs-lookup"><span data-stu-id="8c924-115">Finally, the **CryptoStreamMode.Write** is passed, specifying write access to the stream.</span></span>  
  
```vb  
Dim rmCrypto As New RijndaelManaged()  
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateEncryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Write)  
```  
  
```csharp  
RijndaelManaged rmCrypto = new RijndaelManaged();  
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 <span data-ttu-id="8c924-116">此程式碼執行之後，寫入 **CryptoStream** 物件的任何資料會使用 Rijndael 演算法進行加密。</span><span class="sxs-lookup"><span data-stu-id="8c924-116">After this code is executed, any data written to the **CryptoStream** object is encrypted using the Rijndael algorithm.</span></span>  
  
 <span data-ttu-id="8c924-117">下列範例顯示建立資料流、加密資料流、寫入資料流，然後關閉資料流的整個程序。</span><span class="sxs-lookup"><span data-stu-id="8c924-117">The following example shows the entire process of creating a stream, encrypting the stream, writing to the stream, and closing the stream.</span></span> <span data-ttu-id="8c924-118">這個範例會建立使用 **CryptoStream** 類別和 **RijndaelManaged** 類別加密的網路資料流。</span><span class="sxs-lookup"><span data-stu-id="8c924-118">This example creates a network stream that is encrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="8c924-119">訊息會使用 <xref:System.IO.StreamWriter> 類別寫入至加密的資料流。</span><span class="sxs-lookup"><span data-stu-id="8c924-119">A message is written to the encrypted stream with the <xref:System.IO.StreamWriter> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c924-120">您也可以使用此範例寫入至檔案。</span><span class="sxs-lookup"><span data-stu-id="8c924-120">You can also use this example to write to a file.</span></span> <span data-ttu-id="8c924-121">若要這樣做，請刪除 <xref:System.Net.Sockets.TcpClient> 參考，並將 <xref:System.Net.Sockets.NetworkStream> 取代為 <xref:System.IO.FileStream>。</span><span class="sxs-lookup"><span data-stu-id="8c924-121">To do that, delete the <xref:System.Net.Sockets.TcpClient> reference and replace the <xref:System.Net.Sockets.NetworkStream> with a <xref:System.IO.FileStream>.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
Imports System.Net.Sockets  
  
Module Module1  
Sub Main()  
   Try  
      'Create a TCP connection to a listening TCP process.  
      'Use "localhost" to specify the current computer or  
      'replace "localhost" with the IP address of the   
      'listening process.   
      Dim tcp As New TcpClient("localhost", 11000)  
  
      'Create a network stream from the TCP connection.   
      Dim netStream As NetworkStream = tcp.GetStream()  
  
      'Create a new instance of the RijndaelManaged class  
      'and encrypt the stream.  
      Dim rmCrypto As New RijndaelManaged()  
  
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
  
      'Create a CryptoStream, pass it the NetworkStream, and encrypt   
      'it with the Rijndael class.  
      Dim cryptStream As New CryptoStream(netStream, rmCrypto.CreateEncryptor(key, iv), CryptoStreamMode.Write)  
  
      'Create a StreamWriter for easy writing to the   
      'network stream.  
      Dim sWriter As New StreamWriter(cryptStream)  
  
      'Write to the stream.  
      sWriter.WriteLine("Hello World!")  
  
      'Inform the user that the message was written  
      'to the stream.  
      Console.WriteLine("The message was sent.")  
  
      'Close all the connections.  
      sWriter.Close()  
      cryptStream.Close()  
      netStream.Close()  
      tcp.Close()  
   Catch  
      'Inform the user that an exception was raised.  
      Console.WriteLine("The connection failed.")  
   End Try  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
using System.Net.Sockets;  
  
public class main  
{  
   public static void Main(string[] args)  
   {  
      try  
      {  
         //Create a TCP connection to a listening TCP process.  
         //Use "localhost" to specify the current computer or  
         //replace "localhost" with the IP address of the   
         //listening process.    
         TcpClient tcp = new TcpClient("localhost",11000);  
  
         //Create a network stream from the TCP connection.   
         NetworkStream netStream = tcp.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and encrypt the stream.  
         RijndaelManaged rmCrypto = new RijndaelManaged();  
  
         byte[] key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
         byte[] iv = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
  
         //Create a CryptoStream, pass it the NetworkStream, and encrypt   
         //it with the Rijndael class.  
         CryptoStream cryptStream = new CryptoStream(netStream,   
         rmCrypto.CreateEncryptor(key, iv),     
         CryptoStreamMode.Write);  
  
         //Create a StreamWriter for easy writing to the   
         //network stream.  
         StreamWriter sWriter = new StreamWriter(cryptStream);  
  
         //Write to the stream.  
         sWriter.WriteLine("Hello World!");  
  
         //Inform the user that the message was written  
         //to the stream.  
         Console.WriteLine("The message was sent.");  
  
         //Close all the connections.  
         sWriter.Close();  
         cryptStream.Close();  
         netStream.Close();  
         tcp.Close();  
      }  
      catch  
      {  
         //Inform the user that an exception was raised.  
         Console.WriteLine("The connection failed.");  
      }  
   }  
}  
```  
  
 <span data-ttu-id="8c924-122">前一個範例若要執行成功，必須有處理序在 <xref:System.Net.Sockets.TcpClient> 類別指定的 IP 位址和通訊埠號碼上接聽。</span><span class="sxs-lookup"><span data-stu-id="8c924-122">For the previous example to execute successfully, there must be a process listening on the IP address and port number specified in the <xref:System.Net.Sockets.TcpClient> class.</span></span> <span data-ttu-id="8c924-123">如果接聽的處理序存在，程式碼便會連接到接聽的處理序、使用 Rijndael 對稱演算法加密資料流，並將 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="8c924-123">If a listening process exists, the code will connect to the listening process, encrypt the stream using the Rijndael symmetric algorithm, and write "Hello World!"</span></span> <span data-ttu-id="8c924-124">寫入此資料流。</span><span class="sxs-lookup"><span data-stu-id="8c924-124">to the stream.</span></span> <span data-ttu-id="8c924-125">如果程式碼成功，它會顯示下列文字至主控台：</span><span class="sxs-lookup"><span data-stu-id="8c924-125">If the code is successful, it displays the following text to the console:</span></span>  
  
```console  
The message was sent.  
```  
  
 <span data-ttu-id="8c924-126">不過，如果找不到接聽的處理序或引發了例外狀況，程式碼會顯示下列文字至主控台：</span><span class="sxs-lookup"><span data-stu-id="8c924-126">However, if no listening process is found or an exception is raised, the code displays the following text to the console:</span></span>  
  
```console  
The connection failed.  
```  
  
## <a name="asymmetric-encryption"></a><span data-ttu-id="8c924-127">非對稱加密</span><span class="sxs-lookup"><span data-stu-id="8c924-127">Asymmetric Encryption</span></span>  
 <span data-ttu-id="8c924-128">非對稱演算法通常用來加密少量的資料，例如對稱金鑰和 IV 的加密。</span><span class="sxs-lookup"><span data-stu-id="8c924-128">Asymmetric algorithms are usually used to encrypt small amounts of data such as the encryption of a symmetric key and IV.</span></span> <span data-ttu-id="8c924-129">一般來說，個別的執行中非對稱式加密會使用另一個合作對象所產生的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="8c924-129">Typically, an individual performing asymmetric encryption uses the public key generated by another party.</span></span> <span data-ttu-id="8c924-130"><xref:System.Security.Cryptography.RSACryptoServiceProvider> 類別由 .NET Framework 針對此目的所提供。</span><span class="sxs-lookup"><span data-stu-id="8c924-130">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is provided by the .NET Framework for this purpose.</span></span>  
  
 <span data-ttu-id="8c924-131">下列範例會使用公開金鑰資訊來加密對稱金鑰和 IV。</span><span class="sxs-lookup"><span data-stu-id="8c924-131">The following example uses public key information to encrypt a symmetric key and IV.</span></span> <span data-ttu-id="8c924-132">會初始化兩個代表第三方的公開金鑰的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="8c924-132">Two byte arrays are initialized that represent the public key of a third party.</span></span> <span data-ttu-id="8c924-133"><xref:System.Security.Cryptography.RSAParameters> 物件會初始化為這些值。</span><span class="sxs-lookup"><span data-stu-id="8c924-133">An <xref:System.Security.Cryptography.RSAParameters> object is initialized to these values.</span></span> <span data-ttu-id="8c924-134">接下來， **RSAParameters** (以及它所代表的公開金鑰) 的物件會使用 **方法匯入到** RSACryptoServiceProvider <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="8c924-134">Next, the **RSAParameters** object (along with the public key it represents) is imported into an **RSACryptoServiceProvider** using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8c924-135">最後， <xref:System.Security.Cryptography.RijndaelManaged> 類別所建立的私密金鑰和 IV 會被加密。</span><span class="sxs-lookup"><span data-stu-id="8c924-135">Finally, the private key and IV created by a <xref:System.Security.Cryptography.RijndaelManaged> class are encrypted.</span></span> <span data-ttu-id="8c924-136">此範例會要求系統安裝 128 位元加密。</span><span class="sxs-lookup"><span data-stu-id="8c924-136">This example requires systems to have 128-bit encryption installed.</span></span>  
  
```vb  
Imports System  
Imports System.Security.Cryptography  
  
Module Module1  
  
    Sub Main()  
        'Initialize the byte arrays to the public key information.  
      Dim publicKey As Byte() =  {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19,202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}  
  
        Dim exponent As Byte() = {1, 0, 1}  
  
        'Create values to store encrypted symmetric keys.  
        Dim encryptedSymmetricKey() As Byte  
        Dim encryptedSymmetricIV() As Byte  
  
        'Create a new instance of the RSACryptoServiceProvider class.  
        Dim rsa As New RSACryptoServiceProvider()  
  
        'Create a new instance of the RSAParameters structure.  
        Dim rsaKeyInfo As New RSAParameters()  
  
        'Set rsaKeyInfo to the public key values.   
        rsaKeyInfo.Modulus = publicKey  
        rsaKeyInfo.Exponent = exponent  
  
        'Import key parameters into rsa.  
        rsa.ImportParameters(rsaKeyInfo)  
  
        'Create a new instance of the RijndaelManaged class.  
        Dim RM As New RijndaelManaged()  
  
        'Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(RM.Key, False)  
        encryptedSymmetricIV = rsa.Encrypt(RM.IV, False)  
    End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using System.Security.Cryptography;  
  
class Class1  
{  
   static void Main()  
   {  
      //Initialize the byte arrays to the public key information.  
      byte[] publicKey = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,  
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,  
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,  
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,  
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,  
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,  
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,  
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};  
  
      byte[] exponent = {1,0,1};  
  
      //Create values to store encrypted symmetric keys.  
      byte[] encryptedSymmetricKey;  
      byte[] encryptedSymmetricIV;  
  
      //Create a new instance of the RSACryptoServiceProvider class.  
      RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
  
      //Create a new instance of the RSAParameters structure.  
      RSAParameters rsaKeyInfo = new RSAParameters();  
  
      //Set rsaKeyInfo to the public key values.   
      rsaKeyInfo.Modulus = publicKey;  
      rsaKeyInfo.Exponent = exponent;  
  
      //Import key parameters into RSA.  
      rsa.ImportParameters(rsaKeyInfo);  
  
      //Create a new instance of the RijndaelManaged class.  
      RijndaelManaged rm = new RijndaelManaged();  
  
      //Encrypt the symmetric key and IV.  
      encryptedSymmetricKey = rsa.Encrypt(rm.Key, false);  
      encryptedSymmetricIV = rsa.Encrypt(rm.IV, false);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c924-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c924-137">See also</span></span>

- [<span data-ttu-id="8c924-138">產生加密和解密金鑰</span><span class="sxs-lookup"><span data-stu-id="8c924-138">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="8c924-139">解密資料</span><span class="sxs-lookup"><span data-stu-id="8c924-139">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)
- [<span data-ttu-id="8c924-140">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="8c924-140">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
