---
title: 增益集總覽
ms.date: 03/30/2017
helpviewer_keywords:
- add-ins and XAML browser applications [WPF]
- add-ins overview [WPF]
- add-ins [WPF], performance
- add-ins [WPF], benefits
- .NET Framework add-in model [WPF]
- add-ins [WPF], user interface
- add-ins and the user interface [WPF]
- add-ins [WPF], architecture
- add-ins [WPF], limitations
ms.assetid: 00b4c776-29a8-4dba-b603-280a0cdc2ade
ms.openlocfilehash: 93904e308932ea41c736ca849ce0efb200502a7e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738937"
---
# <a name="wpf-add-ins-overview"></a><span data-ttu-id="b8043-102">WPF 增益集概觀</span><span class="sxs-lookup"><span data-stu-id="b8043-102">WPF Add-Ins Overview</span></span>

<a name="Introduction"></a><span data-ttu-id="b8043-103">.NET Framework 包含一個增益集模型，開發人員可以用來建立支援增益集擴充性的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8043-103">The .NET Framework includes an add-in model that developers can use to create applications that support add-in extensibility.</span></span> <span data-ttu-id="b8043-104">此增益集模型可讓您建立增益集，整合並擴充應用程式的功能。</span><span class="sxs-lookup"><span data-stu-id="b8043-104">This add-in model allows the creation of add-ins that integrate with and extend application functionality.</span></span> <span data-ttu-id="b8043-105">在某些情況下，應用程式也需要顯示增益集所提供的使用者介面。本主題說明 WPF 如何擴充 .NET Framework 增益集模型，以啟用這些案例、其背後的架構、優點和其限制。</span><span class="sxs-lookup"><span data-stu-id="b8043-105">In some scenarios, applications also need to display user interfaces that are provided by add-ins. This topic shows how WPF augments the .NET Framework add-in model to enable these scenarios, the architecture behind it, its benefits, and its limitations.</span></span>

<a name="Requirements"></a>

## <a name="prerequisites"></a><span data-ttu-id="b8043-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="b8043-106">Prerequisites</span></span>

<span data-ttu-id="b8043-107">必須熟悉 .NET Framework 增益集模型。</span><span class="sxs-lookup"><span data-stu-id="b8043-107">Familiarity with the .NET Framework add-in model is required.</span></span> <span data-ttu-id="b8043-108">如需詳細資訊，請參閱[增益集和擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))。</span><span class="sxs-lookup"><span data-stu-id="b8043-108">For more information, see [Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span>

<a name="AddInsOverview"></a>

## <a name="add-ins-overview"></a><span data-ttu-id="b8043-109">增益集概觀</span><span class="sxs-lookup"><span data-stu-id="b8043-109">Add-Ins Overview</span></span>

<span data-ttu-id="b8043-110">為避免新功能包含複雜的應用程式重新編譯和重新部署，應用程式會實作擴充性機制，讓開發人員 (第一方和第三方) 建立整合它們的其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8043-110">In order to avoid the complexities of application recompilation and redeployment to incorporate new functionality, applications implement extensibility mechanisms that allow developers (both first-party and third-party) to create other applications that integrate with them.</span></span> <span data-ttu-id="b8043-111">支援此擴充性類型最常見的方式是使用增益集 (也稱為「附加元件」和「外掛程式」)。</span><span class="sxs-lookup"><span data-stu-id="b8043-111">The most common way to support this type of extensibility is through the use of add-ins (also known as "add-ons" and "plug-ins").</span></span> <span data-ttu-id="b8043-112">公開增益集擴充性的真實世界應用程式範例包括︰</span><span class="sxs-lookup"><span data-stu-id="b8043-112">Examples of real-world applications that expose extensibility with add-ins include:</span></span>

- <span data-ttu-id="b8043-113">Internet Explorer 附加元件。</span><span class="sxs-lookup"><span data-stu-id="b8043-113">Internet Explorer add-ons.</span></span>

- <span data-ttu-id="b8043-114">Windows Media Player 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="b8043-114">Windows Media Player plug-ins.</span></span>

- <span data-ttu-id="b8043-115">Visual Studio 增益集。</span><span class="sxs-lookup"><span data-stu-id="b8043-115">Visual Studio add-ins.</span></span>

<span data-ttu-id="b8043-116">例如，Windows Media Player 增益集模型讓協力廠商開發人員實作以各種方式擴充 Windows Media Player 的「外掛程式」，包括建立適用於 Windows Media Player 原本不支援之媒體格式的解碼器和編碼器 (例如 DVD、MP3)、音訊效果和面板。</span><span class="sxs-lookup"><span data-stu-id="b8043-116">For example, the Windows Media Player add-in model allows third-party developers to implement "plug-ins" that extend Windows Media Player in a variety of ways, including creating decoders and encoders for media formats that are not supported natively by Windows Media Player (for example, DVD, MP3), audio effects, and skins.</span></span> <span data-ttu-id="b8043-117">每個增益集模型都是建置來公開對應用程式的獨特功能，雖然有幾個實體和行為通用所有的增益集模型。</span><span class="sxs-lookup"><span data-stu-id="b8043-117">Each add-in model is built to expose the functionality that is unique to an application, although there are several entities and behaviors that are common to all add-in models.</span></span>

<span data-ttu-id="b8043-118">一般增益集擴充性解決方案的三個主要實體是「合約」、「增益集」和「主應用程式」。</span><span class="sxs-lookup"><span data-stu-id="b8043-118">The three main entities of typical add-in extensibility solutions are *contracts*, *add-ins*, and *host applications*.</span></span> <span data-ttu-id="b8043-119">合約定義增益集與主應用程式整合的兩種方式︰</span><span class="sxs-lookup"><span data-stu-id="b8043-119">Contracts define how add-ins integrate with host applications in two ways:</span></span>

- <span data-ttu-id="b8043-120">增益集整合主應用程式所實作的功能。</span><span class="sxs-lookup"><span data-stu-id="b8043-120">Add-ins integrate with functionality that is implemented by host applications.</span></span>

- <span data-ttu-id="b8043-121">主應用程式公開要整合的增益集功能。</span><span class="sxs-lookup"><span data-stu-id="b8043-121">Host applications expose functionality for add-ins to integrate with.</span></span>

<span data-ttu-id="b8043-122">為能使用增益集，主應用程式需要在執行階段找到並載入它們。</span><span class="sxs-lookup"><span data-stu-id="b8043-122">In order for add-ins to be used, host applications need to find them and load them at run time.</span></span> <span data-ttu-id="b8043-123">因此，支援增益集的應用程式有下列額外的責任︰</span><span class="sxs-lookup"><span data-stu-id="b8043-123">Consequently, applications that support add-ins have the following additional responsibilities:</span></span>

- <span data-ttu-id="b8043-124">**探索**︰尋找遵守主應用程式所支援合約的增益集。</span><span class="sxs-lookup"><span data-stu-id="b8043-124">**Discovery**: Finding add-ins that adhere to contracts supported by host applications.</span></span>

- <span data-ttu-id="b8043-125">**啟用**︰載入、執行及建立與增益集的通訊。</span><span class="sxs-lookup"><span data-stu-id="b8043-125">**Activation**: Loading, running, and establishing communication with add-ins.</span></span>

- <span data-ttu-id="b8043-126">**隔離**︰使用應用程式定義域或處理程序來建立隔離界限，保護應用程式不受增益集的潛在安全性和執行問題影響。</span><span class="sxs-lookup"><span data-stu-id="b8043-126">**Isolation**: Using either application domains or processes to establish isolation boundaries that protect applications from potential security and execution problems with add-ins.</span></span>

- <span data-ttu-id="b8043-127">**通訊**︰透過呼叫方法及傳送資料，讓增益集及主應用程式跨越隔離界限互相通訊。</span><span class="sxs-lookup"><span data-stu-id="b8043-127">**Communication**: Allowing add-ins and host applications to communicate with each other across isolation boundaries by calling methods and passing data.</span></span>

- <span data-ttu-id="b8043-128">**存留期管理**︰以簡潔、可預測的方式載入和卸載應用程式定義域和處理程序 (請參閱[應用程式定義域](../../app-domains/application-domains.md))。</span><span class="sxs-lookup"><span data-stu-id="b8043-128">**Lifetime Management**: Loading and unloading application domains and processes in a clean, predictable manner (see [Application Domains](../../app-domains/application-domains.md)).</span></span>

- <span data-ttu-id="b8043-129">**版本控制**︰確保建立任一新版本時，主應用程式和增益集仍可通訊。</span><span class="sxs-lookup"><span data-stu-id="b8043-129">**Versioning**: Ensuring that host applications and add-ins can still communicate when new versions of either are created.</span></span>

<span data-ttu-id="b8043-130">最後，開發強固的增益集模型是重要的工作。</span><span class="sxs-lookup"><span data-stu-id="b8043-130">Ultimately, developing a robust add-in model is a non-trivial undertaking.</span></span> <span data-ttu-id="b8043-131">基於這個理由，.NET Framework 會提供基礎結構來建立增益集模型。</span><span class="sxs-lookup"><span data-stu-id="b8043-131">For this reason, the .NET Framework provides an infrastructure for building add-in models.</span></span>

> [!NOTE]
> <span data-ttu-id="b8043-132">如需增益集的詳細資訊，請參閱[增益集和擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))。</span><span class="sxs-lookup"><span data-stu-id="b8043-132">For more detailed information on add-ins, see [Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).</span></span>

<a name="NETFrameworkAddInModelOverview"></a>

## <a name="net-framework-add-in-model-overview"></a><span data-ttu-id="b8043-133">.NET Framework 增益集模型概觀</span><span class="sxs-lookup"><span data-stu-id="b8043-133">.NET Framework Add-In Model Overview</span></span>

<span data-ttu-id="b8043-134">在 <xref:System.AddIn> 命名空間中找到的 .NET Framework 增益集模型包含一組類型，其設計目的是為了簡化增益集擴充性的開發。</span><span class="sxs-lookup"><span data-stu-id="b8043-134">The .NET Framework add-in model, found in the <xref:System.AddIn> namespace, contains a set of types that are designed to simplify the development of add-in extensibility.</span></span> <span data-ttu-id="b8043-135">.NET Framework 增益集模型的基本單位是*合約*，它會定義主應用程式和增益集彼此通訊的方式。</span><span class="sxs-lookup"><span data-stu-id="b8043-135">The fundamental unit of the .NET Framework add-in model is the *contract*, which defines how a host application and an add-in communicate with each other.</span></span> <span data-ttu-id="b8043-136">合約會向使用合約主應用程式特定「檢視」的主應用程式公開。</span><span class="sxs-lookup"><span data-stu-id="b8043-136">A contract is exposed to a host application using a host-application-specific *view* of the contract.</span></span> <span data-ttu-id="b8043-137">同樣地，合約的增益集專用「檢視」也會向增益集公開。</span><span class="sxs-lookup"><span data-stu-id="b8043-137">Likewise, an add-in-specific *view* of the contract is exposed to the add-in.</span></span> <span data-ttu-id="b8043-138">「配接器」用以讓主應用程式和增益集在其各自的合約檢視間進行通訊。</span><span class="sxs-lookup"><span data-stu-id="b8043-138">An *adapter* is used to allow a host application and an add-in to communicate between their respective views of the contract.</span></span> <span data-ttu-id="b8043-139">合約、檢視和配接器稱為區段，一組相關的區段構成「管線」。</span><span class="sxs-lookup"><span data-stu-id="b8043-139">Contracts, views, and adapters are referred to as segments, and a set of related segments constitutes a *pipeline*.</span></span> <span data-ttu-id="b8043-140">管線是 .NET Framework 增益集模型支援探索、啟用、安全性隔離、執行隔離（使用應用程式域和進程）、通訊、存留期管理和版本設定的基礎。</span><span class="sxs-lookup"><span data-stu-id="b8043-140">Pipelines are the foundation upon which the .NET Framework add-in model supports discovery, activation, security isolation, execution isolation (using both application domains and processes), communication, lifetime management, and versioning.</span></span>

<span data-ttu-id="b8043-141">這項支援的要點是讓開發人員建置增益集，整合主應用程式的功能。</span><span class="sxs-lookup"><span data-stu-id="b8043-141">The sum of this support allows developers to build add-ins that integrate with the functionality of a host application.</span></span> <span data-ttu-id="b8043-142">不過，某些案例需要主應用程式顯示增益集所提供的使用者介面。由於 .NET Framework 中的每個呈現技術都有自己的模型來執行使用者介面，因此 .NET Framework 增益集模型不支援任何特定的呈現技術。</span><span class="sxs-lookup"><span data-stu-id="b8043-142">However, some scenarios require host applications to display user interfaces provided by add-ins. Because each presentation technology in the .NET Framework has its own model for implementing user interfaces, the .NET Framework add-in model does not support any particular presentation technology.</span></span> <span data-ttu-id="b8043-143">WPF 會以增益集的 UI 支援來擴充 .NET Framework 增益集模型。</span><span class="sxs-lookup"><span data-stu-id="b8043-143">Instead, WPF extends the .NET Framework add-in model with UI support for add-ins.</span></span>

<a name="WPFAddInModel"></a>

## <a name="wpf-add-ins"></a><span data-ttu-id="b8043-144">WPF 增益集</span><span class="sxs-lookup"><span data-stu-id="b8043-144">WPF Add-Ins</span></span>

<span data-ttu-id="b8043-145">WPF 與 .NET Framework 增益集模型結合，可讓您處理各種需要主應用程式從增益集顯示使用者介面的案例。特別的是，WPF 會使用下列兩種程式設計模型來解決這些案例：</span><span class="sxs-lookup"><span data-stu-id="b8043-145">WPF, in conjunction with the .NET Framework add-in model, allows you to address a wide variety of scenarios that require host applications to display user interfaces from add-ins. In particular, these scenarios are addressed by WPF with the following two programming models:</span></span>

1. <span data-ttu-id="b8043-146">**增益集傳回 UI**。</span><span class="sxs-lookup"><span data-stu-id="b8043-146">**The add-in returns a UI**.</span></span> <span data-ttu-id="b8043-147">增益集會透過方法呼叫（如合約所定義），將 UI 傳回到主應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8043-147">An add-in returns a UI to the host application via a method call, as defined by the contract.</span></span> <span data-ttu-id="b8043-148">此案例用於下列情況︰</span><span class="sxs-lookup"><span data-stu-id="b8043-148">This scenario is used in the following cases:</span></span>

    - <span data-ttu-id="b8043-149">增益集所傳回之 UI 的外觀取決於只存在於執行時間的資料或條件，例如動態產生的報表。</span><span class="sxs-lookup"><span data-stu-id="b8043-149">The appearance of a UI that is returned by an add-in is dependent on either data or conditions that exist only at run time, such as dynamically generated reports.</span></span>

    - <span data-ttu-id="b8043-150">增益集提供之服務的 UI 與可使用增益集之主應用程式的 UI 不同。</span><span class="sxs-lookup"><span data-stu-id="b8043-150">The UI for services provided by an add-in differs from the UI of the host applications that can use the add-in.</span></span>

    - <span data-ttu-id="b8043-151">此增益集主要會執行主應用程式的服務，並使用 UI 向主應用程式報告狀態。</span><span class="sxs-lookup"><span data-stu-id="b8043-151">The add-in primarily performs a service for the host application, and reports status to the host application with a UI.</span></span>

2. <span data-ttu-id="b8043-152">**增益集為 UI**。</span><span class="sxs-lookup"><span data-stu-id="b8043-152">**The add-in is a UI**.</span></span> <span data-ttu-id="b8043-153">增益集是使用者介面，如合約所定義。</span><span class="sxs-lookup"><span data-stu-id="b8043-153">An add-in is a UI, as defined by the contract.</span></span> <span data-ttu-id="b8043-154">此案例用於下列情況︰</span><span class="sxs-lookup"><span data-stu-id="b8043-154">This scenario is used in the following cases:</span></span>

    - <span data-ttu-id="b8043-155">增益集不提供顯示以外的服務，例如廣告。</span><span class="sxs-lookup"><span data-stu-id="b8043-155">An add-in doesn't provide services other than being displayed, such as an advertisement.</span></span>

    - <span data-ttu-id="b8043-156">增益集提供之服務的 UI 通用於所有可使用該增益集的主應用程式，例如計算機或色彩選擇器。</span><span class="sxs-lookup"><span data-stu-id="b8043-156">The UI for services provided by an add-in is common to all host applications that can use that add-in, such as a calculator or color picker.</span></span>

<span data-ttu-id="b8043-157">這些案例需要 UI 物件可以在主應用程式和增益集應用程式域之間傳遞。</span><span class="sxs-lookup"><span data-stu-id="b8043-157">These scenarios require that UI objects can be passed between host application and add-in application domains.</span></span> <span data-ttu-id="b8043-158">由於 .NET Framework 增益集模型依賴遠端處理來進行應用程式域之間的通訊，因此在它們之間傳遞的物件必須可以遠端執行。</span><span class="sxs-lookup"><span data-stu-id="b8043-158">Since the .NET Framework add-in model relies on remoting to communicate between application domains, the objects that are passed between them must be remotable.</span></span>

<span data-ttu-id="b8043-159">可在遠端處理的物件是執行下列一或多個工作的類別執行個體︰</span><span class="sxs-lookup"><span data-stu-id="b8043-159">A remotable object is an instance of a class that does one or more of the following:</span></span>

- <span data-ttu-id="b8043-160">衍生自 <xref:System.MarshalByRefObject> 類別。</span><span class="sxs-lookup"><span data-stu-id="b8043-160">Derives from the <xref:System.MarshalByRefObject> class.</span></span>

- <span data-ttu-id="b8043-161">實作 <xref:System.Runtime.Serialization.ISerializable> 介面。</span><span class="sxs-lookup"><span data-stu-id="b8043-161">Implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="b8043-162">已套用 <xref:System.SerializableAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="b8043-162">Has the <xref:System.SerializableAttribute> attribute applied.</span></span>

> [!NOTE]
> <span data-ttu-id="b8043-163">如需有關建立可遠端 .NET Framework 物件的詳細資訊，請參閱[讓物件可遠端](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))處理。</span><span class="sxs-lookup"><span data-stu-id="b8043-163">For more information regarding the creation of remotable .NET Framework objects, see [Making Objects Remotable](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100)).</span></span>

<span data-ttu-id="b8043-164">WPF UI 類型無法遠端處理。</span><span class="sxs-lookup"><span data-stu-id="b8043-164">The WPF UI types are not remotable.</span></span> <span data-ttu-id="b8043-165">為了解決這個問題，WPF 擴充了 .NET Framework 增益集模型，讓增益集所建立的 WPF UI 能夠從主應用程式中顯示。</span><span class="sxs-lookup"><span data-stu-id="b8043-165">To solve the problem, WPF extends the .NET Framework add-in model to enable WPF UI created by add-ins to be displayed from host applications.</span></span> <span data-ttu-id="b8043-166">WPF 提供這項支援的兩種類型： <xref:System.AddIn.Contract.INativeHandleContract> 介面和兩個由 <xref:System.AddIn.Pipeline.FrameworkElementAdapters> 類別所執行的靜態方法： <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> 和 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>。</span><span class="sxs-lookup"><span data-stu-id="b8043-166">This support is provided by WPF by two types: the <xref:System.AddIn.Contract.INativeHandleContract> interface and two static methods implemented by the <xref:System.AddIn.Pipeline.FrameworkElementAdapters> class: <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> and <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.</span></span> <span data-ttu-id="b8043-167">概括而言，這些類型和方法的使用方式如下︰</span><span class="sxs-lookup"><span data-stu-id="b8043-167">At a high level, these types and methods are used in the following manner:</span></span>

1. <span data-ttu-id="b8043-168">WPF 要求增益集所提供的使用者介面是直接或間接衍生自 <xref:System.Windows.FrameworkElement>的類別，例如圖形、控制項、使用者控制項、版面配置面板和頁面。</span><span class="sxs-lookup"><span data-stu-id="b8043-168">WPF requires that user interfaces provided by add-ins are classes that derive directly or indirectly from <xref:System.Windows.FrameworkElement>, such as shapes, controls, user controls, layout panels, and pages.</span></span>

2. <span data-ttu-id="b8043-169">當合約宣告 UI 會在增益集和主應用程式之間傳遞時，就必須將它宣告為 <xref:System.AddIn.Contract.INativeHandleContract> （而非 <xref:System.Windows.FrameworkElement>）;<xref:System.AddIn.Contract.INativeHandleContract> 是可遠端表示的增益集 UI，可以跨隔離界限傳遞。</span><span class="sxs-lookup"><span data-stu-id="b8043-169">Wherever the contract declares that a UI will be passed between the add-in and the host application, it must be declared as an <xref:System.AddIn.Contract.INativeHandleContract> (not a <xref:System.Windows.FrameworkElement>); <xref:System.AddIn.Contract.INativeHandleContract> is a remotable representation of the add-in UI that can be passed across isolation boundaries.</span></span>

3. <span data-ttu-id="b8043-170">從增益集的應用程式域傳遞之前，會藉由呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>，將 <xref:System.Windows.FrameworkElement> 封裝為 <xref:System.AddIn.Contract.INativeHandleContract>。</span><span class="sxs-lookup"><span data-stu-id="b8043-170">Before being passed from the add-in's application domain, a <xref:System.Windows.FrameworkElement> is packaged as an <xref:System.AddIn.Contract.INativeHandleContract> by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.</span></span>

4. <span data-ttu-id="b8043-171">傳遞至主應用程式的應用程式域之後，必須呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>，將 <xref:System.AddIn.Contract.INativeHandleContract> 重新封裝為 <xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="b8043-171">After being passed to the host application's application domain, the <xref:System.AddIn.Contract.INativeHandleContract> must be repackaged as a <xref:System.Windows.FrameworkElement> by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.</span></span>

<span data-ttu-id="b8043-172"><xref:System.AddIn.Contract.INativeHandleContract>、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>和 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 的使用方式，取決於特定案例。</span><span class="sxs-lookup"><span data-stu-id="b8043-172">How <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, and <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> are used depends on the specific scenario.</span></span> <span data-ttu-id="b8043-173">下列各節提供每個程式設計模型的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b8043-173">The following sections provide details for each programming model.</span></span>

<a name="ReturnUIFromAddInContract"></a>

## <a name="add-in-returns-a-user-interface"></a><span data-ttu-id="b8043-174">增益集傳回使用者介面</span><span class="sxs-lookup"><span data-stu-id="b8043-174">Add-In Returns a User Interface</span></span>

<span data-ttu-id="b8043-175">若要讓增益集將 UI 傳回給主應用程式，則需要下列各項：</span><span class="sxs-lookup"><span data-stu-id="b8043-175">For an add-in to return a UI to a host application, the following are required:</span></span>

1. <span data-ttu-id="b8043-176">必須建立主應用程式、增益集和管線，如 .NET Framework[增益集和](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))擴充性檔中所述。</span><span class="sxs-lookup"><span data-stu-id="b8043-176">The host application, add-in, and pipeline must be created, as described by the .NET Framework [Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) documentation.</span></span>

2. <span data-ttu-id="b8043-177">合約必須執行 <xref:System.AddIn.Contract.IContract>，而若要傳回 UI，合約必須宣告具有 <xref:System.AddIn.Contract.INativeHandleContract>類型之傳回值的方法。</span><span class="sxs-lookup"><span data-stu-id="b8043-177">The contract must implement <xref:System.AddIn.Contract.IContract> and, to return a UI, the contract must declare a method with a return value of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span>

3. <span data-ttu-id="b8043-178">在增益集與主應用程式之間傳遞的 UI，必須直接或間接衍生自 <xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="b8043-178">The UI that is passed between the add-in and the host application must directly or indirectly derive from <xref:System.Windows.FrameworkElement>.</span></span>

4. <span data-ttu-id="b8043-179">增益集所傳回的 UI 必須先從 <xref:System.Windows.FrameworkElement> 轉換成 <xref:System.AddIn.Contract.INativeHandleContract>，才能跨越隔離界限。</span><span class="sxs-lookup"><span data-stu-id="b8043-179">The UI that is returned by the add-in must be converted from a <xref:System.Windows.FrameworkElement> to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span>

5. <span data-ttu-id="b8043-180">在跨越隔離界限之後，必須從 <xref:System.AddIn.Contract.INativeHandleContract> 將傳回的 UI 轉換成 <xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="b8043-180">The UI that is returned must be converted from an <xref:System.AddIn.Contract.INativeHandleContract> to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span>

6. <span data-ttu-id="b8043-181">主應用程式會顯示傳回的 <xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="b8043-181">The host application displays the returned <xref:System.Windows.FrameworkElement>.</span></span>

<span data-ttu-id="b8043-182">如需示範如何執行可傳回 UI 之增益集的範例，請參閱建立可傳回[ui 的增益集](how-to-create-an-add-in-that-returns-a-ui.md)。</span><span class="sxs-lookup"><span data-stu-id="b8043-182">For an example that demonstrates how to implement an add-in that returns a UI, see [Create an Add-In That Returns a UI](how-to-create-an-add-in-that-returns-a-ui.md).</span></span>

<a name="AddInIsAUI"></a>

## <a name="add-in-is-a-user-interface"></a><span data-ttu-id="b8043-183">增益集是使用者介面</span><span class="sxs-lookup"><span data-stu-id="b8043-183">Add-In Is a User Interface</span></span>

<span data-ttu-id="b8043-184">當增益集是 UI 時，需要下列各項：</span><span class="sxs-lookup"><span data-stu-id="b8043-184">When an add-in is a UI, the following are required:</span></span>

1. <span data-ttu-id="b8043-185">必須建立主應用程式、增益集和管線，如 .NET Framework[增益集和](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))擴充性檔中所述。</span><span class="sxs-lookup"><span data-stu-id="b8043-185">The host application, add-in, and pipeline must be created, as described by the .NET Framework [Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) documentation.</span></span>

2. <span data-ttu-id="b8043-186">增益集的合約介面必須執行 <xref:System.AddIn.Contract.INativeHandleContract>。</span><span class="sxs-lookup"><span data-stu-id="b8043-186">The contract interface for the add-in must implement <xref:System.AddIn.Contract.INativeHandleContract>.</span></span>

3. <span data-ttu-id="b8043-187">傳遞至主應用程式的增益集必須直接或間接衍生自 <xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="b8043-187">The add-in that is passed to the host application must directly or indirectly derive from <xref:System.Windows.FrameworkElement>.</span></span>

4. <span data-ttu-id="b8043-188">增益集必須先從 <xref:System.Windows.FrameworkElement> 轉換成 <xref:System.AddIn.Contract.INativeHandleContract>，才能跨越隔離界限。</span><span class="sxs-lookup"><span data-stu-id="b8043-188">The add-in must be converted from a <xref:System.Windows.FrameworkElement> to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span>

5. <span data-ttu-id="b8043-189">在跨越隔離界限之後，此增益集必須從 <xref:System.AddIn.Contract.INativeHandleContract> 轉換成 <xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="b8043-189">The add-in must be converted from an <xref:System.AddIn.Contract.INativeHandleContract> to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span>

6. <span data-ttu-id="b8043-190">主應用程式會顯示傳回的 <xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="b8043-190">The host application displays the returned <xref:System.Windows.FrameworkElement>.</span></span>

<span data-ttu-id="b8043-191">如需示範如何執行屬於 UI 之增益集的範例，請參閱[建立屬於 ui 的增益集](how-to-create-an-add-in-that-is-a-ui.md)。</span><span class="sxs-lookup"><span data-stu-id="b8043-191">For an example that demonstrates how to implement an add-in that is a UI, see [Create an Add-In That Is a UI](how-to-create-an-add-in-that-is-a-ui.md).</span></span>

<a name="ReturningMultipleUIsFromAnAddIn"></a>

## <a name="returning-multiple-uis-from-an-add-in"></a><span data-ttu-id="b8043-192">從增益集傳回多個 UI</span><span class="sxs-lookup"><span data-stu-id="b8043-192">Returning Multiple UIs from an Add-In</span></span>

<span data-ttu-id="b8043-193">增益集通常會提供多個使用者介面來顯示主應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8043-193">Add-ins often provide multiple user interfaces for host applications to display.</span></span> <span data-ttu-id="b8043-194">例如，假設有一個 UI 的增益集也提供主應用程式的狀態資訊，同時也是一個 UI。</span><span class="sxs-lookup"><span data-stu-id="b8043-194">For example, consider an add-in that is a UI that also provides status information to the host application, also as a UI.</span></span> <span data-ttu-id="b8043-195">像這樣的增益集的實作方法是，使用[增益集傳回使用者介面](#ReturnUIFromAddInContract)和[增益集是使用者介面](#AddInIsAUI)模型這兩種技術的組合。</span><span class="sxs-lookup"><span data-stu-id="b8043-195">An add-in like this can be implemented by using a combination of techniques from both the [Add-In Returns a User Interface](#ReturnUIFromAddInContract) and [Add-In Is a User Interface](#AddInIsAUI) models.</span></span>

<a name="AddInsAndXBAPs"></a>

## <a name="add-ins-and-xaml-browser-applications"></a><span data-ttu-id="b8043-196">增益集和 XAML 瀏覽器應用程式</span><span class="sxs-lookup"><span data-stu-id="b8043-196">Add-Ins and XAML Browser Applications</span></span>

<span data-ttu-id="b8043-197">在到目前為止的範例中，主應用程式一直是已安裝的獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8043-197">In the examples so far, the host application has been an installed standalone application.</span></span> <span data-ttu-id="b8043-198">但是，XAML 瀏覽器應用程式（Xbap）也可以裝載增益集，但具有下列額外的組建和執行需求：</span><span class="sxs-lookup"><span data-stu-id="b8043-198">But XAML browser applications (XBAPs) can also host add-ins, albeit with the following additional build and implementation requirements:</span></span>

- <span data-ttu-id="b8043-199">XBAP 應用程式資訊清單必須特別設定，才能將管線（資料夾和元件）和增益集元件下載至用戶端電腦上的 ClickOnce 應用程式快取（在與 XBAP 相同的資料夾中）。</span><span class="sxs-lookup"><span data-stu-id="b8043-199">The XBAP application manifest must be configured specially to download the pipeline (folders and assemblies) and add-in assembly to the ClickOnce application cache on the client machine, in the same folder as the XBAP.</span></span>

- <span data-ttu-id="b8043-200">用來探索及載入增益集的 XBAP 程式碼必須使用 XBAP 的 ClickOnce 應用程式快取，做為管線和增益集的位置。</span><span class="sxs-lookup"><span data-stu-id="b8043-200">The XBAP code to discover and load add-ins must use the ClickOnce application cache for the XBAP as the pipeline and add-in location.</span></span>

- <span data-ttu-id="b8043-201">如果增益集參考位於來源網站上的鬆散檔案，XBAP 就必須將增益集載入到特殊的安全性內容中。以 Xbap 裝載時，增益集只能參考位於主應用程式的來源網站上的鬆散檔案。</span><span class="sxs-lookup"><span data-stu-id="b8043-201">The XBAP must load the add-in into a special security context if the add-in references loose files that are located at the site of origin; when hosted by XBAPs, add-ins can only reference loose files that are located at the host application's site of origin.</span></span>

<span data-ttu-id="b8043-202">下列各小節將詳細說明這些工作。</span><span class="sxs-lookup"><span data-stu-id="b8043-202">These tasks are described in detail in the following subsections.</span></span>

### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a><span data-ttu-id="b8043-203">設定 ClickOnce 部署的管線和增益集</span><span class="sxs-lookup"><span data-stu-id="b8043-203">Configuring the Pipeline and Add-In for ClickOnce Deployment</span></span>

<span data-ttu-id="b8043-204">Xbap 會下載至 ClickOnce 部署快取中的安全資料夾並從中執行。</span><span class="sxs-lookup"><span data-stu-id="b8043-204">XBAPs are downloaded to and run from a safe folder in the ClickOnce deployment cache.</span></span> <span data-ttu-id="b8043-205">為了讓 XBAP 裝載增益集，管線和增益集元件也必須下載至 safe 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b8043-205">In order for an XBAP to host an add-in, the pipeline and add-in assembly must also be downloaded to the safe folder.</span></span> <span data-ttu-id="b8043-206">為達到此目的，您需要設定應用程式資訊清單包含管線和增益集組件以供下載。</span><span class="sxs-lookup"><span data-stu-id="b8043-206">To achieve this, you need to configure the application manifest to include both the pipeline and add-in assembly for download.</span></span> <span data-ttu-id="b8043-207">雖然管線和增益集元件必須位於主機 XBAP 專案的根資料夾中，才能讓 Visual Studio 偵測管線元件，但這最容易在 Visual Studio 中完成。</span><span class="sxs-lookup"><span data-stu-id="b8043-207">This is most easily done in Visual Studio, although the pipeline and add-in assembly needs to be in the host XBAP project's root folder in order for Visual Studio to detect the pipeline assemblies.</span></span>

<span data-ttu-id="b8043-208">因此，第一個步驟是設定每個管線元件和增益集元件專案的組建輸出，以將管線和增益集元件建立至 XBAP 專案的根目錄。</span><span class="sxs-lookup"><span data-stu-id="b8043-208">Consequently, the first step is to build the pipeline and add-in assembly to the XBAP project's root by setting the build output of each pipeline assembly and add-in assembly projects.</span></span> <span data-ttu-id="b8043-209">下表顯示管線元件專案和增益集元件專案的組建輸出路徑，其位於與主機 XBAP 專案相同的方案和根資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b8043-209">The following table shows the build output paths for pipeline assembly projects and add-in assembly project that are in the same solution and root folder as the host XBAP project.</span></span>

<span data-ttu-id="b8043-210">表 1：XBAP 裝載之管線組件的組建輸出路徑</span><span class="sxs-lookup"><span data-stu-id="b8043-210">Table 1: Build Output Paths for the Pipeline Assemblies That Are Hosted by an XBAP</span></span>

|<span data-ttu-id="b8043-211">管線組件專案</span><span class="sxs-lookup"><span data-stu-id="b8043-211">Pipeline assembly project</span></span>|<span data-ttu-id="b8043-212">建置輸出路徑</span><span class="sxs-lookup"><span data-stu-id="b8043-212">Build output path</span></span>|
|-------------------------------|-----------------------|
|<span data-ttu-id="b8043-213">合約</span><span class="sxs-lookup"><span data-stu-id="b8043-213">Contract</span></span>|`..\HostXBAP\Contracts\`|
|<span data-ttu-id="b8043-214">增益集檢視</span><span class="sxs-lookup"><span data-stu-id="b8043-214">Add-In View</span></span>|`..\HostXBAP\AddInViews\`|
|<span data-ttu-id="b8043-215">增益集端配接器</span><span class="sxs-lookup"><span data-stu-id="b8043-215">Add-In-Side Adapter</span></span>|`..\HostXBAP\AddInSideAdapters\`|
|<span data-ttu-id="b8043-216">主控件端配接器</span><span class="sxs-lookup"><span data-stu-id="b8043-216">Host-Side Adapter</span></span>|`..\HostXBAP\HostSideAdapters\`|
|<span data-ttu-id="b8043-217">增益集</span><span class="sxs-lookup"><span data-stu-id="b8043-217">Add-In</span></span>|`..\HostXBAP\AddIns\WPFAddIn1`|

<span data-ttu-id="b8043-218">下一個步驟是執行下列動作，將管線元件和增益集元件指定為 Visual Studio 中的 Xbap 內容檔案：</span><span class="sxs-lookup"><span data-stu-id="b8043-218">The next step is to specify the pipeline assemblies and add-in assembly as the XBAPs content files in Visual Studio by doing the following:</span></span>

1. <span data-ttu-id="b8043-219">以滑鼠右鍵按一下方案總管中每個管線資料夾，然後選擇 [加入至專案]，在專案中包含管線和增益集組件。</span><span class="sxs-lookup"><span data-stu-id="b8043-219">Including the pipeline and add-in assembly in the project by right-clicking each pipeline folder in Solution Explorer and choosing **Include In Project**.</span></span>

2. <span data-ttu-id="b8043-220">從 [屬性] 視窗將每個管線組件和增益集組件的 [建置動作] 設定為 [內容]。</span><span class="sxs-lookup"><span data-stu-id="b8043-220">Setting the **Build Action** of each pipeline assembly and add-in assembly to **Content** from the **Properties** window.</span></span>

<span data-ttu-id="b8043-221">最後一個步驟，是設定應用程式資訊清單包含管線組件檔和增益集組件檔以供下載。</span><span class="sxs-lookup"><span data-stu-id="b8043-221">The final step is to configure the application manifest to include the pipeline assembly files and add-in assembly file for download.</span></span> <span data-ttu-id="b8043-222">檔案應該位於 XBAP 應用程式所佔用之 ClickOnce 快取資料夾根目錄的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b8043-222">The files should be located in folders at the root of the folder in the ClickOnce cache that the XBAP application occupies.</span></span> <span data-ttu-id="b8043-223">您可以藉由執行下列動作，在 Visual Studio 中達到設定：</span><span class="sxs-lookup"><span data-stu-id="b8043-223">The configuration can be achieved in Visual Studio by doing the following:</span></span>

1. <span data-ttu-id="b8043-224">以滑鼠右鍵按一下 XBAP 專案，依序按一下 [**屬性**]、[**發佈**]，然後按一下 [**應用程式檔**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b8043-224">Right-click the XBAP project, click **Properties**, click **Publish**, and then click the **Application Files** button.</span></span>

2. <span data-ttu-id="b8043-225">在 [應用程式檔案] 對話方塊中，將每個管線和增益集 DLL 的 [發行狀態] 設成 [Include (Auto)] (包含 (自動))，並將每個管線和增益集 DLL 的 [下載群組] 設成 [(必要項)]。</span><span class="sxs-lookup"><span data-stu-id="b8043-225">In the **Application Files** dialog, set the **Publish Status** of each pipeline and add-in DLL to **Include (Auto)**, and set the **Download Group** for each pipeline and add-in DLL to **(Required)**.</span></span>

### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a><span data-ttu-id="b8043-226">使用來自應用程式基底的管線和增益集</span><span class="sxs-lookup"><span data-stu-id="b8043-226">Using the Pipeline and Add-In from the Application Base</span></span>

<span data-ttu-id="b8043-227">當管線和增益集設定進行 ClickOnce 部署時，會將它們下載到與 XBAP 相同的 ClickOnce 快取資料夾。</span><span class="sxs-lookup"><span data-stu-id="b8043-227">When the pipeline and add-in are configured for ClickOnce deployment, they are downloaded to the same ClickOnce cache folder as the XBAP.</span></span> <span data-ttu-id="b8043-228">若要從 XBAP 使用管線和增益集，XBAP 程式碼必須從應用程式基底取得它們。</span><span class="sxs-lookup"><span data-stu-id="b8043-228">To use the pipeline and add-in from the XBAP, the XBAP code must get them from the application base.</span></span> <span data-ttu-id="b8043-229">使用管線和增益集之 .NET Framework 增益集模型的各種類型和成員，會針對此案例提供特殊支援。</span><span class="sxs-lookup"><span data-stu-id="b8043-229">The various types and members of the .NET Framework add-in model for using pipelines and add-ins provide special support for this scenario.</span></span> <span data-ttu-id="b8043-230">首先，路徑是由 <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> 列舉值所識別。</span><span class="sxs-lookup"><span data-stu-id="b8043-230">Firstly, the path is identified by the <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> enumeration value.</span></span> <span data-ttu-id="b8043-231">您使用此值與相關增益集成員的多載處理使用包含下列各項的管線︰</span><span class="sxs-lookup"><span data-stu-id="b8043-231">You use this value with overloads of the pertinent add-in members for using pipelines that include the following:</span></span>

- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

- <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>

### <a name="accessing-the-hosts-site-of-origin"></a><span data-ttu-id="b8043-232">存取裝載的原始網站</span><span class="sxs-lookup"><span data-stu-id="b8043-232">Accessing the Host's Site of Origin</span></span>

<span data-ttu-id="b8043-233">為確保增益集能參考原始網站的檔案，必須使用相當於主應用程式的安全性隔離載入增益集。</span><span class="sxs-lookup"><span data-stu-id="b8043-233">To ensure that an add-in can reference files from the site of origin, the add-in must be loaded with security isolation that is equivalent to the host application.</span></span> <span data-ttu-id="b8043-234">此安全性層級是由 <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> 列舉值所識別，並在增益集啟動時傳遞至 <xref:System.AddIn.Hosting.AddInToken.Activate%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b8043-234">This security level is identified by the <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> enumeration value, and passed to the <xref:System.AddIn.Hosting.AddInToken.Activate%2A> method when an add-in is activated.</span></span>

<a name="WPFAddInModelArchitecture"></a>

## <a name="wpf-add-in-architecture"></a><span data-ttu-id="b8043-235">WPF 增益集架構</span><span class="sxs-lookup"><span data-stu-id="b8043-235">WPF Add-In Architecture</span></span>

<span data-ttu-id="b8043-236">就如我們所見，WPF 可讓 .NET Framework 增益集使用 <xref:System.AddIn.Contract.INativeHandleContract>、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 和 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>來執行使用者介面（這是直接或間接衍生自 <xref:System.Windows.FrameworkElement>）。</span><span class="sxs-lookup"><span data-stu-id="b8043-236">At the highest level, as we've seen, WPF enables .NET Framework add-ins to implement user interfaces (that derive directly or indirectly from <xref:System.Windows.FrameworkElement>) using <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> and <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.</span></span> <span data-ttu-id="b8043-237">結果是主應用程式傳回的是從主應用程式的 UI 中顯示的 <xref:System.Windows.FrameworkElement>。</span><span class="sxs-lookup"><span data-stu-id="b8043-237">The result is that the host application is returned a <xref:System.Windows.FrameworkElement> that is displayed from UI in the host application.</span></span>

<span data-ttu-id="b8043-238">針對簡單的 UI 增益集案例，這是開發人員需求的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b8043-238">For simple UI add-in scenarios, this is as much detail as a developer needs.</span></span> <span data-ttu-id="b8043-239">針對更複雜的案例，特別是嘗試使用其他 WPF 服務（例如版面配置、資源和資料系結）的情況，需要 WPF 如何擴充 .NET Framework 增益集模型與 UI 支援的詳細知識，以瞭解其優點和限制。</span><span class="sxs-lookup"><span data-stu-id="b8043-239">For more complex scenarios, particularly those that try to utilize additional WPF services such as layout, resources, and data binding, more detailed knowledge of how WPF extends the .NET Framework add-in model with UI support is required to understand its benefits and limitations.</span></span>

<span data-ttu-id="b8043-240">基本上，WPF 不會將 UI 從增益集傳遞至主應用程式;相反地，WPF 會使用 WPF 互通性來傳遞 UI 的 Win32 視窗控制碼。</span><span class="sxs-lookup"><span data-stu-id="b8043-240">Fundamentally, WPF doesn't pass a UI from an add-in to a host application; instead, WPF passes the Win32 window handle for the UI by using WPF interoperability.</span></span> <span data-ttu-id="b8043-241">因此，當增益集的 UI 傳遞至主應用程式時，將會發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="b8043-241">As such, when a UI from an add-in is passed to a host application, the following occurs:</span></span>

- <span data-ttu-id="b8043-242">在增益集端，WPF 會針對將由主應用程式顯示的 UI 取得視窗控制碼。</span><span class="sxs-lookup"><span data-stu-id="b8043-242">On the add-in side, WPF acquires a window handle for the UI that will be displayed by the host application.</span></span> <span data-ttu-id="b8043-243">視窗控制碼是由衍生自 <xref:System.Windows.Interop.HwndSource> 並實 <xref:System.AddIn.Contract.INativeHandleContract>的內部 WPF 類別所封裝。</span><span class="sxs-lookup"><span data-stu-id="b8043-243">The window handle is encapsulated by an internal WPF class that derives from <xref:System.Windows.Interop.HwndSource> and implements <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="b8043-244">這個類別的實例是由 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 傳回，而且會從增益集的應用程式域封送處理到主應用程式的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="b8043-244">An instance of this class is returned by <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> and is marshaled from the add-in's application domain to the host application's application domain.</span></span>

- <span data-ttu-id="b8043-245">在主應用程式端，WPF 會將 <xref:System.Windows.Interop.HwndSource> 重新封裝為衍生自 <xref:System.Windows.Interop.HwndHost> 的內部 WPF 類別，並使用 <xref:System.AddIn.Contract.INativeHandleContract>。</span><span class="sxs-lookup"><span data-stu-id="b8043-245">On the host application side, WPF repackages the <xref:System.Windows.Interop.HwndSource> as an internal WPF class that derives from <xref:System.Windows.Interop.HwndHost> and consumes <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="b8043-246">這個類別的實例會由 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> 傳回給主應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8043-246">An instance of this class is returned by <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> to the host application.</span></span>

<span data-ttu-id="b8043-247"><xref:System.Windows.Interop.HwndHost> 存在，可從 WPF 使用者介面顯示視窗控制碼所識別的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="b8043-247"><xref:System.Windows.Interop.HwndHost> exists to display user interfaces, identified by window handles, from WPF user interfaces.</span></span> <span data-ttu-id="b8043-248">如需詳細資訊，請參閱 [WPF 和 Win32 互通](../advanced/wpf-and-win32-interoperation.md)。</span><span class="sxs-lookup"><span data-stu-id="b8043-248">For more information, see [WPF and Win32 Interoperation](../advanced/wpf-and-win32-interoperation.md).</span></span>

<span data-ttu-id="b8043-249">總而言之，<xref:System.AddIn.Contract.INativeHandleContract>、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>和 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> 都存在，可讓 WPF UI 的視窗控制碼從增益集傳遞至主應用程式，其中會由 <xref:System.Windows.Interop.HwndHost> 封裝，並顯示主應用程式的 UI。</span><span class="sxs-lookup"><span data-stu-id="b8043-249">In summary, <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, and <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> exist to allow the window handle for a WPF UI to be passed from an add-in to a host application, where it is encapsulated by a <xref:System.Windows.Interop.HwndHost> and displayed the host application's UI.</span></span>

> [!NOTE]
> <span data-ttu-id="b8043-250">因為主應用程式會取得 <xref:System.Windows.Interop.HwndHost>，所以主應用程式無法將 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> 傳回的物件轉換為增益集所實作為的型別（例如，<xref:System.Windows.Controls.UserControl>）。</span><span class="sxs-lookup"><span data-stu-id="b8043-250">Because the host application gets an <xref:System.Windows.Interop.HwndHost>, the host application cannot convert the object that is returned by <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> to the type it is implemented as by the add-in (for example, a <xref:System.Windows.Controls.UserControl>).</span></span>

<span data-ttu-id="b8043-251">根據其本質，<xref:System.Windows.Interop.HwndHost> 有某些限制，會影響主應用程式可以使用它們的方式。</span><span class="sxs-lookup"><span data-stu-id="b8043-251">By its nature, <xref:System.Windows.Interop.HwndHost> has certain limitations that affect how host applications can use them.</span></span> <span data-ttu-id="b8043-252">不過，WPF 會使用增益集案例的數個功能來擴充 <xref:System.Windows.Interop.HwndHost>。</span><span class="sxs-lookup"><span data-stu-id="b8043-252">However, WPF extends <xref:System.Windows.Interop.HwndHost> with several capabilities for add-in scenarios.</span></span> <span data-ttu-id="b8043-253">下文說明這些優點與限制。</span><span class="sxs-lookup"><span data-stu-id="b8043-253">These benefits and limitations are described below.</span></span>

<a name="WPFAddInModelBenefits"></a>

## <a name="wpf-add-in-benefits"></a><span data-ttu-id="b8043-254">WPF 增益集的優點</span><span class="sxs-lookup"><span data-stu-id="b8043-254">WPF Add-In Benefits</span></span>

<span data-ttu-id="b8043-255">由於 WPF 增益集使用者介面是從使用衍生自 <xref:System.Windows.Interop.HwndHost>之內部類別的主應用程式中顯示，因此這些使用者介面會受到與 WPF UI 服務（例如版面配置、轉譯、資料系結、樣式、範本和資源）相關的 <xref:System.Windows.Interop.HwndHost> 功能所限制。</span><span class="sxs-lookup"><span data-stu-id="b8043-255">Because WPF add-in user interfaces are displayed from host applications using an internal class that derives from <xref:System.Windows.Interop.HwndHost>, those user interfaces are constrained by the capabilities of <xref:System.Windows.Interop.HwndHost> with respect to WPF UI services such as layout, rendering, data binding, styles, templates, and resources.</span></span> <span data-ttu-id="b8043-256">不過，WPF 會以包含下列的其他功能來增強其內部 <xref:System.Windows.Interop.HwndHost> 子類別：</span><span class="sxs-lookup"><span data-stu-id="b8043-256">However, WPF augments its internal <xref:System.Windows.Interop.HwndHost> subclass with additional capabilities that include the following:</span></span>

- <span data-ttu-id="b8043-257">在主應用程式的 UI 與增益集的 UI 之間切換。</span><span class="sxs-lookup"><span data-stu-id="b8043-257">Tabbing between a host application's UI and an add-in's UI.</span></span> <span data-ttu-id="b8043-258">請注意，「增益集是 UI」程式設計模型需要增益集端介面卡覆寫 <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> 以啟用 tab 鍵，不論增益集是完全信任還是部分信任。</span><span class="sxs-lookup"><span data-stu-id="b8043-258">Note that the "add-in is a UI" programming model requires the add-in-side adapter to override <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> to enable tabbing, whether the add-in is fully trusted or partially trusted.</span></span>

- <span data-ttu-id="b8043-259">接受從主應用程式使用者介面顯示的增益集使用者介面的協助工具需求。</span><span class="sxs-lookup"><span data-stu-id="b8043-259">Honoring accessibility requirements for add-in user interfaces that are displayed from host application user interfaces.</span></span>

- <span data-ttu-id="b8043-260">讓 WPF 應用程式安全地在多個應用程式域案例中執行。</span><span class="sxs-lookup"><span data-stu-id="b8043-260">Enabling WPF applications to run safely in multiple application domain scenarios.</span></span>

- <span data-ttu-id="b8043-261">當增益集以安全性隔離（也就是部分信任安全性沙箱）執行時，防止不合法存取增益集 UI 視窗控制碼。</span><span class="sxs-lookup"><span data-stu-id="b8043-261">Preventing illegal access to add-in UI window handles when add-ins run with security isolation (that is, a partial-trust security sandbox).</span></span> <span data-ttu-id="b8043-262">呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 可確保此安全性：</span><span class="sxs-lookup"><span data-stu-id="b8043-262">Calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> ensures this security:</span></span>

  - <span data-ttu-id="b8043-263">針對「增益集傳回 UI」程式設計模型，在隔離界限上傳遞增益集 UI 之視窗控制碼的唯一方式，就是呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>。</span><span class="sxs-lookup"><span data-stu-id="b8043-263">For the "add-in returns a UI" programming model, the only way to pass the window handle for an add-in UI across the isolation boundary is to call <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.</span></span>

  - <span data-ttu-id="b8043-264">針對「增益集是 UI」程式設計模型，需要覆寫增益集端介面卡上的 <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>，並呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> （如先前範例所示）是必要的，因為它會從主機端介面卡呼叫增益集端介面卡的 `QueryContract` 執行。</span><span class="sxs-lookup"><span data-stu-id="b8043-264">For the "add-in is a UI" programming model, overriding <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> on the add-in-side adapter and calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> (as shown in the preceding examples) is required, as is calling the add-in-side adapter's `QueryContract` implementation from the host-side adapter.</span></span>

- <span data-ttu-id="b8043-265">提供多個應用程式定義域執行保護。</span><span class="sxs-lookup"><span data-stu-id="b8043-265">Providing multiple application domain execution protection.</span></span> <span data-ttu-id="b8043-266">由於應用程式定義域的限制，增益集應用程式定義域中擲回的未處理例外狀況會導致整個應用程式當機，即使有隔離界限。</span><span class="sxs-lookup"><span data-stu-id="b8043-266">Due to limitations with application domains, unhandled exceptions that are thrown in add-in application domains cause the entire application to crash, even though the isolation boundary exists.</span></span> <span data-ttu-id="b8043-267">不過，WPF 和 .NET Framework 增益集模型提供簡單的方法來解決此問題，並改善應用程式穩定性。</span><span class="sxs-lookup"><span data-stu-id="b8043-267">However, WPF and the .NET Framework add-in model provide a simple way to work around this problem and improve application stability.</span></span> <span data-ttu-id="b8043-268">如果主應用程式是 WPF 應用程式，則會顯示 UI 的 WPF 增益集會為應用程式域執行所在的執行緒建立 <xref:System.Windows.Threading.Dispatcher>。</span><span class="sxs-lookup"><span data-stu-id="b8043-268">A WPF add-in that displays a UI creates a <xref:System.Windows.Threading.Dispatcher> for the thread that the application domain runs on, if the host application is a WPF application.</span></span> <span data-ttu-id="b8043-269">您可以藉由處理 WPF 增益集 <xref:System.Windows.Threading.Dispatcher>的 <xref:System.Windows.Threading.Dispatcher.UnhandledException> 事件，來偵測應用程式域中發生的所有未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b8043-269">You can detect all unhandled exceptions that occur in the application domain by handling the <xref:System.Windows.Threading.Dispatcher.UnhandledException> event of the WPF add-in's <xref:System.Windows.Threading.Dispatcher>.</span></span> <span data-ttu-id="b8043-270">您可以從 [<xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>] 屬性取得 <xref:System.Windows.Threading.Dispatcher>。</span><span class="sxs-lookup"><span data-stu-id="b8043-270">You can get the <xref:System.Windows.Threading.Dispatcher> from the <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> property.</span></span>

<a name="WPFAddInModelLimitations"></a>

## <a name="wpf-add-in-limitations"></a><span data-ttu-id="b8043-271">WPF 增益集限制</span><span class="sxs-lookup"><span data-stu-id="b8043-271">WPF Add-In Limitations</span></span>

<span data-ttu-id="b8043-272">除了 WPF 加入 <xref:System.Windows.Interop.HwndSource>、<xref:System.Windows.Interop.HwndHost>和視窗控制碼所提供之預設行為的優點之外，也有從主應用程式顯示的增益集使用者介面的限制：</span><span class="sxs-lookup"><span data-stu-id="b8043-272">Beyond the benefits that WPF adds to the default behaviors supplied by <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost>, and window handles, there are also limitations for add-in user interfaces that are displayed from host applications:</span></span>

- <span data-ttu-id="b8043-273">從主應用程式顯示的增益集使用者介面不會遵守主應用程式的裁剪行為。</span><span class="sxs-lookup"><span data-stu-id="b8043-273">Add-in user interfaces displayed from a host application do not respect the host application's clipping behavior.</span></span>

- <span data-ttu-id="b8043-274">互通性案例中的「空間」概念也適用於增益集 (請參閱[技術領域概觀](../advanced/technology-regions-overview.md))。</span><span class="sxs-lookup"><span data-stu-id="b8043-274">The concept of *airspace* in interoperability scenarios also applies to add-ins (see [Technology Regions Overview](../advanced/technology-regions-overview.md)).</span></span>

- <span data-ttu-id="b8043-275">裝載應用程式的 UI 服務（例如資源繼承、資料系結和命令）不會自動提供給增益集使用者介面。</span><span class="sxs-lookup"><span data-stu-id="b8043-275">A host application's UI services, such as resource inheritance, data binding, and commanding, are not automatically available to add-in user interfaces.</span></span> <span data-ttu-id="b8043-276">若要向增益集提供這些服務，您需要更新管線。</span><span class="sxs-lookup"><span data-stu-id="b8043-276">To provide these services to the add-in, you need to update the pipeline.</span></span>

- <span data-ttu-id="b8043-277">增益集 UI 無法旋轉、縮放、扭曲，或以其他方式受到轉換影響（請參閱[轉換總覽](../graphics-multimedia/transforms-overview.md)）。</span><span class="sxs-lookup"><span data-stu-id="b8043-277">An add-in UI cannot be rotated, scaled, skewed, or otherwise affected by a transformation (see [Transforms Overview](../graphics-multimedia/transforms-overview.md)).</span></span>

- <span data-ttu-id="b8043-278">從 <xref:System.Drawing> 命名空間的繪製作業所轉譯之增益集使用者介面內的內容，可以包含 Alpha 混合。</span><span class="sxs-lookup"><span data-stu-id="b8043-278">Content inside add-in user interfaces that is rendered by drawing operations from the <xref:System.Drawing> namespace can include alpha blending.</span></span> <span data-ttu-id="b8043-279">不過，增益集 UI 和包含它的主應用程式 UI 都必須是100% 不透明;換句話說，兩者的 `Opacity` 屬性都必須設定為1。</span><span class="sxs-lookup"><span data-stu-id="b8043-279">However, both an add-in UI and the host application UI that contains it must be 100% opaque; in other words, the `Opacity` property on both must be set to 1.</span></span>

- <span data-ttu-id="b8043-280">如果主應用程式中包含增益集 UI 之視窗的 [<xref:System.Windows.Window.AllowsTransparency%2A>] 屬性設定為 [`true`]，則不會隱藏增益集。</span><span class="sxs-lookup"><span data-stu-id="b8043-280">If the <xref:System.Windows.Window.AllowsTransparency%2A> property of a window in the host application that contains an add-in UI is set to `true`, the add-in is invisible.</span></span> <span data-ttu-id="b8043-281">即使增益集 UI 是100% 不透明（也就是 `Opacity` 屬性的值為1），也是如此。</span><span class="sxs-lookup"><span data-stu-id="b8043-281">This is true even if the add-in UI is 100% opaque (that is, the `Opacity` property has a value of 1).</span></span>

- <span data-ttu-id="b8043-282">增益集 UI 必須出現在同一個最上層視窗中的其他 WPF 元素之上。</span><span class="sxs-lookup"><span data-stu-id="b8043-282">An add-in UI must appear on top of other WPF elements in the same top-level window.</span></span>

- <span data-ttu-id="b8043-283">您無法使用 <xref:System.Windows.Media.VisualBrush>來轉譯增益集 UI 的任何部分。</span><span class="sxs-lookup"><span data-stu-id="b8043-283">No portion of an add-in's UI can be rendered using a <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="b8043-284">相反地，增益集可能會製作產生之 UI 的快照集，以建立可使用合約所定義的方法傳遞給主應用程式的點陣圖。</span><span class="sxs-lookup"><span data-stu-id="b8043-284">Instead, the add-in may take a snapshot of the generated UI to create a bitmap that can be passed to the host application using methods defined by the contract.</span></span>

- <span data-ttu-id="b8043-285">無法從增益集 UI 中的 <xref:System.Windows.Controls.MediaElement> 播放媒體檔案。</span><span class="sxs-lookup"><span data-stu-id="b8043-285">Media files cannot be played from a <xref:System.Windows.Controls.MediaElement> in an add-in UI.</span></span>

- <span data-ttu-id="b8043-286">主機應用程式不會收到或引發針對增益集 UI 所產生的滑鼠事件，而且主應用程式 UI 的 `IsMouseOver` 屬性具有 `false`的值。</span><span class="sxs-lookup"><span data-stu-id="b8043-286">Mouse events generated for the add-in UI are neither received nor raised by the host application, and the `IsMouseOver` property for host application UI has a value of `false`.</span></span>

- <span data-ttu-id="b8043-287">當焦點在增益集 UI 中的控制項之間移動時，主應用程式不會接收或引發 `GotFocus` 和 `LostFocus` 事件。</span><span class="sxs-lookup"><span data-stu-id="b8043-287">When focus shifts between controls in an add-in UI, the `GotFocus` and `LostFocus` events are neither received nor raised by the host application.</span></span>

- <span data-ttu-id="b8043-288">包含增益集 UI 的主應用程式部分，會在列印時顯示為白色。</span><span class="sxs-lookup"><span data-stu-id="b8043-288">The portion of a host application that contains an add-in UI appears white when printed.</span></span>

- <span data-ttu-id="b8043-289">如果主應用程式繼續執行，則必須先手動關閉增益集 UI 所建立的所有發送器（請參閱 <xref:System.Windows.Threading.Dispatcher>），才能卸載擁有者增益集。</span><span class="sxs-lookup"><span data-stu-id="b8043-289">All dispatchers (see <xref:System.Windows.Threading.Dispatcher>) created by the add-in UI must be shut down manually before the owner add-in is unloaded if the host application continues execution.</span></span> <span data-ttu-id="b8043-290">合約可以執行方法，讓主應用程式在卸載增益集之前對增益集發出信號，藉此允許增益集 UI 關閉其發送器。</span><span class="sxs-lookup"><span data-stu-id="b8043-290">The contract can implement methods that allow the host application to signal the add-in before the add-in is unloaded, thereby allowing the add-in UI to shut down its dispatchers.</span></span>

- <span data-ttu-id="b8043-291">如果增益集 UI 是 <xref:System.Windows.Controls.InkCanvas> 或包含 <xref:System.Windows.Controls.InkCanvas>，您就無法卸載增益集。</span><span class="sxs-lookup"><span data-stu-id="b8043-291">If an add-in UI is an <xref:System.Windows.Controls.InkCanvas> or contains an <xref:System.Windows.Controls.InkCanvas>, you cannot unload the add-in.</span></span>

<a name="PerformanceOptimization"></a>

## <a name="performance-optimization"></a><span data-ttu-id="b8043-292">效能最佳化</span><span class="sxs-lookup"><span data-stu-id="b8043-292">Performance Optimization</span></span>

<span data-ttu-id="b8043-293">根據預設，當使用多個應用程式域時，每個應用程式所需的各種 .NET Framework 元件都會載入至該應用程式的網域。</span><span class="sxs-lookup"><span data-stu-id="b8043-293">By default, when multiple application domains are used, the various .NET Framework assemblies required by each application are all loaded into that application's domain.</span></span> <span data-ttu-id="b8043-294">如此一來，建立新應用程式定義域以及從其中啟動應用程式所需的時間，可能會影響效能。</span><span class="sxs-lookup"><span data-stu-id="b8043-294">As a result, the time required for creating new application domains and starting applications in them might affect performance.</span></span> <span data-ttu-id="b8043-295">不過，.NET Framework 可讓您藉由指示應用程式跨應用程式域共用元件（如果已載入的話），來縮短開始時間。</span><span class="sxs-lookup"><span data-stu-id="b8043-295">However, the .NET Framework provides a way for you to reduce start times by instructing applications to share assemblies across application domains if they are already loaded.</span></span> <span data-ttu-id="b8043-296">若要這麼做，您可以使用 <xref:System.LoaderOptimizationAttribute> 屬性，這必須套用至進入點方法（`Main`）。</span><span class="sxs-lookup"><span data-stu-id="b8043-296">You do this by using the <xref:System.LoaderOptimizationAttribute> attribute, which must be applied to the entry point method (`Main`).</span></span> <span data-ttu-id="b8043-297">在此情況下，您必須只使用程式碼實作您的應用程式定義 (請參閱[應用程式管理概觀](application-management-overview.md))。</span><span class="sxs-lookup"><span data-stu-id="b8043-297">In this case, you must use only code to implement your application definition (see [Application Management Overview](application-management-overview.md)).</span></span>

## <a name="see-also"></a><span data-ttu-id="b8043-298">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8043-298">See also</span></span>

- <xref:System.LoaderOptimizationAttribute>
- <span data-ttu-id="b8043-299">[增益集和擴充性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span><span class="sxs-lookup"><span data-stu-id="b8043-299">[Add-ins and Extensibility](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))</span></span>
- [<span data-ttu-id="b8043-300">應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="b8043-300">Application Domains</span></span>](../../app-domains/application-domains.md)
- <span data-ttu-id="b8043-301">[.NET Framework 遠端處理總覽](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kwdt6w2k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b8043-301">[.NET Framework Remoting Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kwdt6w2k(v=vs.100))</span></span>
- <span data-ttu-id="b8043-302">[使物件可遠端處理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b8043-302">[Making Objects Remotable](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))</span></span>
- [<span data-ttu-id="b8043-303">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="b8043-303">How-to Topics</span></span>](how-to-topics.md)
