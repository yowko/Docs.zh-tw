---
title: HOW TO：在 WPF 應用程式中加入啟動顯示畫面
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 545fce07d0fab3dca8116f2cacfc068b62cbbde2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537539"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="74666-102">HOW TO：在 WPF 應用程式中加入啟動顯示畫面</span><span class="sxs-lookup"><span data-stu-id="74666-102">How to: Add a Splash Screen to a WPF Application</span></span>

<span data-ttu-id="74666-103">本主題說明如何新增 [啟動] 視窗中，或是*啟動顯示畫面*，Windows Presentation Foundation (WPF) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="74666-103">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>

## <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="74666-104">若要將現有的映像新增為啟動顯示畫面</span><span class="sxs-lookup"><span data-stu-id="74666-104">To add an existing image as a splash screen</span></span>

1.  <span data-ttu-id="74666-105">建立或尋找您想要使用的啟動顯示畫面的映像。</span><span class="sxs-lookup"><span data-stu-id="74666-105">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="74666-106">您可以使用任何支援 Windows Imaging Component (WIC) 的映像格式。</span><span class="sxs-lookup"><span data-stu-id="74666-106">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="74666-107">例如，您可以使用 BMP、 GIF、 JPEG、 PNG 或 TIFF 格式。</span><span class="sxs-lookup"><span data-stu-id="74666-107">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>

2.  <span data-ttu-id="74666-108">將映像檔新增至 WPF 應用程式專案中。</span><span class="sxs-lookup"><span data-stu-id="74666-108">Add the image file to the WPF Application project.</span></span>

3.  <span data-ttu-id="74666-109">在 [**方案總管] 中**，選取的映像。</span><span class="sxs-lookup"><span data-stu-id="74666-109">In **Solution Explorer**, select the image.</span></span>

4.  <span data-ttu-id="74666-110">在 [屬性] 視窗中，按一下下拉式箭號**建置動作**屬性。</span><span class="sxs-lookup"><span data-stu-id="74666-110">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>

5.  <span data-ttu-id="74666-111">選取  **SplashScreen**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="74666-111">Select **SplashScreen** from the drop-down list.</span></span>

6.  <span data-ttu-id="74666-112">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="74666-112">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="74666-113">啟動顯示畫面影像會出現在螢幕的中心，然後再讓 當主應用程式視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="74666-113">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>

## <a name="to-exclude-the-splash-screen-from-build"></a><span data-ttu-id="74666-114">若要從組建排除啟動顯示畫面</span><span class="sxs-lookup"><span data-stu-id="74666-114">To exclude the splash screen from build</span></span>

1.  <span data-ttu-id="74666-115">在 **方案總管 中**，選取 啟動顯示畫面影像。</span><span class="sxs-lookup"><span data-stu-id="74666-115">In **Solution Explorer**, select the splash screen image.</span></span>

2.  <span data-ttu-id="74666-116">在 **屬性**視窗中，將**建置動作**來**None**。</span><span class="sxs-lookup"><span data-stu-id="74666-116">In the **Properties** window, set the **Build Action** to **None**.</span></span>

## <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="74666-117">若要移除應用程式的啟動顯示畫面</span><span class="sxs-lookup"><span data-stu-id="74666-117">To remove the splash screen from an application</span></span>

<span data-ttu-id="74666-118">在 [**方案總管] 中**，刪除啟動顯示畫面影像。</span><span class="sxs-lookup"><span data-stu-id="74666-118">In **Solution Explorer**, delete the splash screen image.</span></span>

## <a name="see-also"></a><span data-ttu-id="74666-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74666-119">See also</span></span>

- <xref:System.Windows.SplashScreen>
- <span data-ttu-id="74666-120">[如何：將現有的項目加入至專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="74666-120">[How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span></span>
