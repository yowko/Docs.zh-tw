---
title: "如何：在 WPF 應用程式中加入啟動顯示畫面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 973f35f6bfa259490a9423bf0b69d676ad968372
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="fb7e1-102">如何：在 WPF 應用程式中加入啟動顯示畫面</span><span class="sxs-lookup"><span data-stu-id="fb7e1-102">How to: Add a Splash Screen to a WPF Application</span></span>
<span data-ttu-id="fb7e1-103">本主題說明如何新增到 [啟動] 視窗或*啟動顯示畫面*，Windows Presentation Foundation (WPF) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb7e1-103">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>  
  
### <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="fb7e1-104">將現有的映像新增為啟動顯示畫面</span><span class="sxs-lookup"><span data-stu-id="fb7e1-104">To add an existing image as a splash screen</span></span>  
  
1.  <span data-ttu-id="fb7e1-105">建立或尋找您想要使用的啟動顯示畫面影像。</span><span class="sxs-lookup"><span data-stu-id="fb7e1-105">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="fb7e1-106">您可以使用任何支援 Windows 影像處理元件 (WIC) 的映像格式。</span><span class="sxs-lookup"><span data-stu-id="fb7e1-106">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="fb7e1-107">例如，您可以使用 BMP、 GIF、 JPEG、 PNG 或 TIFF 格式。</span><span class="sxs-lookup"><span data-stu-id="fb7e1-107">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>  
  
2.  <span data-ttu-id="fb7e1-108">將影像檔加入至 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="fb7e1-108">Add the image file to the WPF Application project.</span></span> <span data-ttu-id="fb7e1-109">如需詳細資訊，請參閱[NIB： 如何： 加入現有項目加入至專案](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)。</span><span class="sxs-lookup"><span data-stu-id="fb7e1-109">For more information, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span>  
  
3.  <span data-ttu-id="fb7e1-110">在 [方案總管] 中選取的映像。</span><span class="sxs-lookup"><span data-stu-id="fb7e1-110">In Solution Explorer, select the image.</span></span>  
  
4.  <span data-ttu-id="fb7e1-111">在 [屬性] 視窗中，按一下下拉式箭號**建置動作**屬性。</span><span class="sxs-lookup"><span data-stu-id="fb7e1-111">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>  
  
5.  <span data-ttu-id="fb7e1-112">選取**啟動顯示畫面**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="fb7e1-112">Select **SplashScreen** from the drop-down list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fb7e1-113">如果您沒有看到**啟動顯示畫面**選項，請務必檢查您使用[!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]SP1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="fb7e1-113">If you do not see the **SplashScreen** option, be sure to check that you are using [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] SP1 or later.</span></span>  
  
6.  <span data-ttu-id="fb7e1-114">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb7e1-114">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="fb7e1-115">啟動顯示畫面影像出現在螢幕的中央，並再讓主應用程式視窗出現時。</span><span class="sxs-lookup"><span data-stu-id="fb7e1-115">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="fb7e1-116">若要移除應用程式的啟動顯示畫面</span><span class="sxs-lookup"><span data-stu-id="fb7e1-116">To remove the splash screen from an application</span></span>  
  
1.  <span data-ttu-id="fb7e1-117">在 方案總管 中，選取 啟動顯示畫面影像。</span><span class="sxs-lookup"><span data-stu-id="fb7e1-117">In Solution Explorer, select the splash screen image.</span></span>  
  
2.  <span data-ttu-id="fb7e1-118">在 [屬性] 視窗中，設定**建置動作**至**無**。</span><span class="sxs-lookup"><span data-stu-id="fb7e1-118">In the Properties window, set the **Build Action** to **None**.</span></span>  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="fb7e1-119">若要移除應用程式的啟動顯示畫面</span><span class="sxs-lookup"><span data-stu-id="fb7e1-119">To remove the splash screen from an application</span></span>  
  
-   <span data-ttu-id="fb7e1-120">在 方案總管刪除啟動顯示畫面影像。</span><span class="sxs-lookup"><span data-stu-id="fb7e1-120">In Solution Explorer, delete the splash screen image.</span></span>  
  
-   <span data-ttu-id="fb7e1-121">從專案排除啟動顯示畫面影像。</span><span class="sxs-lookup"><span data-stu-id="fb7e1-121">Exclude the splash screen image from the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb7e1-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb7e1-122">See Also</span></span>  
 <xref:System.Windows.SplashScreen>  
 [<span data-ttu-id="fb7e1-123">NIB： 如何： 將現有的項目加入至專案</span><span class="sxs-lookup"><span data-stu-id="fb7e1-123">NIB:How to: Add Existing Items to a Project</span></span>](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)
