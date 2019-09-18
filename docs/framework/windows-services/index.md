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
ms.openlocfilehash: 61f969c22ac06bd6ed20ccfa9124db3bb35d0692
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053547"
---
# <a name="develop-windows-service-apps"></a><span data-ttu-id="7438f-102">開發 Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="7438f-102">Develop Windows service apps</span></span>

<span data-ttu-id="7438f-103">您可以使用 Visual Studio 或 .NET Framework SDK，藉由建立要安裝為服務的應用程式，以輕鬆地建立服務。</span><span class="sxs-lookup"><span data-stu-id="7438f-103">Using Visual Studio or the .NET Framework SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="7438f-104">這種類型的應用程式稱為 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="7438f-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="7438f-105">您可以使用架構功能，以建立服務、安裝服務，以及啟動、停止及控制服務的行為。</span><span class="sxs-lookup"><span data-stu-id="7438f-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>

> [!NOTE]
> <span data-ttu-id="7438f-106">在 Visual Studio 中，您可以 Visual C# 或 Visual Basic 中的受控程式碼建立服務，必要時該程式碼可以與現有 C++ 程式碼相互操作。</span><span class="sxs-lookup"><span data-stu-id="7438f-106">In Visual Studio you can create a service in managed code in Visual C# or Visual Basic, which can interoperate with existing C++ code if required.</span></span> <span data-ttu-id="7438f-107">或者，您可以藉由使用 [ATL 專案精靈](/cpp/atl/reference/atl-project-wizard)，在原生 C++ 中建立 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="7438f-107">Or, you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7438f-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="7438f-108">In this section</span></span>

[<span data-ttu-id="7438f-109">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="7438f-109">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)

<span data-ttu-id="7438f-110">提供 Windows 服務應用程式、服務存留期，以及服務應用程式與其他常見專案類型有何不同的概觀。</span><span class="sxs-lookup"><span data-stu-id="7438f-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>

[<span data-ttu-id="7438f-111">逐步解說：在元件設計工具中建立 Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="7438f-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

<span data-ttu-id="7438f-112">提供在 Visual Basic 和 Visual C# 中建立服務的範例。</span><span class="sxs-lookup"><span data-stu-id="7438f-112">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>

[<span data-ttu-id="7438f-113">服務應用程式的程式設計架構</span><span class="sxs-lookup"><span data-stu-id="7438f-113">Service Application Programming Architecture</span></span>](service-application-programming-architecture.md)

<span data-ttu-id="7438f-114">說明服務程式設計中所使用的語言元素。</span><span class="sxs-lookup"><span data-stu-id="7438f-114">Explains the language elements used in service programming.</span></span>

[<span data-ttu-id="7438f-115">如何：建立 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="7438f-115">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)

<span data-ttu-id="7438f-116">描述使用 Windows 服務專案範本來建立和設定 Windows 服務的程序。</span><span class="sxs-lookup"><span data-stu-id="7438f-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>

## <a name="related-sections"></a><span data-ttu-id="7438f-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="7438f-117">Related sections</span></span>

<span data-ttu-id="7438f-118"><xref:System.ServiceProcess.ServiceBase> - 描述用來建立服務的 <xref:System.ServiceProcess.ServiceBase> 類別主要功能。</span><span class="sxs-lookup"><span data-stu-id="7438f-118"><xref:System.ServiceProcess.ServiceBase> - Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>

<span data-ttu-id="7438f-119"><xref:System.ServiceProcess.ServiceProcessInstaller> - 描述 <xref:System.ServiceProcess.ServiceProcessInstaller> 類別的功能，其可與 <xref:System.ServiceProcess.ServiceInstaller> 類別搭配使用來安裝和解除安裝您的服務。</span><span class="sxs-lookup"><span data-stu-id="7438f-119"><xref:System.ServiceProcess.ServiceProcessInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>

<span data-ttu-id="7438f-120"><xref:System.ServiceProcess.ServiceInstaller> - 描述 <xref:System.ServiceProcess.ServiceInstaller> 類別的功能，其可與 <xref:System.ServiceProcess.ServiceProcessInstaller> 類別搭配使用來安裝和解除安裝您的服務。</span><span class="sxs-lookup"><span data-stu-id="7438f-120"><xref:System.ServiceProcess.ServiceInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>

<span data-ttu-id="7438f-121">[從範本建立專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) - 描述本章所使用的專案類型，以及如何在兩者之間進行選擇。</span><span class="sxs-lookup"><span data-stu-id="7438f-121">[Create Projects from Templates](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) -  Describes the projects types used in this chapter and how to choose between them.</span></span>
