---
title: HOW TO：在金鑰容器儲存非對稱金鑰
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 42a42ee0fe5029dfe8340701595ba9dfab9a026d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680396"
---
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a><span data-ttu-id="60d43-102">HOW TO：在金鑰容器儲存非對稱金鑰</span><span class="sxs-lookup"><span data-stu-id="60d43-102">How to: Store Asymmetric Keys in a Key Container</span></span>
<span data-ttu-id="60d43-103">非對稱私密金鑰不應逐字或以純文字儲存到本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="60d43-103">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="60d43-104">如果您需要儲存私密金鑰，您應該使用金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="60d43-104">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="60d43-105">如需金鑰容器的詳細資訊，請參閱[了解電腦層級和使用者層級的 RSA 金鑰容器](https://msdn.microsoft.com/library/9a179f38-8fb7-4442-964c-fb7b9f39f5b9)。</span><span class="sxs-lookup"><span data-stu-id="60d43-105">For more information on key containers, see [Understanding Machine-Level and User-Level RSA Key Containers](https://msdn.microsoft.com/library/9a179f38-8fb7-4442-964c-fb7b9f39f5b9).</span></span>  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a><span data-ttu-id="60d43-106">建立非對稱金鑰並儲存到金鑰容器中</span><span class="sxs-lookup"><span data-stu-id="60d43-106">To create an asymmetric key and save it in a key container</span></span>  
  
1.  <span data-ttu-id="60d43-107">建立的新執行個體<xref:System.Security.Cryptography.CspParameters>類別，並傳遞您想要呼叫的金鑰容器名稱<xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType>欄位。</span><span class="sxs-lookup"><span data-stu-id="60d43-107">Create a new instance of a <xref:System.Security.Cryptography.CspParameters> class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>  
  
2.  <span data-ttu-id="60d43-108">建立衍生自類別的新執行個體<xref:System.Security.Cryptography.AsymmetricAlgorithm>類別 (通常**RSACryptoServiceProvider**或是**DSACryptoServiceProvider**)，並傳遞先前建立**一個是 CspParameters**其建構函式的物件。</span><span class="sxs-lookup"><span data-stu-id="60d43-108">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually **RSACryptoServiceProvider** or **DSACryptoServiceProvider**) and pass the previously created **CspParameters** object to its constructor.</span></span>  
  
### <a name="to-delete-the-key-from-a-key-container"></a><span data-ttu-id="60d43-109">從金鑰容器中刪除金鑰</span><span class="sxs-lookup"><span data-stu-id="60d43-109">To delete the key from a key container</span></span>  
  
1.  <span data-ttu-id="60d43-110">建立 **CspParameters** 類別的新執行個體，並將您為金鑰容器命名的名稱傳遞至 **CspParameters.KeyContainerName** 欄位。</span><span class="sxs-lookup"><span data-stu-id="60d43-110">Create a new instance of a **CspParameters** class and pass the name that you want to call the key container to the **CspParameters.KeyContainerName** field.</span></span>  
  
2.  <span data-ttu-id="60d43-111">建立衍生自 **AsymmetricAlgorithm** 類別 (通常是 **RSACryptoServiceProvider** 或 **DSACryptoServiceProvider**) 之類別的新執行個體，並將先前建立的 **CspParameters** 物件傳遞至其建構函式。</span><span class="sxs-lookup"><span data-stu-id="60d43-111">Create a new instance of a class that derives from the **AsymmetricAlgorithm** class (usually **RSACryptoServiceProvider** or **DSACryptoServiceProvider**) and pass the previously created **CspParameters** object to its constructor.</span></span>  
  
3.  <span data-ttu-id="60d43-112">將衍生自 **AsymmetricAlgorithm** 之類別的 **PersistKeyInCSP** 屬性設定為 **false** (在 Visual Basic 中為 **False**)。</span><span class="sxs-lookup"><span data-stu-id="60d43-112">Set the **PersistKeyInCSP** property of the class that derives from **AsymmetricAlgorithm** to **false** (**False** in Visual Basic).</span></span>  
  
4.  <span data-ttu-id="60d43-113">呼叫衍生自 **AsymmetricAlgorithm** 之類別的 **Clear** 方法。</span><span class="sxs-lookup"><span data-stu-id="60d43-113">Call the **Clear** method of the class that derives from **AsymmetricAlgorithm**.</span></span> <span data-ttu-id="60d43-114">這個方法會釋放該類別的所有資源，並清除金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="60d43-114">This method releases all resources of the class and clears the key container.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60d43-115">範例</span><span class="sxs-lookup"><span data-stu-id="60d43-115">Example</span></span>  
 <span data-ttu-id="60d43-116">下列範例示範如何建立非對稱金鑰、將金鑰儲存到金鑰容器中、在稍後擷取金鑰，以及從容器中刪除金鑰。</span><span class="sxs-lookup"><span data-stu-id="60d43-116">The following example demonstrates how to create an asymmetric key, save it in a key container, retrieve the key at a later time, and delete the key from the container.</span></span>  
  
 <span data-ttu-id="60d43-117">請注意，`GenKey_SaveInContainer` 方法和 `GetKeyFromContainer` 方法中的程式碼很類似。</span><span class="sxs-lookup"><span data-stu-id="60d43-117">Notice that code in the `GenKey_SaveInContainer` method and the `GetKeyFromContainer` method is similar.</span></span>  <span data-ttu-id="60d43-118">當您為 <xref:System.Security.Cryptography.CspParameters> 物件指定金鑰容器名稱，並傳遞至 <xref:System.Security.Cryptography.AsymmetricAlgorithm> 屬性或 <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> 屬性設定為 true 的 <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> 物件時，會發生下列情況。</span><span class="sxs-lookup"><span data-stu-id="60d43-118">When you specify a key container name for a <xref:System.Security.Cryptography.CspParameters> object and pass it to an <xref:System.Security.Cryptography.AsymmetricAlgorithm> object with the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> property or <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> property set to true, the following occurs.</span></span>  <span data-ttu-id="60d43-119">如果指定名稱的金鑰容器不存在，則會建立一個金鑰容器並保存金鑰。</span><span class="sxs-lookup"><span data-stu-id="60d43-119">If a key container with the specified name does not exist, then one is created and the key is persisted.</span></span>  <span data-ttu-id="60d43-120">如果指定名稱的金鑰容器存在，則會將容器中的金鑰自動載入目前的 <xref:System.Security.Cryptography.AsymmetricAlgorithm> 物件中。</span><span class="sxs-lookup"><span data-stu-id="60d43-120">If a key container with the specified name does exist, then the key in the container is automatically loaded into the current <xref:System.Security.Cryptography.AsymmetricAlgorithm> object.</span></span>  <span data-ttu-id="60d43-121">因此，`GenKey_SaveInContainer` 方法中的程式碼因為先執行，所以會保存金鑰，而 `GetKeyFromContainer` 方法中的程式碼因為後執行，所以會載入金鑰。</span><span class="sxs-lookup"><span data-stu-id="60d43-121">Therefore, the code in the `GenKey_SaveInContainer` method persists the key because it is run first, while the code in the `GetKeyFromContainer` method loads the key because it is run second.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="60d43-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60d43-122">See also</span></span>

- [<span data-ttu-id="60d43-123">產生加密和解密金鑰</span><span class="sxs-lookup"><span data-stu-id="60d43-123">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="60d43-124">加密資料</span><span class="sxs-lookup"><span data-stu-id="60d43-124">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)
- [<span data-ttu-id="60d43-125">解密資料</span><span class="sxs-lookup"><span data-stu-id="60d43-125">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)
- [<span data-ttu-id="60d43-126">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="60d43-126">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
