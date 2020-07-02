---
title: 如何新增啟動顯示畫面
description: 瞭解如何在 Windows Presentation Foundation （WPF）應用程式中加入啟始視窗或啟動顯示畫面。
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 0d0cf2e2a550320650c3b4a0c257071a0403c32b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617956"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="04546-103">如何：在 WPF 應用程式中加入啟動顯示畫面</span><span class="sxs-lookup"><span data-stu-id="04546-103">How to: Add a Splash Screen to a WPF Application</span></span>

<span data-ttu-id="04546-104">本主題說明如何將啟動視窗或啟動顯示*畫面*新增至 WINDOWS PRESENTATION FOUNDATION （WPF）應用程式。</span><span class="sxs-lookup"><span data-stu-id="04546-104">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>

## <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="04546-105">新增現有的影像做為啟動顯示畫面</span><span class="sxs-lookup"><span data-stu-id="04546-105">To add an existing image as a splash screen</span></span>

1. <span data-ttu-id="04546-106">建立或尋找您要用於啟動顯示畫面的影像。</span><span class="sxs-lookup"><span data-stu-id="04546-106">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="04546-107">您可以使用 Windows 影像處理元件（WIC）所支援的任何影像格式。</span><span class="sxs-lookup"><span data-stu-id="04546-107">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="04546-108">例如，您可以使用 BMP、GIF、JPEG、PNG 或 TIFF 格式。</span><span class="sxs-lookup"><span data-stu-id="04546-108">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>

2. <span data-ttu-id="04546-109">將影像檔案新增至 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="04546-109">Add the image file to the WPF Application project.</span></span>

3. <span data-ttu-id="04546-110">在 [**方案總管**中，選取映射。</span><span class="sxs-lookup"><span data-stu-id="04546-110">In **Solution Explorer**, select the image.</span></span>

4. <span data-ttu-id="04546-111">在 [屬性視窗中，按一下 [**組建動作**] 屬性的下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="04546-111">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>

5. <span data-ttu-id="04546-112">從下拉式清單中選取 [ **SplashScreen** ]。</span><span class="sxs-lookup"><span data-stu-id="04546-112">Select **SplashScreen** from the drop-down list.</span></span>

6. <span data-ttu-id="04546-113">按**F5**以建立並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="04546-113">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="04546-114">啟動顯示畫面影像會出現在螢幕的中央，然後在主應用程式視窗出現時淡化。</span><span class="sxs-lookup"><span data-stu-id="04546-114">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>

## <a name="to-exclude-the-splash-screen-from-build"></a><span data-ttu-id="04546-115">若要從組建中排除啟動顯示畫面</span><span class="sxs-lookup"><span data-stu-id="04546-115">To exclude the splash screen from build</span></span>

1. <span data-ttu-id="04546-116">在 [**方案總管**中，選取啟動顯示畫面影像。</span><span class="sxs-lookup"><span data-stu-id="04546-116">In **Solution Explorer**, select the splash screen image.</span></span>

2. <span data-ttu-id="04546-117">在 [**屬性**] 視窗中，將 [**建立] 動作**設定為 [**無**]。</span><span class="sxs-lookup"><span data-stu-id="04546-117">In the **Properties** window, set the **Build Action** to **None**.</span></span>

## <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="04546-118">若要從應用程式移除啟動顯示畫面</span><span class="sxs-lookup"><span data-stu-id="04546-118">To remove the splash screen from an application</span></span>

<span data-ttu-id="04546-119">在**方案總管**中，刪除啟動顯示畫面影像。</span><span class="sxs-lookup"><span data-stu-id="04546-119">In **Solution Explorer**, delete the splash screen image.</span></span>

## <a name="see-also"></a><span data-ttu-id="04546-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04546-120">See also</span></span>

- <xref:System.Windows.SplashScreen>
- <span data-ttu-id="04546-121">[如何：將現有的項目加入專案中](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="04546-121">[How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span></span>
