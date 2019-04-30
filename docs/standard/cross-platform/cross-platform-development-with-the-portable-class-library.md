---
title: 可攜式類別庫的跨平台開發
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
author: mairaw
ms.author: mairaw
ms.openlocfilehash: afaa8e118bb21e5c1e4f1c53b1d0d29ca6bb3bf5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055052"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a><span data-ttu-id="0ab0a-102">使用可攜式類別庫的跨平台開發</span><span class="sxs-lookup"><span data-stu-id="0ab0a-102">Cross-platform development with the Portable Class Library</span></span>

<span data-ttu-id="0ab0a-103">在 Visual Studio 中的可攜式類別庫專案類型可協助您快速且輕鬆地建置跨平台應用程式和程式庫，針對 Microsoft 平台。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-103">The Portable Class Library project type in Visual Studio helps you build cross-platform apps and libraries for Microsoft platforms quickly and easily.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

<span data-ttu-id="0ab0a-104">可攜式類別庫可幫助您減少開發及測試程式碼的時間和成本。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-104">Portable class libraries can help you reduce the time and costs of developing and testing code.</span></span> <span data-ttu-id="0ab0a-105">撰寫及建置可攜式.NET Framework 組件，使用這種專案類型，並接著從.NET Framework、 iOS 或 mac 等的多個平台為目標的應用程式中參考這些組件</span><span class="sxs-lookup"><span data-stu-id="0ab0a-105">Use this project type to write and build portable .NET Framework assemblies, and then reference those assemblies from apps that target multiple platforms such as the .NET Framework, iOS, or Mac.</span></span>

<span data-ttu-id="0ab0a-106">即使在 Visual Studio 中建立可攜式類別庫專案並開始開發之後，您還是可以變更目標平台。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-106">Even after you create a Portable Class Library project in Visual Studio and start developing it, you can change the target platforms.</span></span> <span data-ttu-id="0ab0a-107">Visual Studio 會編譯您的程式庫的新的組件，可協助您識別您需要在程式碼中進行的變更。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-107">Visual Studio compiles your library with the new assemblies, which helps you identify the changes you need to make in your code.</span></span>

## <a name="create-a-portable-class-library-project"></a><span data-ttu-id="0ab0a-108">建立可攜式類別庫專案</span><span class="sxs-lookup"><span data-stu-id="0ab0a-108">Create a Portable Class Library project</span></span>

<span data-ttu-id="0ab0a-109">若要建立可攜式類別庫，請使用 Visual Studio 中提供的範本。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-109">To create a Portable Class Library, use the template provided in Visual Studio.</span></span> <span data-ttu-id="0ab0a-110">建立新的專案 (**檔案** > **新專案**)，然後在**新專案**對話方塊方塊中，選取您的程式語言 （Visual C# 或 Visual Basic）。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-110">Create a new project (**File** > **New Project**), and in the **New Project** dialog box, select your programming language (Visual C# or Visual Basic).</span></span> <span data-ttu-id="0ab0a-111">然後，選取**類別庫 （舊版可攜式）** 範本。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-111">Then, select the **Class Library (Legacy Portable)** template.</span></span> <span data-ttu-id="0ab0a-112">輸入您專案的名稱，然後選擇**確定**。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-112">Enter a name for your project and choose **OK**.</span></span>

<span data-ttu-id="0ab0a-113">**加入可攜式類別庫** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-113">The **Add Portable Class Library** dialog box appears.</span></span> <span data-ttu-id="0ab0a-114">選擇兩個或多個目標，然後選擇**確定**。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-114">Choose two or more targets, and then choose **OK**.</span></span>

![Visual Studio 中加入可攜式類別程式庫的目標](media/add-portable-class-library.png)

## <a name="change-targets"></a><span data-ttu-id="0ab0a-116">變更目標</span><span class="sxs-lookup"><span data-stu-id="0ab0a-116">Change targets</span></span>

<span data-ttu-id="0ab0a-117">當您在建立時，或您已經開始開發之後，您可以變更目標平台的可攜式類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-117">You can change the target platforms of a portable class library project when you create it or after you’ve started development.</span></span> <span data-ttu-id="0ab0a-118">如果您想要建立您的專案，在之後變更目標**方案總管**，開啟您的可攜式類別庫專案 （而非方案），捷徑功能表，然後選擇**屬性**.</span><span class="sxs-lookup"><span data-stu-id="0ab0a-118">If you want to change the targets after you’ve created your project, in **Solution Explorer**, open the shortcut menu for your Portable Class Library project (not the solution), and then choose **Properties**.</span></span> <span data-ttu-id="0ab0a-119">在專案屬性頁面上，**程式庫** 索引標籤上顯示的平台專案的目前目標。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-119">On the project properties page, the **Library** tab shows the platforms that your project currently targets.</span></span>

![在 Visual Studio 中的可攜式類別庫的專案屬性](media/pcl-project-properties.png)

<span data-ttu-id="0ab0a-121">若要新增或移除目標，選擇**變更**按鈕，然後選取及清除適當的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-121">To add or remove targets, choose the **Change** button, and then select and clear the appropriate check boxes.</span></span>

<span data-ttu-id="0ab0a-122">當您變更目標時，可供您用來開發專案的 API 會變更，以配合您的選項。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-122">When you change the targets, the APIs that are available to you for developing your project will change to match your selection.</span></span> <span data-ttu-id="0ab0a-123">Visual Studio 會提報因為目標變更而可能發生的錯誤和警告。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-123">Visual Studio reports the errors and warnings that may occur as a result of the targets changing.</span></span>

<span data-ttu-id="0ab0a-124">如果您想要評估的可攜性的組件之前，請在 Visual Studio 中進行變更，您可以使用[.NET Portability Analyzer](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-124">If you want to evaluate the portability of your assemblies before you make changes in Visual Studio, you can use the [.NET Portability Analyzer](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).</span></span>

## <a name="supported-types-and-members"></a><span data-ttu-id="0ab0a-125">支援的類型和成員</span><span class="sxs-lookup"><span data-stu-id="0ab0a-125">Supported types and members</span></span>

<span data-ttu-id="0ab0a-126">可攜式類別庫專案中提供的類型和成員受到多個相容性因素所限制：</span><span class="sxs-lookup"><span data-stu-id="0ab0a-126">The types and members that are available in Portable Class Library projects are constrained by several compatibility factors:</span></span>

- <span data-ttu-id="0ab0a-127">它們必須在您選取的目標之間共用。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-127">They must be shared across the targets you selected.</span></span>

- <span data-ttu-id="0ab0a-128">它們必須在這些目標上具有類似的行為。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-128">The must behave similarly across those targets.</span></span>

- <span data-ttu-id="0ab0a-129">它們不能是要被取代的候選項。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-129">They must not be candidates for deprecation.</span></span>

- <span data-ttu-id="0ab0a-130">它們在可攜式環境中必須是合理的，尤其是支援成員無法移植時。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-130">They must make sense in a portable environment, especially when supporting members are not portable.</span></span>

<span data-ttu-id="0ab0a-131">如果可攜式類別庫和您選取的目標可支援某成員，該成員就會出現在 IntelliSense 的專案中。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-131">If a member is supported in the Portable Class Library and for your selected targets, it will appear in your project in IntelliSense.</span></span> <span data-ttu-id="0ab0a-132">不過，請記得，可攜式類別庫可能會支援 API，但您是否可以使用 API，取決於您選取的目標。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-132">However, remember that an API may be supported in the Portable Class Library, but whether you can use the API depends on the targets you select.</span></span>

## <a name="api-differences-in-the-portable-class-library"></a><span data-ttu-id="0ab0a-133">可攜式類別庫中的 API 差異</span><span class="sxs-lookup"><span data-stu-id="0ab0a-133">API differences in the Portable Class Library</span></span>

<span data-ttu-id="0ab0a-134">為了讓可攜式類別庫組件在所有支援的平台上都相容，可攜式類別庫中有部分成員已稍微變更。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-134">To make Portable Class Library assemblies compatible across all supported platforms, some members have been slightly changed in the Portable Class Library.</span></span>

## <a name="use-the-portable-class-library"></a><span data-ttu-id="0ab0a-135">使用可攜式類別庫</span><span class="sxs-lookup"><span data-stu-id="0ab0a-135">Use the Portable Class Library</span></span>

<span data-ttu-id="0ab0a-136">建立可攜式類別庫專案之後，即可從其他專案參考該專案。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-136">After you build your Portable Class Library project, you just reference it from other projects.</span></span> <span data-ttu-id="0ab0a-137">您可以參考此專案，或是包含您想要存取之類別的特定組件。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-137">You can reference either the project or specific assemblies that contain the classes you want to access.</span></span>

<span data-ttu-id="0ab0a-138">若要執行參考可攜式類別庫組件的應用程式，電腦上必須安裝目標平台所需的版本 (或以後版本)。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-138">To run an app that references a Portable Class Library assembly, the required version (or later) of the targeted platforms must be installed on your computer.</span></span> <span data-ttu-id="0ab0a-139">Visual Studio 包含所有必要架構，因此不需要進一步修改用來開發應用程式的電腦，即可執行該應用程式。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-139">Visual Studio contains all the required frameworks, so you can run the app without further modification on the computer that you used to develop the app.</span></span>

### <a name="deploy-a-universal-windows-app"></a><span data-ttu-id="0ab0a-140">將通用 Windows 應用程式部署</span><span class="sxs-lookup"><span data-stu-id="0ab0a-140">Deploy a Universal Windows app</span></span>

<span data-ttu-id="0ab0a-141">當您建立通用 Windows 應用程式參考可攜式類別庫組件，您要部署應用程式的所有一切皆內含在應用程式套件中，並不需要任何進一步的步驟。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-141">When you create a Universal Windows app that references a Portable Class Library assembly, everything you need to deploy the app is included in the app package, and no further steps are required.</span></span>

### <a name="deploy-a-net-framework-app"></a><span data-ttu-id="0ab0a-142">部署.NET Framework 應用程式</span><span class="sxs-lookup"><span data-stu-id="0ab0a-142">Deploy a .NET Framework app</span></span>

<span data-ttu-id="0ab0a-143">當您部署參考可攜式類別庫組件的 .NET Framework 應用程式時，必須指定正確 .NET Framework 版本的相依性。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-143">When you deploy a .NET Framework app that references a Portable Class Library assembly, you must specify a dependency on the correct version of the .NET Framework.</span></span> <span data-ttu-id="0ab0a-144">藉由指定此相依性，您就可以確保所需的版本會隨著您的應用程式一起安裝。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-144">By specifying this dependency, you ensure that the required version is installed with your app.</span></span>

- <span data-ttu-id="0ab0a-145">若要建立與 ClickOnce 部署的相依性：在 [**方案總管] 中**，選擇您想要發佈專案的專案節點。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-145">To create a dependency with ClickOnce deployment: In **Solution Explorer**, choose the project node for the project you want to publish.</span></span> <span data-ttu-id="0ab0a-146">(這是參考可攜式類別庫專案的專案。)在功能表列上選擇 **專案** > **屬性**，然後選擇**發佈** 索引標籤。在 **發佈**頁面上，選擇**必要條件**。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-146">(This is the project that references the Portable Class Library project.) On the menu bar, choose **Project** > **Properties**, and then choose the **Publish** tab. On the **Publish** page, choose **Prerequisites**.</span></span> <span data-ttu-id="0ab0a-147">選取所需的 .NET Framework 版本做為必要條件。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-147">Select the required .NET Framework version as a prerequisite.</span></span>

- <span data-ttu-id="0ab0a-148">若要建立安裝專案的相依性：在 **方案總管 中**，選擇 安裝專案。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-148">To create a dependency with a setup project: In **Solution Explorer**, choose the setup project.</span></span> <span data-ttu-id="0ab0a-149">在功能表列上選擇 **專案** > **屬性** > **必要條件**。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-149">On the menu bar, choose **Project** > **Properties** > **Prerequisites**.</span></span> <span data-ttu-id="0ab0a-150">選取所需的 .NET Framework 版本做為必要條件。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-150">Select the required .NET Framework version as a prerequisite.</span></span>

<span data-ttu-id="0ab0a-151">如需部署.NET Framework 應用程式的詳細資訊，請參閱 <<c0> [ 開發人員部署手冊](../../../docs/framework/deployment/deployment-guide-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="0ab0a-151">For more information about deploying .NET Framework apps, see [Deployment Guide for Developers](../../../docs/framework/deployment/deployment-guide-for-developers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0ab0a-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ab0a-152">See also</span></span>

- [<span data-ttu-id="0ab0a-153">搭配 MVVM 使用可攜式類別庫</span><span class="sxs-lookup"><span data-stu-id="0ab0a-153">Using Portable Class Library with MVVM</span></span>](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md)
- [<span data-ttu-id="0ab0a-154">以多平台為目標之程式庫的應用程式資源</span><span class="sxs-lookup"><span data-stu-id="0ab0a-154">App Resources for Libraries That Target Multiple Platforms</span></span>](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md)
- [<span data-ttu-id="0ab0a-155">.NET portability Analyzer</span><span class="sxs-lookup"><span data-stu-id="0ab0a-155">.NET Portability Analyzer</span></span>](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [<span data-ttu-id="0ab0a-156">Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援</span><span class="sxs-lookup"><span data-stu-id="0ab0a-156">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [<span data-ttu-id="0ab0a-157">部署</span><span class="sxs-lookup"><span data-stu-id="0ab0a-157">Deployment</span></span>](../../../docs/framework/deployment/net-framework-applications.md)
