---
title: 部署參考 PrintForm 元件 (Visual Basic) 的應用程式
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 15b6e21e769c90e23e66e4f87b37f74462423985
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a><span data-ttu-id="e7059-102">部署參考 PrintForm 元件 (Visual Basic) 的應用程式</span><span class="sxs-lookup"><span data-stu-id="e7059-102">Deploying applications that reference the PrintForm component (Visual Basic)</span></span>
<span data-ttu-id="e7059-103">如果您想要部署參考 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件的應用程式，則該元件必須安裝在目的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e7059-103">If you want to deploy an application that references the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component, the component must be installed on the destination computer.</span></span>  
  
 <span data-ttu-id="e7059-104">Visual Studio 中已不再包含 PowerPack 控制項，但您可以從 [下載中心](http://www.microsoft.com/en-us/download/details.aspx?id=25169)下載這些控制項。</span><span class="sxs-lookup"><span data-stu-id="e7059-104">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
## <a name="installing-the-printform-as-a-prerequisite"></a><span data-ttu-id="e7059-105">安裝 PrintForm 作為必要條件</span><span class="sxs-lookup"><span data-stu-id="e7059-105">Installing the PrintForm as a prerequisite</span></span>  
 <span data-ttu-id="e7059-106">若要順利部署應用程式，您也必須部署應用程式參考的所有元件。</span><span class="sxs-lookup"><span data-stu-id="e7059-106">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="e7059-107">安裝必要條件元件的程序稱為 *「啟動載入」*(Bootstrapping)。</span><span class="sxs-lookup"><span data-stu-id="e7059-107">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="e7059-108">將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件安裝到開發電腦時，會將 Microsoft Visual Basic Power Pack 啟動載入器套件加入 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 啟動載入器目錄中。</span><span class="sxs-lookup"><span data-stu-id="e7059-108">When the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is installed on your development computer, a Microsoft Visual Basic Power Packs bootstrapper package is added to the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] bootstrapper directory.</span></span> <span data-ttu-id="e7059-109">接著，當您遵循程序加入 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] 或 Windows Installer 部署的必要條件時，就可以使用這個套件。</span><span class="sxs-lookup"><span data-stu-id="e7059-109">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="e7059-110">預設會從安裝套件所在的相同位置來部署啟動載入的元件。</span><span class="sxs-lookup"><span data-stu-id="e7059-110">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="e7059-111">或者，您也可以視需要選擇從使用者可下載元件的 URL 或檔案共用位置來部署元件。</span><span class="sxs-lookup"><span data-stu-id="e7059-111">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7059-112">若要安裝啟動載入的元件，使用者可能需要該電腦的系統管理或類似的使用者權限。</span><span class="sxs-lookup"><span data-stu-id="e7059-112">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="e7059-113">若為 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] 應用程式，則不論應用程式所指定的安全性層級為何，使用者都需要系統管理權限才能安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="e7059-113">For [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="e7059-114">安裝應用程式之後，使用者不需要系統管理權限，即可執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="e7059-114">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="e7059-115">在安裝期間，如果目的電腦上沒有 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件，則會提示使用者安裝此元件。</span><span class="sxs-lookup"><span data-stu-id="e7059-115">During installation, users will be prompted to install the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component if it is not present on the destination computer.</span></span>  
  
 <span data-ttu-id="e7059-116">您可以使用電子軟體散發系統 (例如 Microsoft Systems Management Server) 來預先部署 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件，以取代啟動載入。</span><span class="sxs-lookup"><span data-stu-id="e7059-116">As an alternative to bootstrapping, you can pre-deploy the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component by using an electronic software distribution system like Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7059-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7059-117">See also</span></span>  
 [<span data-ttu-id="e7059-118">如何：使用 ClickOnce 應用程式安裝必要條件</span><span class="sxs-lookup"><span data-stu-id="e7059-118">How to: Install Prerequisites with a ClickOnce Application</span></span>](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [<span data-ttu-id="e7059-119">PrintForm 元件</span><span class="sxs-lookup"><span data-stu-id="e7059-119">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)
