---
title: 逐步解說：建立裝載於 WPF 中的 Direct3D9 內容
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
ms.openlocfilehash: 321c4ba8659bd2226fff96e74e81ef24f0077c3d
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847330"
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a><span data-ttu-id="1ba3b-102">逐步解說：建立裝載於 WPF 中的 Direct3D9 內容</span><span class="sxs-lookup"><span data-stu-id="1ba3b-102">Walkthrough: Creating Direct3D9 Content for Hosting in WPF</span></span>
<span data-ttu-id="1ba3b-103">本逐步解說示範如何建立適用於 Windows Presentation Foundation (WPF) 應用程式中裝載 Direct3D9 內容。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-103">This walkthrough shows how to create Direct3D9 content that is suitable for hosting in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="1ba3b-104">如需有關裝載 WPF 應用程式中的 Direct3D9 內容的詳細資訊，請參閱[WPF 和 Direct3D9 互通](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-104">For more information on hosting Direct3D9 content in WPF applications, see [WPF and Direct3D9 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).</span></span>

 <span data-ttu-id="1ba3b-105">在這個逐步解說中，您將執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="1ba3b-105">In this walkthrough, you perform the following tasks:</span></span>

-   <span data-ttu-id="1ba3b-106">建立 Direct3D9 專案。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-106">Create a Direct3D9 project.</span></span>

-   <span data-ttu-id="1ba3b-107">設定 WPF 應用程式中裝載 Direct3D9 專案。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-107">Configure the Direct3D9 project for hosting in a WPF application.</span></span>

 <span data-ttu-id="1ba3b-108">當您完成時，您必須包含用於在 WPF 應用程式中的 Direct3D9 內容的 DLL。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-108">When you are finished, you will have a DLL that contains Direct3D9 content for use in a WPF application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1ba3b-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="1ba3b-109">Prerequisites</span></span>
 <span data-ttu-id="1ba3b-110">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="1ba3b-110">You need the following components to complete this walkthrough:</span></span>

-   <span data-ttu-id="1ba3b-111">Visual Studio 2010。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-111">Visual Studio 2010.</span></span>

-   <span data-ttu-id="1ba3b-112">DirectX SDK 9or 更新版本。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-112">DirectX SDK 9or later.</span></span>

## <a name="creating-the-direct3d9-project"></a><span data-ttu-id="1ba3b-113">建立 Direct3D9 專案</span><span class="sxs-lookup"><span data-stu-id="1ba3b-113">Creating the Direct3D9 Project</span></span>
 <span data-ttu-id="1ba3b-114">第一個步驟是建立和設定 Direct3D9 專案。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-114">The first step is to create and configure the Direct3D9 project.</span></span>

#### <a name="to-create-the-direct3d9-project"></a><span data-ttu-id="1ba3b-115">若要建立 Direct3D9 專案</span><span class="sxs-lookup"><span data-stu-id="1ba3b-115">To create the Direct3D9 project</span></span>

1.  <span data-ttu-id="1ba3b-116">名為 c + + 中建立新的 Win32 專案`D3DContent`。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-116">Create a new Win32 Project in C++ named `D3DContent`.</span></span>

     <span data-ttu-id="1ba3b-117">Win32 應用程式精靈 隨即開啟，並顯示歡迎畫面。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-117">The Win32 Application Wizard opens and displays the Welcome screen.</span></span>

2.  <span data-ttu-id="1ba3b-118">按 [ **下一步**]。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-118">Click **Next**.</span></span>

     <span data-ttu-id="1ba3b-119">[應用程式設定] 畫面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-119">The Application Settings screen appears.</span></span>

3.  <span data-ttu-id="1ba3b-120">在 **應用程式類型：** 區段中，選取**DLL**選項。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-120">In the **Application type:** section, select the **DLL** option.</span></span>

4.  <span data-ttu-id="1ba3b-121">按一下 [ **完成**]。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-121">Click **Finish**.</span></span>

     <span data-ttu-id="1ba3b-122">會產生 D3DContent 專案。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-122">The D3DContent project is generated.</span></span>

5.  <span data-ttu-id="1ba3b-123">在 方案總管 中，以滑鼠右鍵按一下 D3DContent 專案，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-123">In Solution Explorer, right-click the D3DContent project and select **Properties**.</span></span>

     <span data-ttu-id="1ba3b-124">**D3DContent 屬性頁**對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-124">The **D3DContent Property Pages** dialog box opens.</span></span>

6.  <span data-ttu-id="1ba3b-125">選取  **C/c + +** 節點。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-125">Select the **C/C++** node.</span></span>

7.  <span data-ttu-id="1ba3b-126">在 **其他 Include 目錄**欄位中，指定的 DirectX 位置包含的資料夾。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-126">In the **Additional Include Directories** field, specify the location of the DirectX include folder.</span></span> <span data-ttu-id="1ba3b-127">此資料夾的預設位置是 %ProgramFiles%\Microsoft DirectX SDK (*版本*) \Include。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-127">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Include.</span></span>

8.  <span data-ttu-id="1ba3b-128">按兩下**連結器**節點來展開它。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-128">Double-click the **Linker** node to expand it.</span></span>

9. <span data-ttu-id="1ba3b-129">在 **其他程式庫目錄**欄位中，指定 DirectX 程式庫資料夾的位置。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-129">In the **Additional Library Directories** field, specify the location of the DirectX libraries folder.</span></span> <span data-ttu-id="1ba3b-130">此資料夾的預設位置是 %ProgramFiles%\Microsoft DirectX SDK (*版本*) \Lib\x86。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-130">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Lib\x86.</span></span>

10. <span data-ttu-id="1ba3b-131">選取 **輸入**節點。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-131">Select the **Input** node.</span></span>

11. <span data-ttu-id="1ba3b-132">在 **其他相依性**欄位中，新增`d3d9.lib`和`d3dx9.lib`檔案。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-132">In the **Additional Dependencies** field, add the `d3d9.lib` and `d3dx9.lib` files.</span></span>

12. <span data-ttu-id="1ba3b-133">在 [方案總管] 中，加入新模組定義檔 (.def) 名為`D3DContent.def`至專案。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-133">In Solution Explorer, add a new module definition file (.def) named `D3DContent.def` to the project.</span></span>

## <a name="creating-the-direct3d9-content"></a><span data-ttu-id="1ba3b-134">建立 Direct3D9 內容</span><span class="sxs-lookup"><span data-stu-id="1ba3b-134">Creating the Direct3D9 Content</span></span>
 <span data-ttu-id="1ba3b-135">若要取得最佳效能，Direct3D9 內容必須使用特定的設定。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-135">To get the best performance, your Direct3D9 content must use particular settings.</span></span> <span data-ttu-id="1ba3b-136">下列程式碼示範如何建立具有最佳的效能特性的 Direct3D9 介面。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-136">The following code shows how to create a Direct3D9 surface that has the best performance characteristics.</span></span> <span data-ttu-id="1ba3b-137">如需詳細資訊，請參閱 < [Direct3D9 和 WPF 互通性的效能考量](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-137">For more information, see [Performance Considerations for Direct3D9 and WPF Interoperability](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span></span>

#### <a name="to-create-the-direct3d9-content"></a><span data-ttu-id="1ba3b-138">建立 Direct3D9 內容</span><span class="sxs-lookup"><span data-stu-id="1ba3b-138">To create the Direct3D9 content</span></span>

1.  <span data-ttu-id="1ba3b-139">使用 [方案總管] 中，加入名為下列專案的三個 c + + 類別。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-139">Using Solution Explorer, add three C++ classes to the project named the following.</span></span>

     <span data-ttu-id="1ba3b-140">`CRenderer` （含虛擬的解構函式）</span><span class="sxs-lookup"><span data-stu-id="1ba3b-140">`CRenderer` (with virtual destructor)</span></span>

     `CRendererManager`

     `CTriangleRenderer`

2.  <span data-ttu-id="1ba3b-141">在程式碼編輯器中開啟 Renderer.h，並以下列程式碼取代自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-141">Open Renderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]

3.  <span data-ttu-id="1ba3b-142">在程式碼編輯器中開啟 Renderer.cpp，並以下列程式碼取代自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-142">Open Renderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]

4.  <span data-ttu-id="1ba3b-143">在程式碼編輯器中開啟 RendererManager.h，並以下列程式碼取代自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-143">Open RendererManager.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]

5.  <span data-ttu-id="1ba3b-144">在程式碼編輯器中開啟 RendererManager.cpp，並以下列程式碼取代自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-144">Open RendererManager.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]

6.  <span data-ttu-id="1ba3b-145">在程式碼編輯器中開啟 TriangleRenderer.h，並以下列程式碼取代自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-145">Open TriangleRenderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]

7.  <span data-ttu-id="1ba3b-146">在程式碼編輯器中開啟 TriangleRenderer.cpp，並以下列程式碼取代自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-146">Open TriangleRenderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]

8.  <span data-ttu-id="1ba3b-147">在程式碼編輯器中開啟 stdafx.h，並以下列程式碼取代自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-147">Open stdafx.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. <span data-ttu-id="1ba3b-148">在程式碼編輯器中開啟 dllmain.cpp，並以下列程式碼取代自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-148">Open dllmain.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. <span data-ttu-id="1ba3b-149">在程式碼編輯器中開啟 D3DContent.def。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-149">Open D3DContent.def in the code editor.</span></span>

11. <span data-ttu-id="1ba3b-150">下列程式碼取代自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-150">Replace the automatically generated code with the following code.</span></span>

    ```
    LIBRARY "D3DContent"

    EXPORTS

    SetSize
    SetAlpha
    SetNumDesiredSamples
    SetAdapter

    GetBackBufferNoRef
    Render
    Destroy
    ```

12. <span data-ttu-id="1ba3b-151">建置專案。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-151">Build the project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1ba3b-152">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1ba3b-152">Next Steps</span></span>

-   <span data-ttu-id="1ba3b-153">裝載 Direct3D9 內容，在 WPF 應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-153">Host the Direct3D9 content in a WPF application.</span></span> <span data-ttu-id="1ba3b-154">如需詳細資訊，請參閱 <<c0> [ 逐步解說： 裝載 Direct3D9 內容在 WPF 中](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="1ba3b-154">For more information, see [Walkthrough: Hosting Direct3D9 Content in WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1ba3b-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ba3b-155">See Also</span></span>

- <xref:System.Windows.Interop.D3DImage>
- [<span data-ttu-id="1ba3b-156">Direct3D9 和 WPF 互通性的效能考量</span><span class="sxs-lookup"><span data-stu-id="1ba3b-156">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [<span data-ttu-id="1ba3b-157">逐步解說：在 WPF 中裝載 Direct3D9 內容</span><span class="sxs-lookup"><span data-stu-id="1ba3b-157">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)