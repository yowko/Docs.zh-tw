---
title: 可攜式類別庫的跨平台開發
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: 7caddd7361b8f364762fb4357e35cb918ae99263
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242799"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a><span data-ttu-id="df7c2-102">使用便攜式類庫進行跨平台開發</span><span class="sxs-lookup"><span data-stu-id="df7c2-102">Cross-platform development with the Portable Class Library</span></span>

<span data-ttu-id="df7c2-103">Visual Studio 中的便攜式類庫項目類型可説明您快速輕鬆地為 Microsoft 平臺構建跨平台應用和庫。</span><span class="sxs-lookup"><span data-stu-id="df7c2-103">The Portable Class Library project type in Visual Studio helps you build cross-platform apps and libraries for Microsoft platforms quickly and easily.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

<span data-ttu-id="df7c2-104">可攜式類別庫可幫助您減少開發及測試程式碼的時間和成本。</span><span class="sxs-lookup"><span data-stu-id="df7c2-104">Portable class libraries can help you reduce the time and costs of developing and testing code.</span></span> <span data-ttu-id="df7c2-105">使用此項目類型可以編寫和生成可移植的 .NET 框架程式集,然後從針對多個平臺(如 .NET Framework、iOS 或 Mac)的應用引用這些程式集。</span><span class="sxs-lookup"><span data-stu-id="df7c2-105">Use this project type to write and build portable .NET Framework assemblies, and then reference those assemblies from apps that target multiple platforms such as the .NET Framework, iOS, or Mac.</span></span>

<span data-ttu-id="df7c2-106">即使在 Visual Studio 中建立可攜式類別庫專案並開始開發之後，您還是可以變更目標平台。</span><span class="sxs-lookup"><span data-stu-id="df7c2-106">Even after you create a Portable Class Library project in Visual Studio and start developing it, you can change the target platforms.</span></span> <span data-ttu-id="df7c2-107">Visual Studio 使用新程式集編譯庫,這有助於標識需要在代碼中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="df7c2-107">Visual Studio compiles your library with the new assemblies, which helps you identify the changes you need to make in your code.</span></span>

## <a name="create-a-portable-class-library-project"></a><span data-ttu-id="df7c2-108">建立便攜式類別庫專案</span><span class="sxs-lookup"><span data-stu-id="df7c2-108">Create a Portable Class Library project</span></span>

<span data-ttu-id="df7c2-109">要創建便攜式類庫,請使用可視化工作室中提供的範本。</span><span class="sxs-lookup"><span data-stu-id="df7c2-109">To create a Portable Class Library, use the template provided in Visual Studio.</span></span> <span data-ttu-id="df7c2-110">創建新專案 (**檔案** > **新專案**),並在 **「新項目**」對話方塊中,選擇您的程式設計語言(可視化 C# 或可視化基本)。</span><span class="sxs-lookup"><span data-stu-id="df7c2-110">Create a new project (**File** > **New Project**), and in the **New Project** dialog box, select your programming language (Visual C# or Visual Basic).</span></span> <span data-ttu-id="df7c2-111">然後,選擇**類庫(舊式可移植)** 範本。</span><span class="sxs-lookup"><span data-stu-id="df7c2-111">Then, select the **Class Library (Legacy Portable)** template.</span></span> <span data-ttu-id="df7c2-112">輸入項目的名稱,然後選擇 **"確定**"。</span><span class="sxs-lookup"><span data-stu-id="df7c2-112">Enter a name for your project and choose **OK**.</span></span>

<span data-ttu-id="df7c2-113">將顯示「**新增便攜式類庫**」 對話框。</span><span class="sxs-lookup"><span data-stu-id="df7c2-113">The **Add Portable Class Library** dialog box appears.</span></span> <span data-ttu-id="df7c2-114">選擇兩個或多個目標,然後選擇 **「確定**」。</span><span class="sxs-lookup"><span data-stu-id="df7c2-114">Choose two or more targets, and then choose **OK**.</span></span>

![在可視化工作室中添加攜帶型類庫目標](media/add-portable-class-library.png)

## <a name="change-targets"></a><span data-ttu-id="df7c2-116">變更目標</span><span class="sxs-lookup"><span data-stu-id="df7c2-116">Change targets</span></span>

<span data-ttu-id="df7c2-117">您可以在創建便攜式類庫專案時或開始開發後更改其目標平臺。</span><span class="sxs-lookup"><span data-stu-id="df7c2-117">You can change the target platforms of a portable class library project when you create it or after you've started development.</span></span> <span data-ttu-id="df7c2-118">如果要在建立項目後更改目標,請在**解決方案資源管理員**中開啟可攜式類庫專案的快捷方式選單(不是解決方案),然後選擇**屬性**。</span><span class="sxs-lookup"><span data-stu-id="df7c2-118">If you want to change the targets after you've created your project, in **Solution Explorer**, open the shortcut menu for your Portable Class Library project (not the solution), and then choose **Properties**.</span></span> <span data-ttu-id="df7c2-119">在項目屬性頁上,「**庫**」選項卡顯示專案當前目標的平臺。</span><span class="sxs-lookup"><span data-stu-id="df7c2-119">On the project properties page, the **Library** tab shows the platforms that your project currently targets.</span></span>

![視覺化工作室中可攜式類庫的項目屬性](media/pcl-project-properties.png)

<span data-ttu-id="df7c2-121">要新增或刪除目標,請選擇 **「更改」** 按鈕,然後選擇並清除相應的複選框。</span><span class="sxs-lookup"><span data-stu-id="df7c2-121">To add or remove targets, choose the **Change** button, and then select and clear the appropriate check boxes.</span></span>

<span data-ttu-id="df7c2-122">當您變更目標時，可供您用來開發專案的 API 會變更，以配合您的選項。</span><span class="sxs-lookup"><span data-stu-id="df7c2-122">When you change the targets, the APIs that are available to you for developing your project will change to match your selection.</span></span> <span data-ttu-id="df7c2-123">Visual Studio 會提報因為目標變更而可能發生的錯誤和警告。</span><span class="sxs-lookup"><span data-stu-id="df7c2-123">Visual Studio reports the errors and warnings that may occur as a result of the targets changing.</span></span>

<span data-ttu-id="df7c2-124">如果要在 Visual Studio 中進行更改之前評估程式集的可移植性,可以使用[.NET 可移植性分析器](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)。</span><span class="sxs-lookup"><span data-stu-id="df7c2-124">If you want to evaluate the portability of your assemblies before you make changes in Visual Studio, you can use the [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).</span></span>

## <a name="supported-types-and-members"></a><span data-ttu-id="df7c2-125">支援的類型和成員</span><span class="sxs-lookup"><span data-stu-id="df7c2-125">Supported types and members</span></span>

<span data-ttu-id="df7c2-126">可攜式類別庫專案中提供的類型和成員受到多個相容性因素所限制：</span><span class="sxs-lookup"><span data-stu-id="df7c2-126">The types and members that are available in Portable Class Library projects are constrained by several compatibility factors:</span></span>

- <span data-ttu-id="df7c2-127">它們必須在您選取的目標之間共用。</span><span class="sxs-lookup"><span data-stu-id="df7c2-127">They must be shared across the targets you selected.</span></span>

- <span data-ttu-id="df7c2-128">它們必須在這些目標上具有類似的行為。</span><span class="sxs-lookup"><span data-stu-id="df7c2-128">The must behave similarly across those targets.</span></span>

- <span data-ttu-id="df7c2-129">它們不能是要被取代的候選項。</span><span class="sxs-lookup"><span data-stu-id="df7c2-129">They must not be candidates for deprecation.</span></span>

- <span data-ttu-id="df7c2-130">它們在可攜式環境中必須是合理的，尤其是支援成員無法移植時。</span><span class="sxs-lookup"><span data-stu-id="df7c2-130">They must make sense in a portable environment, especially when supporting members are not portable.</span></span>

<span data-ttu-id="df7c2-131">如果可攜式類別庫和您選取的目標可支援某成員，該成員就會出現在 IntelliSense 的專案中。</span><span class="sxs-lookup"><span data-stu-id="df7c2-131">If a member is supported in the Portable Class Library and for your selected targets, it will appear in your project in IntelliSense.</span></span> <span data-ttu-id="df7c2-132">不過，請記得，可攜式類別庫可能會支援 API，但您是否可以使用 API，取決於您選取的目標。</span><span class="sxs-lookup"><span data-stu-id="df7c2-132">However, remember that an API may be supported in the Portable Class Library, but whether you can use the API depends on the targets you select.</span></span>

## <a name="api-differences-in-the-portable-class-library"></a><span data-ttu-id="df7c2-133">可攜式類別庫中的 API 差異</span><span class="sxs-lookup"><span data-stu-id="df7c2-133">API differences in the Portable Class Library</span></span>

<span data-ttu-id="df7c2-134">為了讓可攜式類別庫組件在所有支援的平台上都相容，可攜式類別庫中有部分成員已稍微變更。</span><span class="sxs-lookup"><span data-stu-id="df7c2-134">To make Portable Class Library assemblies compatible across all supported platforms, some members have been slightly changed in the Portable Class Library.</span></span>

## <a name="use-the-portable-class-library"></a><span data-ttu-id="df7c2-135">使用便攜式類別庫</span><span class="sxs-lookup"><span data-stu-id="df7c2-135">Use the Portable Class Library</span></span>

<span data-ttu-id="df7c2-136">建立可攜式類別庫專案之後，即可從其他專案參考該專案。</span><span class="sxs-lookup"><span data-stu-id="df7c2-136">After you build your Portable Class Library project, you just reference it from other projects.</span></span> <span data-ttu-id="df7c2-137">您可以參考此專案，或是包含您想要存取之類別的特定組件。</span><span class="sxs-lookup"><span data-stu-id="df7c2-137">You can reference either the project or specific assemblies that contain the classes you want to access.</span></span>

<span data-ttu-id="df7c2-138">若要執行參考可攜式類別庫組件的應用程式，電腦上必須安裝目標平台所需的版本 (或以後版本)。</span><span class="sxs-lookup"><span data-stu-id="df7c2-138">To run an app that references a Portable Class Library assembly, the required version (or later) of the targeted platforms must be installed on your computer.</span></span> <span data-ttu-id="df7c2-139">Visual Studio 包含所有必要架構，因此不需要進一步修改用來開發應用程式的電腦，即可執行該應用程式。</span><span class="sxs-lookup"><span data-stu-id="df7c2-139">Visual Studio contains all the required frameworks, so you can run the app without further modification on the computer that you used to develop the app.</span></span>

### <a name="deploy-a-universal-windows-app"></a><span data-ttu-id="df7c2-140">部署通用 Windows 應用</span><span class="sxs-lookup"><span data-stu-id="df7c2-140">Deploy a Universal Windows app</span></span>

<span data-ttu-id="df7c2-141">當您創建引用便攜式類庫程式集的通用 Windows 應用時,部署該應用所需的一切內容都包含在應用包中,並且不需要執行其他步驟。</span><span class="sxs-lookup"><span data-stu-id="df7c2-141">When you create a Universal Windows app that references a Portable Class Library assembly, everything you need to deploy the app is included in the app package, and no further steps are required.</span></span>

### <a name="deploy-a-net-framework-app"></a><span data-ttu-id="df7c2-142">部署 .NET 架構套用</span><span class="sxs-lookup"><span data-stu-id="df7c2-142">Deploy a .NET Framework app</span></span>

<span data-ttu-id="df7c2-143">當您部署參考可攜式類別庫組件的 .NET Framework 應用程式時，必須指定正確 .NET Framework 版本的相依性。</span><span class="sxs-lookup"><span data-stu-id="df7c2-143">When you deploy a .NET Framework app that references a Portable Class Library assembly, you must specify a dependency on the correct version of the .NET Framework.</span></span> <span data-ttu-id="df7c2-144">藉由指定此相依性，您就可以確保所需的版本會隨著您的應用程式一起安裝。</span><span class="sxs-lookup"><span data-stu-id="df7c2-144">By specifying this dependency, you ensure that the required version is installed with your app.</span></span>

- <span data-ttu-id="df7c2-145">要使用 ClickOnce 部署建立依賴項:在**解決方案資源管理器**中,選擇要發布的專案的專案節點。</span><span class="sxs-lookup"><span data-stu-id="df7c2-145">To create a dependency with ClickOnce deployment: In **Solution Explorer**, choose the project node for the project you want to publish.</span></span> <span data-ttu-id="df7c2-146">(這是引用便攜式類庫專案的專案。在選單列上,選擇 **「項目** > **屬性**」,然後選擇「**發布**」選項卡。在 **「發布」** 頁上,選擇 **「先決條件**」。。</span><span class="sxs-lookup"><span data-stu-id="df7c2-146">(This is the project that references the Portable Class Library project.) On the menu bar, choose **Project** > **Properties**, and then choose the **Publish** tab. On the **Publish** page, choose **Prerequisites**.</span></span> <span data-ttu-id="df7c2-147">選取所需的 .NET Framework 版本做為必要條件。</span><span class="sxs-lookup"><span data-stu-id="df7c2-147">Select the required .NET Framework version as a prerequisite.</span></span>

- <span data-ttu-id="df7c2-148">要使用設置項目創建依賴項:在**解決方案資源管理員**中,選擇設置專案。</span><span class="sxs-lookup"><span data-stu-id="df7c2-148">To create a dependency with a setup project: In **Solution Explorer**, choose the setup project.</span></span> <span data-ttu-id="df7c2-149">在功能表欄上,選擇 **「項目** > **屬性** > **先決條件**」。。</span><span class="sxs-lookup"><span data-stu-id="df7c2-149">On the menu bar, choose **Project** > **Properties** > **Prerequisites**.</span></span> <span data-ttu-id="df7c2-150">選取所需的 .NET Framework 版本做為必要條件。</span><span class="sxs-lookup"><span data-stu-id="df7c2-150">Select the required .NET Framework version as a prerequisite.</span></span>

<span data-ttu-id="df7c2-151">有關部署 .NET 框架應用的詳細資訊,請參閱[開發人員的部署指南](../../../docs/framework/deployment/deployment-guide-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="df7c2-151">For more information about deploying .NET Framework apps, see [Deployment Guide for Developers](../../../docs/framework/deployment/deployment-guide-for-developers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="df7c2-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df7c2-152">See also</span></span>

- [<span data-ttu-id="df7c2-153">搭配 MVVM 使用可攜式類別庫</span><span class="sxs-lookup"><span data-stu-id="df7c2-153">Using Portable Class Library with MVVM</span></span>](using-portable-class-library-with-model-view-view-model.md)
- [<span data-ttu-id="df7c2-154">面向多個平台的庫的應用資源</span><span class="sxs-lookup"><span data-stu-id="df7c2-154">App Resources for Libraries That Target Multiple Platforms</span></span>](app-resources-for-libraries-that-target-multiple-platforms.md)
- [<span data-ttu-id="df7c2-155">.NET Portability Analyzer</span><span class="sxs-lookup"><span data-stu-id="df7c2-155">.NET Portability Analyzer</span></span>](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [<span data-ttu-id="df7c2-156">適用於 Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援</span><span class="sxs-lookup"><span data-stu-id="df7c2-156">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [<span data-ttu-id="df7c2-157">部署</span><span class="sxs-lookup"><span data-stu-id="df7c2-157">Deployment</span></span>](../../../docs/framework/deployment/net-framework-applications.md)
