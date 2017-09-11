---
title: "如何：卸載應用程式定義域"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eefaf670202e6b4977d75fffa906f1b07053eb3e
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="4b525-102">如何：卸載應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="4b525-102">How to: Unload an Application Domain</span></span>
<span data-ttu-id="4b525-103">當您完成使用應用程式定義域時，請使用 <xref:System.AppDomain.Unload%2A?displayProperty=fullName> 方法將它卸載。</span><span class="sxs-lookup"><span data-stu-id="4b525-103">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="4b525-104">**Unload** 方法會依正常程序關閉指定的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="4b525-104">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="4b525-105">在卸載過程中，任何新的執行緒皆不得存取應用程式定義域，且系統會將所有應用程式定義域特定的資料結構釋放出來，</span><span class="sxs-lookup"><span data-stu-id="4b525-105">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="4b525-106">並將已載入應用程式定義域的組件移除，而不再可供使用。</span><span class="sxs-lookup"><span data-stu-id="4b525-106">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="4b525-107">如果應用程式定義域中的組件為定義域中性組件，則系統會將組件的資料保留在記憶體中，直到整個程序關閉為止。</span><span class="sxs-lookup"><span data-stu-id="4b525-107">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="4b525-108">目前沒有任何機制可以卸載定義域中性的組件，因此您只能關閉整個程序。</span><span class="sxs-lookup"><span data-stu-id="4b525-108">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="4b525-109">有時候，卸載應用程式定義域的要求可能無法運作，並會導致 <xref:System.CannotUnloadAppDomainException>。</span><span class="sxs-lookup"><span data-stu-id="4b525-109">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="4b525-110">下列範例會建立名為 `MyDomain` 的新應用程式定義域，再將部分資訊列印到主控台中，然後卸載應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="4b525-110">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="4b525-111">請注意，此時程式碼會嘗試將已卸載之應用程式定義域的易記名稱列印至主控台。</span><span class="sxs-lookup"><span data-stu-id="4b525-111">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="4b525-112">這個動作會產生一個例外狀況，並由程式結尾的 try/catch 陳述式進行處理。</span><span class="sxs-lookup"><span data-stu-id="4b525-112">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b525-113">範例</span><span class="sxs-lookup"><span data-stu-id="4b525-113">Example</span></span>  
 <span data-ttu-id="4b525-114">[!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)] [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)] [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]</span><span class="sxs-lookup"><span data-stu-id="4b525-114">[!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)] [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)] [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b525-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b525-115">See Also</span></span>  
 <span data-ttu-id="4b525-116">[使用應用程式定義域設計程式](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131) </span><span class="sxs-lookup"><span data-stu-id="4b525-116">[Programming with Application Domains](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131) </span></span>  
 <span data-ttu-id="4b525-117">[如何：建立應用程式定義域](../../../docs/framework/app-domains/how-to-create-an-application-domain.md) </span><span class="sxs-lookup"><span data-stu-id="4b525-117">[How to: Create an Application Domain](../../../docs/framework/app-domains/how-to-create-an-application-domain.md) </span></span>  
 [<span data-ttu-id="4b525-118">使用應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="4b525-118">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)

