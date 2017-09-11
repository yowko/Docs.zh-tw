---
title: "部署參考 PrintForm 元件 (Visual Basic) 的應用程式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7b625e0c58653f1ee9a2d263d7d2d29ad3b2e3c1
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a><span data-ttu-id="d39a2-102">部署參考 PrintForm 元件 (Visual Basic) 的應用程式</span><span class="sxs-lookup"><span data-stu-id="d39a2-102">Deploying applications that reference the PrintForm component (Visual Basic)</span></span>
<span data-ttu-id="d39a2-103">如果您想要部署應用程式參考<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件，必須在目的地電腦上安裝的元件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="d39a2-103">If you want to deploy an application that references the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component, the component must be installed on the destination computer.</span></span>  
  
 <span data-ttu-id="d39a2-104">Visual Studio 中已不再包含 PowerPack 控制項，但您可以從 [下載中心](http://www.microsoft.com/en-us/download/details.aspx?id=25169)下載這些控制項。</span><span class="sxs-lookup"><span data-stu-id="d39a2-104">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
## <a name="installing-the-printform-as-a-prerequisite"></a><span data-ttu-id="d39a2-105">安裝必須配合做為必要條件</span><span class="sxs-lookup"><span data-stu-id="d39a2-105">Installing the PrintForm as a prerequisite</span></span>  
 <span data-ttu-id="d39a2-106">若要順利部署應用程式，您也必須部署應用程式參考的所有元件。</span><span class="sxs-lookup"><span data-stu-id="d39a2-106">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="d39a2-107">安裝必要條件元件的程序稱為 *「啟動載入」*(Bootstrapping)。</span><span class="sxs-lookup"><span data-stu-id="d39a2-107">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="d39a2-108">當<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>開發電腦上已安裝元件，Microsoft Visual Basic Power Pack 啟動載入器套件會新增至[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]啟動載入器目錄。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="d39a2-108">When the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is installed on your development computer, a Microsoft Visual Basic Power Packs bootstrapper package is added to the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] bootstrapper directory.</span></span> <span data-ttu-id="d39a2-109">當您遵循的程序加入任何一項必要條件，就可以使用此套件[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]或 Windows Installer 部署。</span><span class="sxs-lookup"><span data-stu-id="d39a2-109">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="d39a2-110">預設會從安裝套件所在的相同位置來部署啟動載入的元件。</span><span class="sxs-lookup"><span data-stu-id="d39a2-110">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="d39a2-111">或者，您也可以視需要選擇從使用者可下載元件的 URL 或檔案共用位置來部署元件。</span><span class="sxs-lookup"><span data-stu-id="d39a2-111">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d39a2-112">若要安裝啟動載入的元件，使用者可能需要該電腦的系統管理或類似的使用者權限。</span><span class="sxs-lookup"><span data-stu-id="d39a2-112">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="d39a2-113">如[!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)]應用程式，也就是說，使用者將會需要系統管理權限才能安裝應用程式，不論應用程式所指定的安全性層級。</span><span class="sxs-lookup"><span data-stu-id="d39a2-113">For [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="d39a2-114">安裝應用程式之後，使用者不需要系統管理權限，即可執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d39a2-114">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="d39a2-115">在安裝期間，將會提示使用者安裝<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>如果不存在於目的地電腦上的元件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="d39a2-115">During installation, users will be prompted to install the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component if it is not present on the destination computer.</span></span>  
  
 <span data-ttu-id="d39a2-116">若要啟動另外，您可以預先部署<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件使用電子軟體發佈系統，例如 Microsoft Systems Management Server。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="d39a2-116">As an alternative to bootstrapping, you can pre-deploy the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component by using an electronic software distribution system like Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d39a2-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="d39a2-117">See also</span></span>  
 <span data-ttu-id="d39a2-118">[如何︰ 使用 ClickOnce 應用程式安裝必要條件](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5) </span><span class="sxs-lookup"><span data-stu-id="d39a2-118">[How to: Install Prerequisites with a ClickOnce Application](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5) </span></span>  
<span data-ttu-id="d39a2-119"> [PrintForm 元件](../../../visual-basic/developing-apps/printing/printform-component.md)</span><span class="sxs-lookup"><span data-stu-id="d39a2-119"> [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)</span></span>
