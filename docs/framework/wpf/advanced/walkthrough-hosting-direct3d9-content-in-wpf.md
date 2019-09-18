---
title: 逐步解說：將 Direct3D9 內容裝載在 WPF 中
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: 2c31c044aa50a74255a61da1675037ab3d09f615
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053456"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a><span data-ttu-id="b9808-102">逐步解說：將 Direct3D9 內容裝載在 WPF 中</span><span class="sxs-lookup"><span data-stu-id="b9808-102">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>

<span data-ttu-id="b9808-103">本逐步解說說明如何在 Windows Presentation Foundation （WPF）應用程式中裝載 Direct3D9 內容。</span><span class="sxs-lookup"><span data-stu-id="b9808-103">This walkthrough shows how to host Direct3D9 content in a Windows Presentation Foundation (WPF) application.</span></span>

<span data-ttu-id="b9808-104">在這個逐步解說中，您將執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="b9808-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="b9808-105">建立 WPF 專案來裝載 Direct3D9 內容。</span><span class="sxs-lookup"><span data-stu-id="b9808-105">Create a WPF project to host the Direct3D9 content.</span></span>

- <span data-ttu-id="b9808-106">匯入 Direct3D9 內容。</span><span class="sxs-lookup"><span data-stu-id="b9808-106">Import the Direct3D9 content.</span></span>

- <span data-ttu-id="b9808-107">使用<xref:System.Windows.Interop.D3DImage>類別顯示 Direct3D9 內容。</span><span class="sxs-lookup"><span data-stu-id="b9808-107">Display the Direct3D9 content by using the <xref:System.Windows.Interop.D3DImage> class.</span></span>

 <span data-ttu-id="b9808-108">當您完成時，您會知道如何在 WPF 應用程式中裝載 Direct3D9 內容。</span><span class="sxs-lookup"><span data-stu-id="b9808-108">When you are finished, you will know how to host Direct3D9 content in a WPF application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b9808-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="b9808-109">Prerequisites</span></span>

<span data-ttu-id="b9808-110">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="b9808-110">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="b9808-111">Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="b9808-111">Visual Studio.</span></span>

- <span data-ttu-id="b9808-112">DirectX SDK 9 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="b9808-112">DirectX SDK 9 or later.</span></span>

- <span data-ttu-id="b9808-113">包含 WPF 相容格式之 Direct3D9 內容的 DLL。</span><span class="sxs-lookup"><span data-stu-id="b9808-113">A DLL that contains Direct3D9 content in a WPF-compatible format.</span></span> <span data-ttu-id="b9808-114">如需詳細資訊，請參閱[WPF 和 Direct3D9 交互操作](wpf-and-direct3d9-interoperation.md)性和[逐步解說：建立在 WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)中裝載的 Direct3D9 內容。</span><span class="sxs-lookup"><span data-stu-id="b9808-114">For more information, see [WPF and Direct3D9 Interoperation](wpf-and-direct3d9-interoperation.md) and [Walkthrough: Creating Direct3D9 Content for Hosting in WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span></span>

## <a name="creating-the-wpf-project"></a><span data-ttu-id="b9808-115">建立 WPF 專案</span><span class="sxs-lookup"><span data-stu-id="b9808-115">Creating the WPF Project</span></span>

<span data-ttu-id="b9808-116">第一個步驟是建立 WPF 應用程式的專案。</span><span class="sxs-lookup"><span data-stu-id="b9808-116">The first step is to create the project for the WPF application.</span></span>

### <a name="to-create-the-wpf-project"></a><span data-ttu-id="b9808-117">若要建立 WPF 專案</span><span class="sxs-lookup"><span data-stu-id="b9808-117">To create the WPF project</span></span>

<span data-ttu-id="b9808-118">在 Visual C#中建立名為`D3DHost`的新 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="b9808-118">Create a new WPF Application project in Visual C# named `D3DHost`.</span></span> <span data-ttu-id="b9808-119">如需詳細資訊，請參閱[逐步解說：我的第一個 WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="b9808-119">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

<span data-ttu-id="b9808-120">Mainwindow.xaml 會在中[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]開啟。</span><span class="sxs-lookup"><span data-stu-id="b9808-120">MainWindow.xaml opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

## <a name="importing-the-direct3d9-content"></a><span data-ttu-id="b9808-121">匯入 Direct3D9 內容</span><span class="sxs-lookup"><span data-stu-id="b9808-121">Importing the Direct3D9 Content</span></span>

<span data-ttu-id="b9808-122">您可以使用`DllImport`屬性，從非受控 DLL 匯入 Direct3D9 的內容。</span><span class="sxs-lookup"><span data-stu-id="b9808-122">You import the Direct3D9 content from an unmanaged DLL by using the `DllImport` attribute.</span></span>

### <a name="to-import-direct3d9-content"></a><span data-ttu-id="b9808-123">匯入 Direct3D9 內容</span><span class="sxs-lookup"><span data-stu-id="b9808-123">To import Direct3D9 content</span></span>

1. <span data-ttu-id="b9808-124">在程式碼編輯器中開啟 MainWindow.xaml.cs。</span><span class="sxs-lookup"><span data-stu-id="b9808-124">Open MainWindow.xaml.cs in the Code Editor.</span></span>

2. <span data-ttu-id="b9808-125">使用下列程式碼取代自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b9808-125">Replace the automatically generated code with the following code.</span></span>

    [!code-csharp[System.Windows.Interop.D3DImage#1](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]

## <a name="hosting-the-direct3d9-content"></a><span data-ttu-id="b9808-126">裝載 Direct3D9 內容</span><span class="sxs-lookup"><span data-stu-id="b9808-126">Hosting the Direct3D9 Content</span></span>

<span data-ttu-id="b9808-127">最後，使用<xref:System.Windows.Interop.D3DImage>類別來裝載 Direct3D9 內容。</span><span class="sxs-lookup"><span data-stu-id="b9808-127">Finally, use the <xref:System.Windows.Interop.D3DImage> class to host the Direct3D9 content.</span></span>

### <a name="to-host-the-direct3d9-content"></a><span data-ttu-id="b9808-128">裝載 Direct3D9 內容</span><span class="sxs-lookup"><span data-stu-id="b9808-128">To host the Direct3D9 content</span></span>

1. <span data-ttu-id="b9808-129">在 Mainwindow.xaml 中，以下列 XAML 取代自動產生的 XAML。</span><span class="sxs-lookup"><span data-stu-id="b9808-129">In MainWindow.xaml, replace the automatically generated XAML with the following XAML.</span></span>

    [!code-xaml[System.Windows.Interop.D3DImage#10](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]

2. <span data-ttu-id="b9808-130">建置專案。</span><span class="sxs-lookup"><span data-stu-id="b9808-130">Build the project.</span></span>

3. <span data-ttu-id="b9808-131">將包含 Direct3D9 內容的 DLL 複製到 bin/Debug 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b9808-131">Copy the DLL that contains the Direct3D9 content to the bin/Debug folder.</span></span>

4. <span data-ttu-id="b9808-132">按 F5 執行專案。</span><span class="sxs-lookup"><span data-stu-id="b9808-132">Press F5 to run the project.</span></span>

    <span data-ttu-id="b9808-133">Direct3D9 內容會出現在 WPF 應用程式中。</span><span class="sxs-lookup"><span data-stu-id="b9808-133">The Direct3D9 content appears within the WPF application.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9808-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9808-134">See also</span></span>

- <xref:System.Windows.Interop.D3DImage>
- [<span data-ttu-id="b9808-135">Direct3D9 和 WPF 互通性的效能考量</span><span class="sxs-lookup"><span data-stu-id="b9808-135">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
