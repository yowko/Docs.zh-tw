---
title: 部署參考 Power Packs 控制項 (Visual Studio) 的應用程式
ms.date: 07/20/2015
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
ms.openlocfilehash: bd235bc0b4a7f9978333931ae1dce012c0950374
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2018
ms.locfileid: "39198224"
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a><span data-ttu-id="6cbb8-102">部署參考 Power Packs 控制項 (Visual Studio) 的應用程式</span><span class="sxs-lookup"><span data-stu-id="6cbb8-102">Deploying applications that reference Power Packs controls (Visual Studio)</span></span>
<span data-ttu-id="6cbb8-103">如果您想要部署參考 Power Packs 控制項的應用程式 (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>， <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>， <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>，或<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>)，控制項必須安裝在目的地電腦上。</span><span class="sxs-lookup"><span data-stu-id="6cbb8-103">If you want to deploy an application that references the Power Packs controls (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), the controls must be installed on the destination computer.</span></span>  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a><span data-ttu-id="6cbb8-104">安裝 Power Packs 控制項作為必要條件</span><span class="sxs-lookup"><span data-stu-id="6cbb8-104">Installing the Power Packs controls as a prerequisite</span></span>  
 <span data-ttu-id="6cbb8-105">若要順利部署應用程式，您也必須部署應用程式參考的所有元件。</span><span class="sxs-lookup"><span data-stu-id="6cbb8-105">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="6cbb8-106">安裝必要條件元件的程序稱為 *「啟動載入」*(Bootstrapping)。</span><span class="sxs-lookup"><span data-stu-id="6cbb8-106">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="6cbb8-107">在您的開發電腦上安裝 Visual Studio 時，Power Pack 啟動載入器套件會加入 Visual Studio 啟動載入器目錄中。</span><span class="sxs-lookup"><span data-stu-id="6cbb8-107">When Visual Studio is installed on your development computer, a Power Packs bootstrapper package is added to the Visual Studio bootstrapper directory.</span></span> <span data-ttu-id="6cbb8-108">接著，當您遵循程序加入 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] 或 Windows Installer 部署的必要條件時，就可以使用這個套件。</span><span class="sxs-lookup"><span data-stu-id="6cbb8-108">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="6cbb8-109">預設會從安裝套件所在的相同位置來部署啟動載入的元件。</span><span class="sxs-lookup"><span data-stu-id="6cbb8-109">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="6cbb8-110">或者，您也可以視需要選擇從使用者可下載元件的 URL 或檔案共用位置來部署元件。</span><span class="sxs-lookup"><span data-stu-id="6cbb8-110">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6cbb8-111">若要安裝啟動載入的元件，使用者可能需要該電腦的系統管理或類似的使用者權限。</span><span class="sxs-lookup"><span data-stu-id="6cbb8-111">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="6cbb8-112">若為 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] 應用程式，則不論應用程式所指定的安全性層級為何，使用者都需要系統管理權限才能安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="6cbb8-112">For [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="6cbb8-113">安裝應用程式之後，使用者不需要系統管理權限，即可執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="6cbb8-113">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="6cbb8-114">在安裝期間，將會提示使用者安裝 Power Packs 控制項，如果它們不會出現在目的地電腦上。</span><span class="sxs-lookup"><span data-stu-id="6cbb8-114">During installation, users will be prompted to install the Power Packs controls if they are not present on the destination computer.</span></span>  
  
 <span data-ttu-id="6cbb8-115">為啟動程序的替代方案，您可以使用電子軟體發佈系統，例如 Microsoft Systems Management Server，預先部署 Power Packs 控制項。</span><span class="sxs-lookup"><span data-stu-id="6cbb8-115">As an alternative to bootstrapping, you can pre-deploy the Power Packs controls by using an electronic software distribution system such as Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cbb8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cbb8-116">See also</span></span>  
 [<span data-ttu-id="6cbb8-117">如何：使用 ClickOnce 應用程式安裝必要條件</span><span class="sxs-lookup"><span data-stu-id="6cbb8-117">How to: Install Prerequisites with a ClickOnce Application</span></span>](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [<span data-ttu-id="6cbb8-118">Visual Basic Power Packs 控制項</span><span class="sxs-lookup"><span data-stu-id="6cbb8-118">Visual Basic Power Packs Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
