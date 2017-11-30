---
title: "如何：將對稱金鑰儲存在金鑰容器中"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- storing asymmetric keys
- keys, asymmetric
- encryption keys
- keys, storing in key containers
- asymmetric keys [.NET Framework]
- encryption [.NET Framework], asymmetric keys
- decryption keys
ms.assetid: 0dbcbd8d-0dcf-40e9-9f0c-e3f162d35ccc
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 475139230c4b58bc6dcc307bd99eeafdc3e89e53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a>如何：將對稱金鑰儲存在金鑰容器中
非對稱私密金鑰不應逐字或以純文字儲存到本機電腦上。 如果您需要儲存私密金鑰，您應該使用金鑰容器。 如需金鑰容器的詳細資訊，請參閱[了解電腦層級和使用者層級的 RSA 金鑰容器](http://msdn.microsoft.com/library/9a179f38-8fb7-4442-964c-fb7b9f39f5b9)。  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a>建立非對稱金鑰並儲存到金鑰容器中  
  
1.  建立的新執行個體<xref:System.Security.Cryptography.CspParameters>類別，並傳遞您想要呼叫的金鑰容器名稱<xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType>欄位。  
  
2.  建立衍生自類別的新執行個體<xref:System.Security.Cryptography.AsymmetricAlgorithm>類別 (通常**RSACryptoServiceProvider**或**DSACryptoServiceProvider**) 並將先前建立**CspParameters**其建構函式的物件。  
  
### <a name="to-delete-the-key-from-a-key-container"></a>從金鑰容器中刪除金鑰  
  
1.  建立 **CspParameters** 類別的新執行個體，並將您為金鑰容器命名的名稱傳遞至 **CspParameters.KeyContainerName** 欄位。  
  
2.  建立衍生自 **AsymmetricAlgorithm** 類別 (通常是 **RSACryptoServiceProvider** 或 **DSACryptoServiceProvider**) 之類別的新執行個體，並將先前建立的 **CspParameters** 物件傳遞至其建構函式。  
  
3.  將衍生自 **AsymmetricAlgorithm** 之類別的 **PersistKeyInCSP** 屬性設定為 **false** (在 Visual Basic 中為 **False**)。  
  
4.  呼叫衍生自 **AsymmetricAlgorithm** 之類別的 **Clear** 方法。 這個方法會釋放該類別的所有資源，並清除金鑰容器。  
  
## <a name="example"></a>範例  
 下列範例示範如何建立非對稱金鑰、將金鑰儲存到金鑰容器中、在稍後擷取金鑰，以及從容器中刪除金鑰。  
  
 請注意，`GenKey_SaveInContainer` 方法和 `GetKeyFromContainer` 方法中的程式碼很類似。  當您為 <xref:System.Security.Cryptography.CspParameters> 物件指定金鑰容器名稱，並傳遞至 <xref:System.Security.Cryptography.AsymmetricAlgorithm> 屬性或 <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> 屬性設定為 true 的 <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> 物件時，會發生下列情況。  如果指定名稱的金鑰容器不存在，則會建立一個金鑰容器並保存金鑰。  如果指定名稱的金鑰容器存在，則會將容器中的金鑰自動載入目前的 <xref:System.Security.Cryptography.AsymmetricAlgorithm> 物件中。  因此，`GenKey_SaveInContainer` 方法中的程式碼因為先執行，所以會保存金鑰，而 `GetKeyFromContainer` 方法中的程式碼因為後執行，所以會載入金鑰。  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
 _  
  
Public Class StoreKey  
  
    Public Shared Sub Main()  
        Try  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
        Catch e As CryptographicException  
            Console.WriteLine(e.Message)  
        End Try  
    End Sub  
  
    Public Shared Sub GenKey_SaveInContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        ' name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key added to container:  {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub GetKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub DeleteKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Delete the key entry in the container.  
        rsa.PersistKeyInCsp = False  
  
        ' Call Clear to release resources and delete the key from the container.  
        rsa.Clear()  
  
        Console.WriteLine("Key deleted.")  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
  
public class StoreKey  
  
{  
    public static void Main()  
    {  
        try  
        {  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
        }  
        catch(CryptographicException e)  
        {  
            Console.WriteLine(e.Message);  
        }  
  
    }  
  
    public static void GenKey_SaveInContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key added to container: \n  {0}", rsa.ToXmlString(true));  
    }  
  
    public static void GetKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : \n {0}", rsa.ToXmlString(true));  
    }  
  
    public static void DeleteKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Delete the key entry in the container.  
        rsa.PersistKeyInCsp = false;  
  
        // Call Clear to release resources and delete the key from the container.  
        rsa.Clear();  
  
        Console.WriteLine("Key deleted.");  
    }  
}  
```  
  
```Output  
Key added to container:  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key retrieved from container :  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key deleted.  
Key added to container:  
<RSAKeyValue> Key Information B</RSAKeyValue>  
Key deleted.  
```  
  
## <a name="see-also"></a>另請參閱  
 [產生加密和解密金鑰](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
 [加密資料](../../../docs/standard/security/encrypting-data.md)  
 [解密資料](../../../docs/standard/security/decrypting-data.md)  
 [The signature is valid](../../../docs/standard/security/cryptographic-services.md)
