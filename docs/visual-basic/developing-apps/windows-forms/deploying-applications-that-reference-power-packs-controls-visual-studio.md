---
title: "部署參考 Power Packs 控制項 (Visual Studio) 的應用程式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ad1aba4f2e725abbe560f0c71fbb543e15741200
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a><span data-ttu-id="cc1f1-102">部署參考 Power Packs 控制項 (Visual Studio) 的應用程式</span><span class="sxs-lookup"><span data-stu-id="cc1f1-102">Deploying applications that reference Power Packs controls (Visual Studio)</span></span>
<span data-ttu-id="cc1f1-103">如果您想要部署參考 Power Packs 控制項的應用程式 (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>， <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>， <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>，或<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>)，必須在目的地電腦上安裝的控制項。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> </xref:Microsoft.VisualBasic.PowerPacks.OvalShape> </xref:Microsoft.VisualBasic.PowerPacks.LineShape></span><span class="sxs-lookup"><span data-stu-id="cc1f1-103">If you want to deploy an application that references the Power Packs controls (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), the controls must be installed on the destination computer.</span></span>  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a><span data-ttu-id="cc1f1-104">安裝 Power Packs 控制項做為必要條件</span><span class="sxs-lookup"><span data-stu-id="cc1f1-104">Installing the Power Packs controls as a prerequisite</span></span>  
 <span data-ttu-id="cc1f1-105">若要順利部署應用程式，您也必須部署應用程式參考的所有元件。</span><span class="sxs-lookup"><span data-stu-id="cc1f1-105">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="cc1f1-106">安裝必要條件元件的程序稱為 *「啟動載入」*(Bootstrapping)。</span><span class="sxs-lookup"><span data-stu-id="cc1f1-106">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="cc1f1-107">當[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]安裝開發電腦上，啟動載入器套件加入至 Power Pack[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]啟動載入器目錄。</span><span class="sxs-lookup"><span data-stu-id="cc1f1-107">When [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] is installed on your development computer, a Power Packs bootstrapper package is added to the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] bootstrapper directory.</span></span> <span data-ttu-id="cc1f1-108">當您遵循的程序加入任何一項必要條件，就可以使用此套件[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]或 Windows Installer 部署。</span><span class="sxs-lookup"><span data-stu-id="cc1f1-108">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="cc1f1-109">預設會從安裝套件所在的相同位置來部署啟動載入的元件。</span><span class="sxs-lookup"><span data-stu-id="cc1f1-109">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="cc1f1-110">或者，您也可以視需要選擇從使用者可下載元件的 URL 或檔案共用位置來部署元件。</span><span class="sxs-lookup"><span data-stu-id="cc1f1-110">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc1f1-111">若要安裝啟動載入的元件，使用者可能需要該電腦的系統管理或類似的使用者權限。</span><span class="sxs-lookup"><span data-stu-id="cc1f1-111">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="cc1f1-112">如[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]應用程式，也就是說，使用者將會需要系統管理權限才能安裝應用程式，不論應用程式所指定的安全性層級。</span><span class="sxs-lookup"><span data-stu-id="cc1f1-112">For [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="cc1f1-113">安裝應用程式之後，使用者不需要系統管理權限，即可執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="cc1f1-113">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="cc1f1-114">在安裝期間，將會提示使用者安裝 Power Packs 控制項，如果沒有出現在目的地電腦上。</span><span class="sxs-lookup"><span data-stu-id="cc1f1-114">During installation, users will be prompted to install the Power Packs controls if they are not present on the destination computer.</span></span>  
  
 <span data-ttu-id="cc1f1-115">除了用來啟動，您可以使用電子軟體發佈系統，例如 Microsoft Systems Management Server，預先部署 Power Packs 控制項。</span><span class="sxs-lookup"><span data-stu-id="cc1f1-115">As an alternative to bootstrapping, you can pre-deploy the Power Packs controls by using an electronic software distribution system such as Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc1f1-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="cc1f1-116">See also</span></span>  
 <span data-ttu-id="cc1f1-117">[如何︰ 使用 ClickOnce 應用程式安裝必要條件](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5) </span><span class="sxs-lookup"><span data-stu-id="cc1f1-117">[How to: Install Prerequisites with a ClickOnce Application](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5) </span></span>  
<span data-ttu-id="cc1f1-118"> [Visual Basic Power Packs 控制項](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)</span><span class="sxs-lookup"><span data-stu-id="cc1f1-118"> [Visual Basic Power Packs Controls](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)</span></span>
