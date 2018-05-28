---
title: 開發 Windows 服務應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
author: ghogen
manager: douge
ms.openlocfilehash: af6e4bf7697b3139f6809295737fdd0d90b7f013
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="developing-windows-service-applications"></a><span data-ttu-id="367e3-102">開發 Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="367e3-102">Developing Windows Service Applications</span></span>
<span data-ttu-id="367e3-103">您可以使用 Microsoft Visual Studio 或 Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK，藉由建立要安裝為服務的應用程式，以輕鬆地建立服務。</span><span class="sxs-lookup"><span data-stu-id="367e3-103">Using Microsoft Visual Studio or the Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="367e3-104">這種類型的應用程式稱為 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="367e3-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="367e3-105">您可以使用架構功能，以建立服務、安裝服務，以及啟動、停止及控制服務的行為。</span><span class="sxs-lookup"><span data-stu-id="367e3-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="367e3-106">Visual Studio 2010 並未隨附適用於 C++ 的 Windows 服務範本。</span><span class="sxs-lookup"><span data-stu-id="367e3-106">The Windows service template for C++ was not included in Visual Studio 2010.</span></span> <span data-ttu-id="367e3-107">若要建立 Windows 服務，可以在 Visual C# 或 Visual Basic 的受控程式碼中建立服務，其可視需要與現有的 C++ 程式碼交互操作，或者，可以使用 [ATL 專案精靈](/cpp/atl/reference/atl-project-wizard)，在原生 C++ 中建立 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="367e3-107">To create a Windows service, you can either create a service in managed code in Visual C# or Visual Basic, which could interoperate with existing C++ code if required, or you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="367e3-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="367e3-108">In This Section</span></span>  
 [<span data-ttu-id="367e3-109">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="367e3-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 <span data-ttu-id="367e3-110">提供 Windows 服務應用程式、服務存留期，以及服務應用程式與其他常見專案類型有何不同的概觀。</span><span class="sxs-lookup"><span data-stu-id="367e3-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>  
  
 [<span data-ttu-id="367e3-111">逐步解說：在元件設計工具中建立 Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="367e3-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 <span data-ttu-id="367e3-112">提供在 Visual Basic 和 Visual C# 中建立服務的範例。</span><span class="sxs-lookup"><span data-stu-id="367e3-112">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>  
  
 [<span data-ttu-id="367e3-113">服務應用程式的程式設計架構</span><span class="sxs-lookup"><span data-stu-id="367e3-113">Service Application Programming Architecture</span></span>](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 <span data-ttu-id="367e3-114">說明服務程式設計中所使用的語言元素。</span><span class="sxs-lookup"><span data-stu-id="367e3-114">Explains the language elements used in service programming.</span></span>  
  
 [<span data-ttu-id="367e3-115">如何：建立 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="367e3-115">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 <span data-ttu-id="367e3-116">描述使用 Windows 服務專案範本來建立和設定 Windows 服務的程序。</span><span class="sxs-lookup"><span data-stu-id="367e3-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="367e3-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="367e3-117">Related Sections</span></span>  
 <xref:System.ServiceProcess.ServiceBase>  
 <span data-ttu-id="367e3-118">描述用來建立服務的 <xref:System.ServiceProcess.ServiceBase> 類別主要功能。</span><span class="sxs-lookup"><span data-stu-id="367e3-118">Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 <span data-ttu-id="367e3-119">描述 <xref:System.ServiceProcess.ServiceProcessInstaller> 類別的功能，其可與 <xref:System.ServiceProcess.ServiceInstaller> 類別搭配使用來安裝和解除安裝您的服務。</span><span class="sxs-lookup"><span data-stu-id="367e3-119">Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 <span data-ttu-id="367e3-120">描述 <xref:System.ServiceProcess.ServiceInstaller> 類別的功能，其可與 <xref:System.ServiceProcess.ServiceProcessInstaller> 類別搭配使用來安裝和解除安裝您的服務。</span><span class="sxs-lookup"><span data-stu-id="367e3-120">Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>  
  
 <span data-ttu-id="367e3-121">[NIB 根據範本建立專案](http://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2) \(機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="367e3-121">[NIB Creating Projects from Templates](http://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)</span></span>  
 <span data-ttu-id="367e3-122">描述本章所使用的專案類型，以及如何在兩者之間進行選擇。</span><span class="sxs-lookup"><span data-stu-id="367e3-122">Describes the projects types used in this chapter and how to choose between them.</span></span>
