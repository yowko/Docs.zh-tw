---
title: 開發 Windows 服務應用程式
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
caps.latest.revision: 18
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 4ed6a741a6f86b492929598613a0c10ae08981c5
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="developing-windows-service-applications"></a><span data-ttu-id="6a176-102">開發 Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="6a176-102">Developing Windows Service Applications</span></span>
<span data-ttu-id="6a176-103">使用 Microsoft[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]或 Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK，您可以輕鬆地建立服務所建立的應用程式，安裝為服務。</span><span class="sxs-lookup"><span data-stu-id="6a176-103">Using Microsoft [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or the Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="6a176-104">這種類型的應用程式稱為 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="6a176-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="6a176-105">透過架構功能，您可以建立服務、 加以安裝，以及啟動、 停止及控制它們的行為。</span><span class="sxs-lookup"><span data-stu-id="6a176-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="6a176-106">C + + 的 Windows 服務範本未包含在 Visual Studio 2010。</span><span class="sxs-lookup"><span data-stu-id="6a176-106">The Windows service template for C++ was not included in Visual Studio 2010.</span></span> <span data-ttu-id="6a176-107">若要建立 Windows 服務，您可以在 Visual C# 或 Visual Basic，可以與視需要現有的 c + + 程式碼交互操作，在 managed 程式碼建立服務，或您也可以使用原生 c + + 中建立 Windows 服務[ATL 專案精靈](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="6a176-107">To create a Windows service, you can either create a service in managed code in Visual C# or Visual Basic, which could interoperate with existing C++ code if required, or you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6a176-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="6a176-108">In This Section</span></span>  
 [<span data-ttu-id="6a176-109">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="6a176-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 <span data-ttu-id="6a176-110">概略說明 Windows 服務應用程式、 服務和服務應用程式有何不同於其他常見的專案類型的存留期。</span><span class="sxs-lookup"><span data-stu-id="6a176-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>  
  
 [<span data-ttu-id="6a176-111">逐步解說：在元件設計工具中建立 Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="6a176-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 <span data-ttu-id="6a176-112">提供 Visual Basic 和 Visual C# 中建立服務的範例。</span><span class="sxs-lookup"><span data-stu-id="6a176-112">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>  
  
 [<span data-ttu-id="6a176-113">服務應用程式的程式設計架構</span><span class="sxs-lookup"><span data-stu-id="6a176-113">Service Application Programming Architecture</span></span>](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 <span data-ttu-id="6a176-114">說明在服務程式設計中使用的語言項目。</span><span class="sxs-lookup"><span data-stu-id="6a176-114">Explains the language elements used in service programming.</span></span>  
  
 [<span data-ttu-id="6a176-115">如何：建立 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="6a176-115">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 <span data-ttu-id="6a176-116">說明建立和設定 Windows 服務使用 Windows 服務專案範本的程序。</span><span class="sxs-lookup"><span data-stu-id="6a176-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6a176-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="6a176-117">Related Sections</span></span>  
 <xref:System.ServiceProcess.ServiceBase>  
 <span data-ttu-id="6a176-118">描述主要功能<xref:System.ServiceProcess.ServiceBase>類別，用來建立服務。</span><span class="sxs-lookup"><span data-stu-id="6a176-118">Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 <span data-ttu-id="6a176-119">說明的功能<xref:System.ServiceProcess.ServiceProcessInstaller>類別，可搭配沿著<xref:System.ServiceProcess.ServiceInstaller>安裝和解除安裝您的服務類別。</span><span class="sxs-lookup"><span data-stu-id="6a176-119">Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 <span data-ttu-id="6a176-120">說明的功能<xref:System.ServiceProcess.ServiceInstaller>類別，可搭配沿著<xref:System.ServiceProcess.ServiceProcessInstaller>安裝和解除安裝您的服務類別。</span><span class="sxs-lookup"><span data-stu-id="6a176-120">Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>  
  
 [<span data-ttu-id="6a176-121">NIB 從範本建立專案</span><span class="sxs-lookup"><span data-stu-id="6a176-121">NIB Creating Projects from Templates</span></span>](http://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 <span data-ttu-id="6a176-122">描述專案中這一章，以及如何選擇兩者之間使用的類型。</span><span class="sxs-lookup"><span data-stu-id="6a176-122">Describes the projects types used in this chapter and how to choose between them.</span></span>
