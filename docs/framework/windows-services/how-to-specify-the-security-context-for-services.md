---
title: "如何：指定服務的安全性內容"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 50a9c6ff7f02cda4475aa5390181fa5d410af161
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="b1de5-102">如何：指定服務的安全性內容</span><span class="sxs-lookup"><span data-stu-id="b1de5-102">How to: Specify the Security Context for Services</span></span>
<span data-ttu-id="b1de5-103">根據預設，服務會在不同的安全性內容以外的登入的使用者中執行。</span><span class="sxs-lookup"><span data-stu-id="b1de5-103">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="b1de5-104">預設的系統帳戶內容中執行的服務呼叫`LocalSystem`，讓他們擁有不同的存取權限與使用者的系統資源。</span><span class="sxs-lookup"><span data-stu-id="b1de5-104">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="b1de5-105">您可以變更此行為，以指定不同的使用者帳戶，您的服務應在其下執行。</span><span class="sxs-lookup"><span data-stu-id="b1de5-105">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="b1de5-106">管理設定的安全性內容<xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A>服務執行所在的處理序的屬性。</span><span class="sxs-lookup"><span data-stu-id="b1de5-106">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="b1de5-107">這個屬性可讓您將服務設定為四種帳戶類型之一：</span><span class="sxs-lookup"><span data-stu-id="b1de5-107">This property allows you to set the service to one of four account types:</span></span>  
  
-   <span data-ttu-id="b1de5-108">`User`這會使系統服務已安裝，且指定的網路; 上的單一使用者帳戶內容中執行時，有效的使用者名稱和密碼提示</span><span class="sxs-lookup"><span data-stu-id="b1de5-108">`User`, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
-   <span data-ttu-id="b1de5-109">`LocalService`其中會做為沒有權限的使用者的本機電腦上，並提供匿名認證給任何遠端伺服器的帳戶內容中執行</span><span class="sxs-lookup"><span data-stu-id="b1de5-109">`LocalService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
-   <span data-ttu-id="b1de5-110">`LocalSystem`其中會提供延伸本機的權限，並顯示電腦的認證給任何遠端伺服器; 的帳戶內容中執行</span><span class="sxs-lookup"><span data-stu-id="b1de5-110">`LocalSystem`, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
-   <span data-ttu-id="b1de5-111">`NetworkService`其中會做為沒有權限的使用者的本機電腦上，並顯示電腦的認證給任何遠端伺服器的帳戶內容中執行。</span><span class="sxs-lookup"><span data-stu-id="b1de5-111">`NetworkService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="b1de5-112">如需詳細資訊，請參閱 <xref:System.ServiceProcess.ServiceAccount> 列舉。</span><span class="sxs-lookup"><span data-stu-id="b1de5-112">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="b1de5-113">若要指定服務的安全性內容</span><span class="sxs-lookup"><span data-stu-id="b1de5-113">To specify the security context for a service</span></span>  
  
1.  <span data-ttu-id="b1de5-114">建立您的服務之後, 加入必要的安裝它。</span><span class="sxs-lookup"><span data-stu-id="b1de5-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="b1de5-115">如需詳細資訊，請參閱[如何： 加入至您的服務應用程式的安裝程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。</span><span class="sxs-lookup"><span data-stu-id="b1de5-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2.  <span data-ttu-id="b1de5-116">在設計工具中，存取`ProjectInstaller`類別，並按一下您要使用的服務的服務處理程序安裝程式。</span><span class="sxs-lookup"><span data-stu-id="b1de5-116">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b1de5-117">每一個服務應用程式中，有至少兩個安裝元件中的`ProjectInstaller`類別 — 一個用於專案中，而每個服務應用程式包含一個安裝程式會安裝所有服務的程序。</span><span class="sxs-lookup"><span data-stu-id="b1de5-117">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="b1de5-118">在本例中，您想要選取<xref:System.ServiceProcess.ServiceProcessInstaller>。</span><span class="sxs-lookup"><span data-stu-id="b1de5-118">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3.  <span data-ttu-id="b1de5-119">在**屬性**視窗中，將<xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A>適當的值。</span><span class="sxs-lookup"><span data-stu-id="b1de5-119">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1de5-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1de5-120">See Also</span></span>  
 [<span data-ttu-id="b1de5-121">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="b1de5-121">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="b1de5-122">如何： 加入 Installer 至服務應用程式</span><span class="sxs-lookup"><span data-stu-id="b1de5-122">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="b1de5-123">如何： 建立 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="b1de5-123">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)
