---
title: 解密資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET Framework], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3cb0b010a7b5f3e9baaf1c075bfbcf25cea842fe
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583481"
---
# <a name="decrypting-data"></a>解密資料
解密是加密的反向作業。 針對秘密金鑰加密，您必須同時知道金鑰和用來加密資料的 IV。 針對公開金鑰加密，您必須知道公開金鑰 (如果使用私密金鑰來加密資料) 或私密金鑰 (如果使用公開金鑰來加密資料)。  
  
## <a name="symmetric-decryption"></a>對稱解密  
 以對稱演算法加密的資料解密類似於用來以對稱演算法加密資料的程序。 <xref:System.Security.Cryptography.CryptoStream> 類別與 .NET Framework 所提供的對稱式密碼編譯類別一起用來解密從任何 Managed 資料流物件讀取的資料。  
  
 下列範例說明如何建立 <xref:System.Security.Cryptography.RijndaelManaged> 類別的新執行個體，並使用它對 <xref:System.Security.Cryptography.CryptoStream> 物件執行解密。 此範例會先建立 **RijndaelManaged** 類別的新執行個體。 接下來它會建立 **CryptoStream** 物件，並將它初始化為稱為 `myStream`的 Managed 資料流的值。 接下來，會傳遞用於加密的相同金鑰和 IV 給 **RijndaelManaged** 類別的 **CreateDecryptor** 方法，然後傳遞至 **CryptoStream** 建構函式。 最後， **CryptoStreamMode.Read** 列舉會傳遞至 **CryptoStream** 建構函式，指定資料流的讀取權限。  
  
```vb  
Dim rmCrypto As New RijndaelManaged()  
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateDecryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Read)  
```  
  
```csharp  
RijndaelManaged rmCrypto = new RijndaelManaged();  
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);  
```  
  
 下列範例顯示建立資料流、解密資料流、從資料流讀取，然後關閉資料流的整個程序。 會建立 <xref:System.Net.Sockets.TcpListener> 物件，它會在建立接聽物件的連線時初始化網路資料流。 接著會使用 **CryptoStream** 類別和 **RijndaelManaged** 類別解密網路資料流。 這個範例假設金鑰和 IV 已成功傳輸，或是事先已同意。 它不會顯示加密和傳輸這些值所需的程式碼。  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Threading  
Imports System.IO  
Imports System.Net  
Imports System.Security.Cryptography  
  
Module Module1  
    Sub Main()  
            'The key and IV must be the same values that were used  
            'to encrypt the stream.    
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
        Try  
            'Initialize a TCPListener on port 11000  
            'using the current IP address.  
            Dim tcpListen As New TcpListener(IPAddress.Any, 11000)  
  
            'Start the listener.  
            tcpListen.Start()  
  
            'Check for a connection every five seconds.  
            While Not tcpListen.Pending()  
                Console.WriteLine("Still listening. Will try in 5 seconds.")  
  
                Thread.Sleep(5000)  
            End While  
  
            'Accept the client if one is found.  
            Dim tcp As TcpClient = tcpListen.AcceptTcpClient()  
  
            'Create a network stream from the connection.  
            Dim netStream As NetworkStream = tcp.GetStream()  
  
            'Create a new instance of the RijndaelManaged class  
            'and decrypt the stream.  
            Dim rmCrypto As New RijndaelManaged()  
  
            'Create an instance of the CryptoStream class, pass it the NetworkStream, and decrypt   
            'it with the Rijndael class using the key and IV.  
            Dim cryptStream As New CryptoStream(netStream, rmCrypto.CreateDecryptor(key, iv), CryptoStreamMode.Read)  
  
            'Read the stream.  
            Dim sReader As New StreamReader(cryptStream)  
  
            'Display the message.  
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd())  
  
            'Close the streams.  
            sReader.Close()  
            netStream.Close()  
            tcp.Close()  
            'Catch any exceptions.   
        Catch  
            Console.WriteLine("The Listener Failed.")  
        End Try  
    End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Threading;  
using System.IO;  
using System.Net;  
using System.Security.Cryptography;  
  
class Class1  
{  
   static void Main(string[] args)  
   {  
      //The key and IV must be the same values that were used  
      //to encrypt the stream.    
      byte[] key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
      byte[] iv = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
      try  
      {  
         //Initialize a TCPListener on port 11000  
         //using the current IP address.  
         TcpListener tcpListen = new TcpListener(IPAdress.Any, 11000);  
  
         //Start the listener.  
         tcpListen.Start();  
  
         //Check for a connection every five seconds.  
         while(!tcpListen.Pending())  
         {  
            Console.WriteLine("Still listening. Will try in 5 seconds.");  
            Thread.Sleep(5000);  
         }  
  
         //Accept the client if one is found.  
         TcpClient tcp = tcpListen.AcceptTcpClient();  
  
         //Create a network stream from the connection.  
         NetworkStream netStream = tcp.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and decrypt the stream.  
         RijndaelManaged rmCrypto = new RijndaelManaged();  
  
         //Create a CryptoStream, pass it the NetworkStream, and decrypt   
         //it with the Rijndael class using the key and IV.  
         CryptoStream cryptStream = new CryptoStream(netStream,   
            rmCrypto.CreateDecryptor(key, iv),   
            CryptoStreamMode.Read);  
  
         //Read the stream.  
         StreamReader sReader = new StreamReader(cryptStream);  
  
         //Display the message.  
         Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd());  
  
         //Close the streams.  
         sReader.Close();  
         netStream.Close();  
         tcp.Close();  
      }  
      //Catch any exceptions.   
      catch  
      {  
         Console.WriteLine("The Listener Failed.");  
      }  
   }  
}  
```  
  
 先前的範例要能運作，必須建立接聽程式的加密連線。 連線必須使用接聽程式中使用的相同金鑰、IV 和演算法。 建立這樣的連線之後，訊息會經過解密並顯示到主控台。  
  
## <a name="asymmetric-decryption"></a>非對稱解密  
 一般而言，有一方 (A 方) 會同時產生公開和私密金鑰，並將金鑰儲存在記憶體或密碼編譯金鑰容器中。  A 方接著會將公開金鑰傳送給另一方 (B 方)。  使用公開金鑰時，B 方會加密資料並將資料傳回 A 方。在收到資料之後，A 方會使用對應的私密金鑰將資料解密。  只有在 A 方使用的私密金鑰對應於 B 方用來加密資料的公開金鑰時，解密才會成功。  
  
 如需如何儲存非對稱金鑰在安全的密碼編譯金鑰容器，以及稍後如何擷取非對稱金鑰，請參閱[How to:將對稱金鑰儲存到金鑰容器中](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)。  
  
 下列範例說明代表對稱金鑰和 IV 的兩個位元組陣列的解密。  如需如何從 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 物件擷取非對稱式公開金鑰，且使用的格式可以輕鬆地傳送給第三方的相關資訊，請參閱 [Encrypting Data](../../../docs/standard/security/encrypting-data.md)的 Managed 資料流的值。  
  
```vb  
'Create a new instance of the RSACryptoServiceProvider class.  
Dim rsa As New RSACryptoServiceProvider()  
  
' Export the public key information and send it to a third party.  
' Wait for the third party to encrypt some data and send it back.  

'Decrypt the symmetric key and IV.  
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, False)  
symmetricIV = rsa.Decrypt(encryptedSymmetricIV, False)  
```  
  
```csharp  
//Create a new instance of the RSACryptoServiceProvider class.  
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
  
// Export the public key information and send it to a third party.  
// Wait for the third party to encrypt some data and send it back.  

//Decrypt the symmetric key and IV.  
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, false);  
symmetricIV = rsa.Decrypt(encryptedSymmetricIV , false);  
```  
  
## <a name="see-also"></a>另請參閱

- [產生加密和解密金鑰](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [加密資料](../../../docs/standard/security/encrypting-data.md)
- [The signature is valid](../../../docs/standard/security/cryptographic-services.md)
