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
# <a name="store-asymmetric-keys-in-a-key-container"></a><span data-ttu-id="b4c47-104">將非對稱金鑰儲存在金鑰容器中</span><span class="sxs-lookup"><span data-stu-id="b4c47-104">Store asymmetric keys in a key container</span></span>

<span data-ttu-id="b4c47-105">非對稱私密金鑰不應逐字或以純文字儲存到本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="b4c47-105">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="b4c47-106">如果您需要儲存私密金鑰，請使用金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="b4c47-106">If you need to store a private key, use a key container.</span></span> <span data-ttu-id="b4c47-107">如需金鑰容器的詳細資訊，請參閱[瞭解電腦層級和使用者層級的 RSA 金鑰容器](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="b4c47-107">For more information on key containers, see [Understanding machine-level and user-level RSA key containers](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="b4c47-108">本文中的程式碼適用于 Windows，並使用 .NET Core 2.2 和更早版本中未提供的功能。</span><span class="sxs-lookup"><span data-stu-id="b4c47-108">The code in this article applies to Windows and uses features not available in .NET Core 2.2 and earlier versions.</span></span> <span data-ttu-id="b4c47-109">如需詳細資訊，請參閱[dotnet/runtime # 23391](https://github.com/dotnet/runtime/issues/23391)。</span><span class="sxs-lookup"><span data-stu-id="b4c47-109">For more information, see [dotnet/runtime#23391](https://github.com/dotnet/runtime/issues/23391).</span></span>

## <a name="create-an-asymmetric-key-and-save-it-in-a-key-container"></a><span data-ttu-id="b4c47-110">建立非對稱金鑰，並將它儲存在金鑰容器中</span><span class="sxs-lookup"><span data-stu-id="b4c47-110">Create an asymmetric key and save it in a key container</span></span>

1. <span data-ttu-id="b4c47-111">建立類別的新實例 <xref:System.Security.Cryptography.CspParameters> ，並將您想要呼叫金鑰容器的名稱傳遞至 <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> 欄位。</span><span class="sxs-lookup"><span data-stu-id="b4c47-111">Create a new instance of a <xref:System.Security.Cryptography.CspParameters> class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>

1. <span data-ttu-id="b4c47-112">建立衍生自類別的類別的新實例 <xref:System.Security.Cryptography.AsymmetricAlgorithm> (通常 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 或 <xref:System.Security.Cryptography.DSACryptoServiceProvider>) ，並將先前建立的物件傳遞 `CspParameters` 至其函式。</span><span class="sxs-lookup"><span data-stu-id="b4c47-112">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually <xref:System.Security.Cryptography.RSACryptoServiceProvider> or <xref:System.Security.Cryptography.DSACryptoServiceProvider>) and pass the previously created `CspParameters` object to its constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="b4c47-113">建立和抓取非對稱金鑰是一項作業。</span><span class="sxs-lookup"><span data-stu-id="b4c47-113">The creation and retrieval of an asymmetric key is one operation.</span></span> <span data-ttu-id="b4c47-114">如果容器中尚未有索引鍵，則會在傳回之前先建立它。</span><span class="sxs-lookup"><span data-stu-id="b4c47-114">If a key is not already in the container, it's created before being returned.</span></span>
>
> - <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType>
> - <xref:System.Security.Cryptography.DSA.ToXmlString%2A?displayProperty=nameWithType>

## <a name="delete-the-key-from-the-key-container"></a><span data-ttu-id="b4c47-115">從金鑰容器中刪除金鑰</span><span class="sxs-lookup"><span data-stu-id="b4c47-115">Delete the key from the key container</span></span>

1. <span data-ttu-id="b4c47-116">建立類別的新實例 `CspParameters` ，並將您想要呼叫金鑰容器的名稱傳遞至 <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> 欄位。</span><span class="sxs-lookup"><span data-stu-id="b4c47-116">Create a new instance of a `CspParameters` class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>

1. <span data-ttu-id="b4c47-117">建立衍生自類別的類別的新實例 <xref:System.Security.Cryptography.AsymmetricAlgorithm> (通常 `RSACryptoServiceProvider` 或 `DSACryptoServiceProvider`) ，並將先前建立的物件傳遞 `CspParameters` 至其函式。</span><span class="sxs-lookup"><span data-stu-id="b4c47-117">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually `RSACryptoServiceProvider` or `DSACryptoServiceProvider`) and pass the previously created `CspParameters` object to its constructor.</span></span>

1. <span data-ttu-id="b4c47-118">設定 <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> 衍生自之類別的或屬性， `AsymmetricAlgorithm` 以 `false` `False` 在 Visual Basic) 中 (。</span><span class="sxs-lookup"><span data-stu-id="b4c47-118">Set the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> or the <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> property of the class that derives from `AsymmetricAlgorithm` to `false` (`False` in Visual Basic).</span></span>

1. <span data-ttu-id="b4c47-119">呼叫 `Clear` 衍生自之類別的方法 `AsymmetricAlgorithm` 。</span><span class="sxs-lookup"><span data-stu-id="b4c47-119">Call the `Clear` method of the class that derives from `AsymmetricAlgorithm`.</span></span> <span data-ttu-id="b4c47-120">這個方法會釋放該類別的所有資源，並清除金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="b4c47-120">This method releases all resources of the class and clears the key container.</span></span>

## <a name="example"></a><span data-ttu-id="b4c47-121">範例</span><span class="sxs-lookup"><span data-stu-id="b4c47-121">Example</span></span>

<span data-ttu-id="b4c47-122">下列範例示範如何建立非對稱金鑰、將金鑰儲存到金鑰容器中、在稍後擷取金鑰，以及從容器中刪除金鑰。</span><span class="sxs-lookup"><span data-stu-id="b4c47-122">The following example demonstrates how to create an asymmetric key, save it in a key container, retrieve the key at a later time, and delete the key from the container.</span></span>

<span data-ttu-id="b4c47-123">請注意，`GenKey_SaveInContainer` 方法和 `GetKeyFromContainer` 方法中的程式碼很類似。</span><span class="sxs-lookup"><span data-stu-id="b4c47-123">Notice that code in the `GenKey_SaveInContainer` method and the `GetKeyFromContainer` method is similar.</span></span> <span data-ttu-id="b4c47-124">當您指定物件的金鑰容器名稱 <xref:System.Security.Cryptography.CspParameters> ，並將它傳遞給 <xref:System.Security.Cryptography.AsymmetricAlgorithm> <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> 屬性或 <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> 屬性設定為的物件時，其 `true` 行為如下所示：</span><span class="sxs-lookup"><span data-stu-id="b4c47-124">When you specify a key container name for a <xref:System.Security.Cryptography.CspParameters> object and pass it to an <xref:System.Security.Cryptography.AsymmetricAlgorithm> object with the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> property or <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> property set to `true`, the behavior is as follows:</span></span>

- <span data-ttu-id="b4c47-125">如果指定名稱的金鑰容器不存在，則會建立一個金鑰容器並保存金鑰。</span><span class="sxs-lookup"><span data-stu-id="b4c47-125">If a key container with the specified name does not exist, then one is created and the key is persisted.</span></span>
- <span data-ttu-id="b4c47-126">如果指定名稱的金鑰容器存在，則會將容器中的金鑰自動載入目前的 <xref:System.Security.Cryptography.AsymmetricAlgorithm> 物件中。</span><span class="sxs-lookup"><span data-stu-id="b4c47-126">If a key container with the specified name does exist, then the key in the container is automatically loaded into the current <xref:System.Security.Cryptography.AsymmetricAlgorithm> object.</span></span>

<span data-ttu-id="b4c47-127">因此，方法中的 `GenKey_SaveInContainer` 程式碼會保存金鑰，因為它會先執行，而方法中的程式碼會 `GetKeyFromContainer` 載入金鑰，因為它會執行第二個。</span><span class="sxs-lookup"><span data-stu-id="b4c47-127">Therefore, the code in the `GenKey_SaveInContainer` method persists the key because it is run first, while the code in the `GetKeyFromContainer` method loads the key because it's run second.</span></span>

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

<span data-ttu-id="b4c47-128">輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="b4c47-128">The output is as follows:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b4c47-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4c47-129">See also</span></span>

- [<span data-ttu-id="b4c47-130">密碼編譯模型</span><span class="sxs-lookup"><span data-stu-id="b4c47-130">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="b4c47-131">密碼編譯服務</span><span class="sxs-lookup"><span data-stu-id="b4c47-131">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="b4c47-132">跨平臺密碼編譯</span><span class="sxs-lookup"><span data-stu-id="b4c47-132">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="b4c47-133">產生加密和解密的金鑰</span><span class="sxs-lookup"><span data-stu-id="b4c47-133">Generating keys for encryption and decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="b4c47-134">加密資料</span><span class="sxs-lookup"><span data-stu-id="b4c47-134">Encrypting data</span></span>](encrypting-data.md)
- [<span data-ttu-id="b4c47-135">解密資料</span><span class="sxs-lookup"><span data-stu-id="b4c47-135">Decrypting data</span></span>](decrypting-data.md)
- [<span data-ttu-id="b4c47-136">ASP.NET Core 資料保護</span><span class="sxs-lookup"><span data-stu-id="b4c47-136">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
