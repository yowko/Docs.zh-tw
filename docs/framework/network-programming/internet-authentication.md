---
title: 網際網路驗證
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [.NET Framework], classes
- IAuthenticationModule interface
- ICredentialLookup interface
- CredentialCache class, about CredentialCache class
- receiving data, authentication
- AuthenticationManager class, about AuthenticationManager class
- Internet, authentication
- sending data, authentication
- network resources, authentication
- user authentication, classes for authentication
- NetworkCredential class, about NetworkCredential class
- client authentication, classes for authentication
ms.assetid: d342e87c-f672-4660-a513-41a2f2b80c4a
ms.openlocfilehash: 8b17f5a7167eb539e04a19db797bc1b0cc6c5eaa
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295454"
---
# <a name="internet-authentication"></a><span data-ttu-id="3a123-102">網際網路驗證</span><span class="sxs-lookup"><span data-stu-id="3a123-102">Internet Authentication</span></span>
<span data-ttu-id="3a123-103"><xref:System.Net> 類別支援各種不同的用戶端驗證機制，包括標準的網際網路驗證方法 (基本、摘要式、交涉式、NTLM 和 Kerberos 驗證) 以及您可以建立的自訂方法。</span><span class="sxs-lookup"><span data-stu-id="3a123-103">The <xref:System.Net> classes support a variety of client authentication mechanisms, including the standard Internet authentication methods basic, digest, negotiate, NTLM, and Kerberos authentication, as well as custom methods that you can create.</span></span>  
  
 <span data-ttu-id="3a123-104">驗證認證儲存在 <xref:System.Net.NetworkCredential> 和 <xref:System.Net.CredentialCache> 類別中，能夠實作 <xref:System.Net.ICredentials> 介面。</span><span class="sxs-lookup"><span data-stu-id="3a123-104">Authentication credentials are stored in the <xref:System.Net.NetworkCredential> and <xref:System.Net.CredentialCache> classes, which implement the <xref:System.Net.ICredentials> interface.</span></span> <span data-ttu-id="3a123-105">當這些類別的其中之一經查詢認證後，它會傳回 **NetworkCredential** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3a123-105">When one of these classes is queried for credentials, it returns an instance of the **NetworkCredential** class.</span></span> <span data-ttu-id="3a123-106">驗證程序是由 <xref:System.Net.AuthenticationManager> 類別管理，而實際的驗證程序是由實作 <xref:System.Net.IAuthenticationModule> 介面的驗證模組類別執行。</span><span class="sxs-lookup"><span data-stu-id="3a123-106">The authentication process is managed by the <xref:System.Net.AuthenticationManager> class, and the actual authentication process is performed by an authentication module class that implements the <xref:System.Net.IAuthenticationModule> interface.</span></span> <span data-ttu-id="3a123-107">您必須先向 **AuthenticationManager** 註冊自訂的驗證模組才能使用它，預設會註冊基本、摘要式、交涉式、NTLM 和 Kerberos 驗證方法模組。</span><span class="sxs-lookup"><span data-stu-id="3a123-107">You must register a custom authentication module with the **AuthenticationManager** before it can be used; modules for the basic, digest, negotiate, NTLM, and Kerberos authentication methods are registered by default.</span></span>  
  
 <span data-ttu-id="3a123-108">**NetworkCredential** 儲存了一組與 URI 所識別之單一網際網路資源建立關聯的認證，並傳回它們以回應 <xref:System.Net.NetworkCredential.GetCredential%2A> 方法的任何呼叫。</span><span class="sxs-lookup"><span data-stu-id="3a123-108">**NetworkCredential** stores a set of credentials associated with a single Internet resource identified by a URI and returns them in response to any call to the <xref:System.Net.NetworkCredential.GetCredential%2A> method.</span></span> <span data-ttu-id="3a123-109">存取有限數量網際網路資源的應用程式，或在所有情況下使用同一組認證的應用程式，通常會使用 **NetworkCredential** 類別。</span><span class="sxs-lookup"><span data-stu-id="3a123-109">The **NetworkCredential** class is typically used by applications that access a limited number of Internet resources or by applications that use the same set of credentials in all cases.</span></span>  
  
 <span data-ttu-id="3a123-110">**CredentialCache** 類別儲存各種 Web 資源認證的集合。</span><span class="sxs-lookup"><span data-stu-id="3a123-110">The **CredentialCache** class stores a collection of credentials for various Web resources.</span></span> <span data-ttu-id="3a123-111">呼叫 <xref:System.Net.CredentialCache.GetCredential%2A> 方法時，**CredentialCache** 會傳回適當的認證集，由 Web 資源 URI 和要求的驗證配置決定。</span><span class="sxs-lookup"><span data-stu-id="3a123-111">When the <xref:System.Net.CredentialCache.GetCredential%2A> method is called, **CredentialCache** returns the proper set of credentials, as determined by the URI of the Web resource and the requested authentication scheme.</span></span> <span data-ttu-id="3a123-112">使用各種網際網路資源和不同驗證配置的應用程式，得益於使用 **CredentialCache** 類別，因為它會儲存所有認證並依要求提供認證。</span><span class="sxs-lookup"><span data-stu-id="3a123-112">Applications that use a variety of Internet resources with different authentication schemes benefit from using the **CredentialCache** class, since it stores all the credentials and provides them as requested.</span></span>  
  
 <span data-ttu-id="3a123-113">當網際網路資源要求驗證時，<xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> 方法會將 <xref:System.Net.WebRequest> 以及認證要求傳送至 **AuthenticationManager**。</span><span class="sxs-lookup"><span data-stu-id="3a123-113">When an Internet resource requests authentication, the <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> method sends the <xref:System.Net.WebRequest> to the **AuthenticationManager** along with the request for credentials.</span></span> <span data-ttu-id="3a123-114">然後根據下列程序驗證要求：</span><span class="sxs-lookup"><span data-stu-id="3a123-114">The request is then authenticated according to the following process:</span></span>  
  
1. <span data-ttu-id="3a123-115">**AuthenticationManager** 會在每個已註冊的驗證模組上，依其註冊順序呼叫 <xref:System.Net.IAuthenticationModule.Authenticate%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="3a123-115">The **AuthenticationManager** calls the <xref:System.Net.IAuthenticationModule.Authenticate%2A> method on each of the registered authentication modules in the order they were registered.</span></span> <span data-ttu-id="3a123-116">**AuthenticationManager** 使用不會傳回 **null** 的第一個模組執行驗證程序。</span><span class="sxs-lookup"><span data-stu-id="3a123-116">The **AuthenticationManager** uses the first module that does not return **null** to carry out the authentication process.</span></span> <span data-ttu-id="3a123-117">程序的詳細資料隨所涉及的驗證模組類型而不同。</span><span class="sxs-lookup"><span data-stu-id="3a123-117">The details of the process vary depending on the type of authentication module involved.</span></span>  
  
2. <span data-ttu-id="3a123-118">完成驗證程序後，驗證模組會將 <xref:System.Net.Authorization> 傳回至 **WebRequest**，後者包含存取網際網路資源所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="3a123-118">When the authentication process is complete, the authentication module returns an <xref:System.Net.Authorization> to the **WebRequest** that contains the information needed to access the Internet resource.</span></span>  
  
 <span data-ttu-id="3a123-119">某些驗證配置可以驗證使用者，不需要先要求資源。</span><span class="sxs-lookup"><span data-stu-id="3a123-119">Some authentication schemes can authenticate a user without first making a request for a resource.</span></span> <span data-ttu-id="3a123-120">應用程式可以預先驗證使用者和資源，至少消除一次伺服器往返，進而節省時間。</span><span class="sxs-lookup"><span data-stu-id="3a123-120">An application can save time by preauthenticating the user with the resource, thus eliminating at least one round trip to the server.</span></span> <span data-ttu-id="3a123-121">或者，它可以在程式啟動期間執行驗證，以便稍後更能回應使用者。</span><span class="sxs-lookup"><span data-stu-id="3a123-121">Or, it can perform authentication during program startup in order to be more responsive to the user later.</span></span> <span data-ttu-id="3a123-122">可以使用預先驗證的驗證配置，將 <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> 屬性設為 **true**。</span><span class="sxs-lookup"><span data-stu-id="3a123-122">Authentication schemes that can use preauthentication set the <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> property to **true**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a123-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a123-123">See also</span></span>

- [<span data-ttu-id="3a123-124">基本和摘要式驗證</span><span class="sxs-lookup"><span data-stu-id="3a123-124">Basic and Digest Authentication</span></span>](../../../docs/framework/network-programming/basic-and-digest-authentication.md)
- [<span data-ttu-id="3a123-125">NTLM 與 Kerberos 驗證</span><span class="sxs-lookup"><span data-stu-id="3a123-125">NTLM and Kerberos Authentication</span></span>](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)
- [<span data-ttu-id="3a123-126">網路程式設計的安全性</span><span class="sxs-lookup"><span data-stu-id="3a123-126">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)
