---
title: 部署參考 PrintForm 元件 (Visual Basic) 的應用程式
ms.date: 07/20/2015
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
ms.openlocfilehash: 3dd7c348c4dc36a7ff64e76a93c05ddb24837079
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584692"
---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a><span data-ttu-id="3e64f-102">部署參考 PrintForm 元件 (Visual Basic) 的應用程式</span><span class="sxs-lookup"><span data-stu-id="3e64f-102">Deploying applications that reference the PrintForm component (Visual Basic)</span></span>
<span data-ttu-id="3e64f-103">如果您想要部署參考 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件的應用程式，則該元件必須安裝在目的電腦上。</span><span class="sxs-lookup"><span data-stu-id="3e64f-103">If you want to deploy an application that references the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component, the component must be installed on the destination computer.</span></span>  
  
 <span data-ttu-id="3e64f-104">Visual Studio 中已不再包含 PowerPack 控制項，但您可以從 [下載中心](http://www.microsoft.com/en-us/download/details.aspx?id=25169)下載這些控制項。</span><span class="sxs-lookup"><span data-stu-id="3e64f-104">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
## <a name="installing-the-printform-as-a-prerequisite"></a><span data-ttu-id="3e64f-105">安裝 PrintForm 作為必要條件</span><span class="sxs-lookup"><span data-stu-id="3e64f-105">Installing the PrintForm as a prerequisite</span></span>  
 <span data-ttu-id="3e64f-106">若要順利部署應用程式，您也必須部署應用程式參考的所有元件。</span><span class="sxs-lookup"><span data-stu-id="3e64f-106">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="3e64f-107">安裝必要條件元件的程序稱為 *「啟動載入」*(Bootstrapping)。</span><span class="sxs-lookup"><span data-stu-id="3e64f-107">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="3e64f-108">當<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>開發電腦上安裝元件，Microsoft Visual Basic Power Pack 啟動載入器套件新增至 Visual Studio 啟動載入器目錄。</span><span class="sxs-lookup"><span data-stu-id="3e64f-108">When the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is installed on your development computer, a Microsoft Visual Basic Power Packs bootstrapper package is added to the Visual Studio bootstrapper directory.</span></span> <span data-ttu-id="3e64f-109">接著，當您遵循程序加入 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] 或 Windows Installer 部署的必要條件時，就可以使用這個套件。</span><span class="sxs-lookup"><span data-stu-id="3e64f-109">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="3e64f-110">預設會從安裝套件所在的相同位置來部署啟動載入的元件。</span><span class="sxs-lookup"><span data-stu-id="3e64f-110">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="3e64f-111">或者，您也可以視需要選擇從使用者可下載元件的 URL 或檔案共用位置來部署元件。</span><span class="sxs-lookup"><span data-stu-id="3e64f-111">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e64f-112">若要安裝啟動載入的元件，使用者可能需要該電腦的系統管理或類似的使用者權限。</span><span class="sxs-lookup"><span data-stu-id="3e64f-112">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="3e64f-113">若為 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] 應用程式，則不論應用程式所指定的安全性層級為何，使用者都需要系統管理權限才能安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="3e64f-113">For [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="3e64f-114">安裝應用程式之後，使用者不需要系統管理權限，即可執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="3e64f-114">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="3e64f-115">在安裝期間，如果目的電腦上沒有 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件，則會提示使用者安裝此元件。</span><span class="sxs-lookup"><span data-stu-id="3e64f-115">During installation, users will be prompted to install the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component if it is not present on the destination computer.</span></span>  
  
 <span data-ttu-id="3e64f-116">您可以使用電子軟體散發系統 (例如 Microsoft Systems Management Server) 來預先部署 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件，以取代啟動載入。</span><span class="sxs-lookup"><span data-stu-id="3e64f-116">As an alternative to bootstrapping, you can pre-deploy the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component by using an electronic software distribution system like Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e64f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e64f-117">See also</span></span>  
 [<span data-ttu-id="3e64f-118">如何：使用 ClickOnce 應用程式安裝必要條件</span><span class="sxs-lookup"><span data-stu-id="3e64f-118">How to: Install Prerequisites with a ClickOnce Application</span></span>](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [<span data-ttu-id="3e64f-119">PrintForm 元件</span><span class="sxs-lookup"><span data-stu-id="3e64f-119">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)
