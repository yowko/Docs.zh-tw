---
title: 如何：將使用者資訊指派給群組連接
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ce550d6-8f7c-4ea7-add8-5bc27a7b51be
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 51e000019999056fd707c1fbf4fa1a9b0a8e7bc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395141"
---
# <a name="how-to-assign-user-information-to-group-connections"></a><span data-ttu-id="ac4e2-102">如何：將使用者資訊指派給群組連接</span><span class="sxs-lookup"><span data-stu-id="ac4e2-102">How to: Assign User Information to Group Connections</span></span>

  
 <span data-ttu-id="ac4e2-103">下列範例示範如何將使用者資訊指派給群組連線，並假設應用程式會在呼叫這段程式碼之前設定 *UserName*、*SecurelyStoredPassword* 和 *Domain* 變數，且 *UserName* 為唯一。</span><span class="sxs-lookup"><span data-stu-id="ac4e2-103">The following example demonstrates how to assign user information to group connections, assuming that the application sets the variables *UserName*, *SecurelyStoredPassword*, and *Domain* before this section of code is called and that *UserName* is unique.</span></span>  
  
### <a name="to-assign-user-information-to-a-group-connection"></a><span data-ttu-id="ac4e2-104">將使用者資訊指派給群組連線</span><span class="sxs-lookup"><span data-stu-id="ac4e2-104">To assign user information to a group connection</span></span>  
  
1.  <span data-ttu-id="ac4e2-105">建立連線群組名稱。</span><span class="sxs-lookup"><span data-stu-id="ac4e2-105">Create a connection group name.</span></span>  
  
    ```csharp  
    SHA1Managed Sha1 = new SHA1Managed();  
    Byte[] updHash = Sha1.ComputeHash(Encoding.UTF8.GetBytes(UserName + SecurelyStoredPassword + Domain));  
    String secureGroupName = Encoding.Default.GetString(updHash);  
    ```  
  
    ```vb  
    Dim Sha1 As New SHA1Managed()  
    Dim updHash As [Byte]() = Sha1.ComputeHash(Encoding.UTF8.GetBytes((UserName + SecurelyStoredPassword + Domain)))  
    Dim secureGroupName As [String] = Encoding.Default.GetString(updHash)  
    ```  
  
2.  <span data-ttu-id="ac4e2-106">建立特定 URL 的要求。</span><span class="sxs-lookup"><span data-stu-id="ac4e2-106">Create a request for a specific URL.</span></span> <span data-ttu-id="ac4e2-107">例如，下列程式碼會建立 URL `http://www.contoso.com.` 的要求</span><span class="sxs-lookup"><span data-stu-id="ac4e2-107">For example, the following code creates a request for the URL `http://www.contoso.com.`</span></span>  
  
    ```csharp  
    WebRequest myWebRequest=WebRequest.Create("http://www.contoso.com");  
    ```  
  
    ```vb  
    Dim myWebRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ```  
  
3.  <span data-ttu-id="ac4e2-108">設定 Web 要求的認證和連線群組名稱，並呼叫 **GetResponse** 來擷取 **WebResponse** 物件。</span><span class="sxs-lookup"><span data-stu-id="ac4e2-108">Set the credentials and Connection GroupName for the Web request, and call **GetResponse** to retrieve a **WebResponse** object.</span></span>  
  
    ```csharp  
    myWebRequest.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword, Domain);   
    myWebRequest.ConnectionGroupName = secureGroupName;  
  
    WebResponse myWebResponse=myWebRequest.GetResponse();  
    ```  
  
    ```vb  
    myWebRequest.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
    myWebRequest.ConnectionGroupName = secureGroupName  
  
    Dim myWebResponse As WebResponse = myWebRequest.GetResponse()  
    ```  
  
4.  <span data-ttu-id="ac4e2-109">使用 WebRespose 物件之後，關閉回應資料流。</span><span class="sxs-lookup"><span data-stu-id="ac4e2-109">Close the response stream after using the WebRespose object.</span></span>  
  
    ```csharp  
    MyWebResponse.Close();  
    ```  
  
    ```vb  
    MyWebResponse.Close()  
    ```  
  
 <span data-ttu-id="ac4e2-110">範例</span><span class="sxs-lookup"><span data-stu-id="ac4e2-110">Example</span></span>  
  
```csharp  
// Create a connection group name.  
SHA1Managed Sha1 = new SHA1Managed();  
Byte[] updHash = Sha1.ComputeHash(Encoding.UTF8.GetBytes(UserName + SecurelyStoredPassword + Domain));  
String secureGroupName = Encoding.Default.GetString(updHash);  
  
// Create a request for a specific URL.  
WebRequest myWebRequest=WebRequest.Create("http://www.contoso.com");  
  
myWebRequest.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword, Domain);   
myWebRequest.ConnectionGroupName = secureGroupName;  
  
WebResponse myWebResponse=myWebRequest.GetResponse();  
  
// Insert the code that uses myWebResponse.  
  
MyWebResponse.Close();  
```  
  
```vb  
' Create a secure group name.  
Dim Sha1 As New SHA1Managed()  
Dim updHash As [Byte]() = Sha1.ComputeHash(Encoding.UTF8.GetBytes((UserName + SecurelyStoredPassword + Domain)))  
Dim secureGroupName As [String] = Encoding.Default.GetString(updHash)  
  
' Create a request for a specific URL.  
Dim myWebRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
  
myWebRequest.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
myWebRequest.ConnectionGroupName = secureGroupName  
  
Dim myWebResponse As WebResponse = myWebRequest.GetResponse()  
  
' Insert the code that uses myWebResponse.  
MyWebResponse.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac4e2-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="ac4e2-111">See Also</span></span>  
 [<span data-ttu-id="ac4e2-112">管理連線</span><span class="sxs-lookup"><span data-stu-id="ac4e2-112">Managing Connections</span></span>](../../../docs/framework/network-programming/managing-connections.md)  
 [<span data-ttu-id="ac4e2-113">連線群組</span><span class="sxs-lookup"><span data-stu-id="ac4e2-113">Connection Grouping</span></span>](../../../docs/framework/network-programming/connection-grouping.md)
