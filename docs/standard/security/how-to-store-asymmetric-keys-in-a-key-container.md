---
title: 如何：將對稱金鑰儲存在金鑰容器中
description: 瞭解如何在 .NET 中將非對稱金鑰儲存在金鑰容器中。 請參閱如何建立非對稱金鑰、將它儲存在金鑰容器中，以及取出和刪除金鑰。
ms.date: 05/26/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET], asymmetric keys
- storing asymmetric keys
- keys, asymmetric
- encryption keys
- keys, storing in key containers
- asymmetric keys [.NET]
- encryption [.NET], asymmetric keys
- decryption keys
ms.assetid: 0dbcbd8d-0dcf-40e9-9f0c-e3f162d35ccc
ms.openlocfilehash: 9c04d1ea4d7e7ee46d875b3fa791f3eee2059e52
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854720"
---
# <a name="store-asymmetric-keys-in-a-key-container"></a>將非對稱金鑰儲存在金鑰容器中

非對稱私密金鑰不應逐字或以純文字儲存到本機電腦上。 如果您需要儲存私密金鑰，請使用金鑰容器。 如需金鑰容器的詳細資訊，請參閱[瞭解電腦層級和使用者層級的 RSA 金鑰容器](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100))。

> [!NOTE]
> 本文中的程式碼適用于 Windows，並使用 .NET Core 2.2 和更早版本中未提供的功能。 如需詳細資訊，請參閱[dotnet/runtime # 23391](https://github.com/dotnet/runtime/issues/23391)。

## <a name="create-an-asymmetric-key-and-save-it-in-a-key-container"></a>建立非對稱金鑰，並將它儲存在金鑰容器中

1. 建立類別的新實例 <xref:System.Security.Cryptography.CspParameters> ，並將您想要呼叫金鑰容器的名稱傳遞至 <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> 欄位。

1. 建立衍生自類別的類別的新實例 <xref:System.Security.Cryptography.AsymmetricAlgorithm> (通常 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 或 <xref:System.Security.Cryptography.DSACryptoServiceProvider>) ，並將先前建立的物件傳遞 `CspParameters` 至其函式。

> [!NOTE]
> 建立和抓取非對稱金鑰是一項作業。 如果容器中尚未有索引鍵，則會在傳回之前先建立它。
>
> - <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType>
> - <xref:System.Security.Cryptography.DSA.ToXmlString%2A?displayProperty=nameWithType>

## <a name="delete-the-key-from-the-key-container"></a>從金鑰容器中刪除金鑰

1. 建立類別的新實例 `CspParameters` ，並將您想要呼叫金鑰容器的名稱傳遞至 <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> 欄位。

1. 建立衍生自類別的類別的新實例 <xref:System.Security.Cryptography.AsymmetricAlgorithm> (通常 `RSACryptoServiceProvider` 或 `DSACryptoServiceProvider`) ，並將先前建立的物件傳遞 `CspParameters` 至其函式。

1. 設定 <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> 衍生自之類別的或屬性， `AsymmetricAlgorithm` 以 `false` `False` 在 Visual Basic) 中 (。

1. 呼叫 `Clear` 衍生自之類別的方法 `AsymmetricAlgorithm` 。 這個方法會釋放該類別的所有資源，並清除金鑰容器。

## <a name="example"></a>範例

下列範例示範如何建立非對稱金鑰、將金鑰儲存到金鑰容器中、在稍後擷取金鑰，以及從容器中刪除金鑰。

請注意，`GenKey_SaveInContainer` 方法和 `GetKeyFromContainer` 方法中的程式碼很類似。 當您指定物件的金鑰容器名稱 <xref:System.Security.Cryptography.CspParameters> ，並將它傳遞給 <xref:System.Security.Cryptography.AsymmetricAlgorithm> <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> 屬性或 <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> 屬性設定為的物件時，其 `true` 行為如下所示：

- 如果指定名稱的金鑰容器不存在，則會建立一個金鑰容器並保存金鑰。
- 如果指定名稱的金鑰容器存在，則會將容器中的金鑰自動載入目前的 <xref:System.Security.Cryptography.AsymmetricAlgorithm> 物件中。

因此，方法中的 `GenKey_SaveInContainer` 程式碼會保存金鑰，因為它會先執行，而方法中的程式碼會 `GetKeyFromContainer` 載入金鑰，因為它會執行第二個。

```vb
Imports System
Imports System.Security.Cryptography

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

    Private Shared Sub GenKey_SaveInContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        ' name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container MyKeyContainerName.
        Using rsa As New RSACryptoServiceProvider(parameters)
            ' Display the key information to the console.
            Console.WriteLine($"Key added to container:  {rsa.ToXmlString(True)}")
        End Using
    End Sub

    Private Shared Sub GetKeyFromContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        '  name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container MyKeyContainerName.
        Using rsa As New RSACryptoServiceProvider(parameters)
            ' Display the key information to the console.
            Console.WriteLine($"Key retrieved from container : {rsa.ToXmlString(True)}")
        End Using
    End Sub

    Private Shared Sub DeleteKeyFromContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        '  name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container.
        ' Delete the key entry in the container.
        Dim rsa As New RSACryptoServiceProvider(parameters) With {
            .PersistKeyInCsp = False
        }

        ' Call Clear to release resources and delete the key from the container.
        rsa.Clear()

        Console.WriteLine("Key deleted.")
    End Sub
End Class
```

```csharp
using System;
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
        catch (CryptographicException e)
        {
            Console.WriteLine(e.Message);
        }
    }

    private static void GenKey_SaveInContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container MyKeyContainerName.
        using var rsa = new RSACryptoServiceProvider(parameters);

        // Display the key information to the console.
        Console.WriteLine($"Key added to container: \n  {rsa.ToXmlString(true)}");
    }

    private static void GetKeyFromContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container MyKeyContainerName.
        using var rsa = new RSACryptoServiceProvider(parameters);

        // Display the key information to the console.
        Console.WriteLine($"Key retrieved from container : \n {rsa.ToXmlString(true)}");
    }

    private static void DeleteKeyFromContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container.
        using var rsa = new RSACryptoServiceProvider(parameters)
        {
            // Delete the key entry in the container.
            PersistKeyInCsp = false
        };

        // Call Clear to release resources and delete the key from the container.
        rsa.Clear();

        Console.WriteLine("Key deleted.");
    }
}
```

輸出如下所示：

```console
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

- [密碼編譯模型](cryptography-model.md)
- [密碼編譯服務](cryptographic-services.md)
- [跨平臺密碼編譯](cross-platform-cryptography.md)
- [產生加密和解密的金鑰](generating-keys-for-encryption-and-decryption.md)
- [加密資料](encrypting-data.md)
- [解密資料](decrypting-data.md)
- [ASP.NET Core 資料保護](/aspnet/core/security/data-protection/introduction)
