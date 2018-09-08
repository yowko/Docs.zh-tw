---
title: 逐步解說：在 WPF 中裝載 Direct3D9 內容
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: 5e7edfbeb9a3cddcdcd81d9c87e5e85bfc947339
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44188705"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a><span data-ttu-id="f69c4-102">逐步解說：在 WPF 中裝載 Direct3D9 內容</span><span class="sxs-lookup"><span data-stu-id="f69c4-102">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>
<span data-ttu-id="f69c4-103">本逐步解說示範如何裝載 Windows Presentation Foundation (WPF) 應用程式中的 Direct3D9 內容。</span><span class="sxs-lookup"><span data-stu-id="f69c4-103">This walkthrough shows how to host Direct3D9 content in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 <span data-ttu-id="f69c4-104">在這個逐步解說中，您將執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="f69c4-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="f69c4-105">建立 WPF 專案來裝載 Direct3D9 內容。</span><span class="sxs-lookup"><span data-stu-id="f69c4-105">Create a WPF project to host the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="f69c4-106">匯入 Direct3D9 內容。</span><span class="sxs-lookup"><span data-stu-id="f69c4-106">Import the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="f69c4-107">使用顯示 Direct3D9 內容<xref:System.Windows.Interop.D3DImage>類別。</span><span class="sxs-lookup"><span data-stu-id="f69c4-107">Display the Direct3D9 content by using the <xref:System.Windows.Interop.D3DImage> class.</span></span>  
  
 <span data-ttu-id="f69c4-108">當您完成時，您會知道如何裝載在 WPF 應用程式中的 Direct3D9 內容。</span><span class="sxs-lookup"><span data-stu-id="f69c4-108">When you are finished, you will know how to host Direct3D9 content in a WPF application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f69c4-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="f69c4-109">Prerequisites</span></span>  
 <span data-ttu-id="f69c4-110">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="f69c4-110">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="f69c4-111">.</span><span class="sxs-lookup"><span data-stu-id="f69c4-111">.</span></span>  
  
-   <span data-ttu-id="f69c4-112">DirectX 9 或更新版本的 SDK。</span><span class="sxs-lookup"><span data-stu-id="f69c4-112">DirectX SDK 9 or later.</span></span>  
  
-   <span data-ttu-id="f69c4-113">包含與 WPF 相容的格式中的 Direct3D9 內容的 DLL。</span><span class="sxs-lookup"><span data-stu-id="f69c4-113">A DLL that contains Direct3D9 content in a WPF-compatible format.</span></span> <span data-ttu-id="f69c4-114">如需詳細資訊，請參閱 < [WPF 和 Direct3D9 互通](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)並[逐步解說： 建立 Direct3D9 內容裝載於 WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="f69c4-114">For more information, see [WPF and Direct3D9 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) and [Walkthrough: Creating Direct3D9 Content for Hosting in WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span></span>  
  
## <a name="creating-the-wpf-project"></a><span data-ttu-id="f69c4-115">建立 WPF 專案</span><span class="sxs-lookup"><span data-stu-id="f69c4-115">Creating the WPF Project</span></span>  
 <span data-ttu-id="f69c4-116">第一個步驟是建立 WPF 應用程式的專案。</span><span class="sxs-lookup"><span data-stu-id="f69c4-116">The first step is to create the project for the WPF application.</span></span>  
  
#### <a name="to-create-the-wpf-project"></a><span data-ttu-id="f69c4-117">若要建立 WPF 專案</span><span class="sxs-lookup"><span data-stu-id="f69c4-117">To create the WPF project</span></span>  
  
-   <span data-ttu-id="f69c4-118">新的 WPF 應用程式專案中 Visual C# 建立名為`D3DHost`。</span><span class="sxs-lookup"><span data-stu-id="f69c4-118">Create a new WPF Application project in Visual C# named `D3DHost`.</span></span> <span data-ttu-id="f69c4-119">如需詳細資訊，請參閱[如何：建立新的 WPF 應用程式專案](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)。</span><span class="sxs-lookup"><span data-stu-id="f69c4-119">For more information, see [How to: Create a New WPF Application Project](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
     <span data-ttu-id="f69c4-120">在中開啟 MainWindow.xaml [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f69c4-120">MainWindow.xaml opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
## <a name="importing-the-direct3d9-content"></a><span data-ttu-id="f69c4-121">匯入 Direct3D9 內容</span><span class="sxs-lookup"><span data-stu-id="f69c4-121">Importing the Direct3D9 Content</span></span>  
 <span data-ttu-id="f69c4-122">您使用匯入 Direct3D9 內容從 unmanaged DLL`DllImport`屬性。</span><span class="sxs-lookup"><span data-stu-id="f69c4-122">You import the Direct3D9 content from an unmanaged DLL by using the `DllImport` attribute.</span></span>  
  
#### <a name="to-import-direct3d9-content"></a><span data-ttu-id="f69c4-123">若要匯入 Direct3D9 內容</span><span class="sxs-lookup"><span data-stu-id="f69c4-123">To import Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="f69c4-124">在程式碼編輯器中開啟 MainWindow.xaml.cs。</span><span class="sxs-lookup"><span data-stu-id="f69c4-124">Open MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2.  <span data-ttu-id="f69c4-125">下列程式碼取代自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f69c4-125">Replace the automatically generated code with the following code.</span></span>  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a><span data-ttu-id="f69c4-126">裝載 Direct3D9 內容</span><span class="sxs-lookup"><span data-stu-id="f69c4-126">Hosting the Direct3D9 Content</span></span>  
 <span data-ttu-id="f69c4-127">最後，使用<xref:System.Windows.Interop.D3DImage>類別，以裝載 Direct3D9 內容。</span><span class="sxs-lookup"><span data-stu-id="f69c4-127">Finally, use the <xref:System.Windows.Interop.D3DImage> class to host the Direct3D9 content.</span></span>  
  
#### <a name="to-host-the-direct3d9-content"></a><span data-ttu-id="f69c4-128">若要裝載 Direct3D9 內容</span><span class="sxs-lookup"><span data-stu-id="f69c4-128">To host the Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="f69c4-129">在 MainWindow.xaml 中，自動產生的 XAML 取代為下列 XAML。</span><span class="sxs-lookup"><span data-stu-id="f69c4-129">In MainWindow.xaml, replace the automatically generated XAML with the following XAML.</span></span>  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  <span data-ttu-id="f69c4-130">建置專案。</span><span class="sxs-lookup"><span data-stu-id="f69c4-130">Build the project.</span></span>  
  
3.  <span data-ttu-id="f69c4-131">複製包含 bin/Debug 資料夾的 Direct3D9 內容的 DLL。</span><span class="sxs-lookup"><span data-stu-id="f69c4-131">Copy the DLL that contains the Direct3D9 content to the bin/Debug folder.</span></span>  
  
4.  <span data-ttu-id="f69c4-132">按 F5 執行專案。</span><span class="sxs-lookup"><span data-stu-id="f69c4-132">Press F5 to run the project.</span></span>  
  
     <span data-ttu-id="f69c4-133">Direct3D9 內容會出現在 WPF 應用程式中。</span><span class="sxs-lookup"><span data-stu-id="f69c4-133">The Direct3D9 content appears within the WPF application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f69c4-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f69c4-134">See Also</span></span>  
 <xref:System.Windows.Interop.D3DImage>  
 [<span data-ttu-id="f69c4-135">Direct3D9 和 WPF 互通性的效能考量</span><span class="sxs-lookup"><span data-stu-id="f69c4-135">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
