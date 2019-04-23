---
title: 作法：指定服務的資訊安全內容
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
author: ghogen
ms.openlocfilehash: 68fd5d705cb2f38e00e90c211111ff34d23f3b10
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335806"
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="c47ac-102">作法：指定服務的資訊安全內容</span><span class="sxs-lookup"><span data-stu-id="c47ac-102">How to: Specify the Security Context for Services</span></span>
<span data-ttu-id="c47ac-103">根據預設，服務會在與登入使用者不同的安全性內容中執行。</span><span class="sxs-lookup"><span data-stu-id="c47ac-103">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="c47ac-104">服務會在稱為 `LocalSystem` 的預設系統帳戶內容中執行，授與他們與使用者不同的系統資源存取權限。</span><span class="sxs-lookup"><span data-stu-id="c47ac-104">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="c47ac-105">您可以變更此行為，以指定服務應在其中執行的不同使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="c47ac-105">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="c47ac-106">您可以藉由針對服務執行所在的處理序，操作 <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> 屬性來設定安全性內容。</span><span class="sxs-lookup"><span data-stu-id="c47ac-106">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="c47ac-107">這個屬性可讓您將服務設定為下列其中一種帳戶類型：</span><span class="sxs-lookup"><span data-stu-id="c47ac-107">This property allows you to set the service to one of four account types:</span></span>  
  
-   `User`<span data-ttu-id="c47ac-108">，其會導致系統在安裝服務時提示輸入有效的使用者名稱和密碼，並在網路上由單一使用者所指定的帳戶內容中執行；</span><span class="sxs-lookup"><span data-stu-id="c47ac-108">, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
-   `LocalService`<span data-ttu-id="c47ac-109">，其會在帳戶的內容中執行，以便在本機電腦上作為沒有權限的使用者，並提供匿名認證給任何遠端伺服器；</span><span class="sxs-lookup"><span data-stu-id="c47ac-109">, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
-   `LocalSystem`<span data-ttu-id="c47ac-110">，其會在帳戶的內容中執行，以提供更廣泛的本機權限，並提供電腦的認證給任何遠端伺服器；</span><span class="sxs-lookup"><span data-stu-id="c47ac-110">, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
-   `NetworkService`<span data-ttu-id="c47ac-111">，其會在帳戶的內容中執行，以便在本機電腦上作為沒有權限的使用者，並提供電腦的認證給任何遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="c47ac-111">, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="c47ac-112">如需詳細資訊，請參閱 <xref:System.ServiceProcess.ServiceAccount> 列舉。</span><span class="sxs-lookup"><span data-stu-id="c47ac-112">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="c47ac-113">指定服務的安全性內容</span><span class="sxs-lookup"><span data-stu-id="c47ac-113">To specify the security context for a service</span></span>  
  
1. <span data-ttu-id="c47ac-114">建立服務之後，為其加入必要的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="c47ac-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="c47ac-115">如需詳細資訊，請參閱[如何：將安裝程式新增至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。</span><span class="sxs-lookup"><span data-stu-id="c47ac-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2. <span data-ttu-id="c47ac-116">在設計工具中，存取 `ProjectInstaller` 類別，然後按一下所要使用服務的服務處理序安裝程式。</span><span class="sxs-lookup"><span data-stu-id="c47ac-116">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c47ac-117">針對每個服務應用程式，`ProjectInstaller` 類別中至少有兩個安裝元件：一個用於安裝專案中所有服務的處理序，以及一個適用於應用程式所包含每個服務的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="c47ac-117">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="c47ac-118">在此執行個體中，您想要選取 <xref:System.ServiceProcess.ServiceProcessInstaller>。</span><span class="sxs-lookup"><span data-stu-id="c47ac-118">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3. <span data-ttu-id="c47ac-119">在 [屬性] 視窗中，將 <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> 屬性設定為適當的值。</span><span class="sxs-lookup"><span data-stu-id="c47ac-119">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c47ac-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c47ac-120">See also</span></span>

- [<span data-ttu-id="c47ac-121">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="c47ac-121">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="c47ac-122">作法：將安裝程式新增至服務應用程式</span><span class="sxs-lookup"><span data-stu-id="c47ac-122">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="c47ac-123">作法：建立 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="c47ac-123">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)
