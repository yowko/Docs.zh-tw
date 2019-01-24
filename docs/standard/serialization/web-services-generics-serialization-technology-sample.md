---
title: Web 服務泛型序列化技術範例
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: 27e0a7621bc77b62e36a0bbbdfa25f0ec3778798
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636574"
---
# <a name="web-services-generics-serialization-technology-sample"></a><span data-ttu-id="fcfaa-102">Web 服務泛型序列化技術範例</span><span class="sxs-lookup"><span data-stu-id="fcfaa-102">Web Services Generics Serialization Technology Sample</span></span>
[<span data-ttu-id="fcfaa-103">下載範例</span><span class="sxs-lookup"><span data-stu-id="fcfaa-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 <span data-ttu-id="fcfaa-104">此範例顯示如何在 ASP.NET Web 服務中使用及控制泛型的序列化。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-104">This sample shows how to use and control the serialization of generics in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="fcfaa-105">若要使用 Visual Studio 建置範例</span><span class="sxs-lookup"><span data-stu-id="fcfaa-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="fcfaa-106">開啟 Visual Studio，然後從 [檔案] 功能表中選取 [新網站]。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-106">Open Visual Studio and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="fcfaa-107">在 [新網站] 對話方塊的左窗格中選取想要的程式設計語言，再從右窗格中選取 [ASP.NET Web 服務]。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-107">In the **New Web Site** dialog, select from the left pane your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="fcfaa-108">按一下 [瀏覽] 並巡覽至 \CS\GenericsService 子目錄。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-108">Click **Browse** and navigate to the \CS\GenericsService subdirectory.</span></span>  
  
4.  <span data-ttu-id="fcfaa-109">選取 Service.asmx，在 Visual Studio 中開啟該檔案。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-109">Select Service.asmx to open the file in Visual Studio.</span></span>  
  
5.  <span data-ttu-id="fcfaa-110">在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-110">On the **Build** menu, click **Build Solution**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fcfaa-111">此清單中的前五個步驟是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-111">The first five steps in this list are optional.</span></span> <span data-ttu-id="fcfaa-112">.NET Framework 執行階段會在第一次要求服務時，自動產生 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-112">The .NET Framework runtime will automatically generate the Web service the first time the service is requested.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fcfaa-113">以下為建置範例的必要步驟。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-113">The following steps are required to build the sample.</span></span>  
  
1.  <span data-ttu-id="fcfaa-114">開啟 [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]，巡覽至 \CS 子目錄。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the \CS subdirectory.</span></span>  
  
2.  <span data-ttu-id="fcfaa-115">以滑鼠右鍵按一下 GenericsService 子目錄的圖示，然後選取 [共用和安全性]。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-115">Right-click the icon for the GenericsService subdirectory, and select **Sharing and Security**.</span></span>  
  
3.  <span data-ttu-id="fcfaa-116">在 [Web 共用] 索引標籤中，選取 [共用此資料夾]。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-116">In the **Web Sharing** tab, select **Share this Folder**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fcfaa-117">記下 [別名] 窗格中列出的虛擬目錄名稱，因為執行範例時會需要這個名稱。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-117">Take note of the virtual directory name that is listed in the **Aliases** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-build-the-sample-using-internet-information-services"></a><span data-ttu-id="fcfaa-118">若要使用網際網路資訊服務建置範例</span><span class="sxs-lookup"><span data-stu-id="fcfaa-118">To build the sample using Internet Information Services</span></span>  
  
1.  <span data-ttu-id="fcfaa-119">開啟 [網際網路資訊服務] 管理嵌入式管理單元，並展開 [網站]。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-119">Open the **Internet Information Services** management snap-in and expand **Web Sites**.</span></span>  
  
2.  <span data-ttu-id="fcfaa-120">以滑鼠左鍵按一下 [預設的網站]，然後依序選取 [新增]、[虛擬目錄] 以建立 [虛擬目錄建立精靈]。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-120">Left-click **Default Web Site**, select **New**, and then select **Virtual Directory?** to create the **Virtual Directory Creation Wizard**.</span></span>  
  
3.  <span data-ttu-id="fcfaa-121">按 [下一步]，輸入虛擬目錄的公用別名，再按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-121">Click **Next**, enter the public alias for your virtual directory, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="fcfaa-122">輸入儲存範例所在目錄的路徑 (通常是 \CS\GenericsService 子目錄)，然後按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-122">Enter the path to the directory where you saved the sample (normally the \CS\GenericsService subdirectory) and click **Next**.</span></span> <span data-ttu-id="fcfaa-123">按 [下一步] 完成精靈。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-123">Click **Next** to finish the wizard.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fcfaa-124">記下 [別名] 窗格中列出的虛擬目錄名稱，因為執行範例時會需要這個名稱。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-124">Take note of the virtual directory name that is listed in the **Alias** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="fcfaa-125">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="fcfaa-125">To run the sample</span></span>  
  
1.  <span data-ttu-id="fcfaa-126">開啟瀏覽器視窗，並選取網址列。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-126">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="fcfaa-127">型別`http://localhost/[virtual directory]/Service.asmx`，其中`[virtual directory]`代表建置範例時所建立的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-127">Type `http://localhost/[virtual directory]/Service.asmx`, where `[virtual directory]` represents the virtual directory you created when you built the sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcfaa-128">備註</span><span class="sxs-lookup"><span data-stu-id="fcfaa-128">Remarks</span></span>  
 <span data-ttu-id="fcfaa-129">範例會顯示預設的 ASP.NET 網頁，其中包含 Web 服務定義的連結。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-129">The sample displays a default ASP.NET page that contains links to the definition of the Web Service.</span></span> <span data-ttu-id="fcfaa-130">除了修改 Web 服務的原始程式碼之外，您還可以自訂顯示內容。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-130">You can customize the display in addition to modifying the source code for the Web service.</span></span> <span data-ttu-id="fcfaa-131">如需詳細資訊，請參閱[建置 XML Web Service 用戶端](https://msdn.microsoft.com/library/c606f3cb-4111-45b4-ae42-9300420fa16c)。</span><span class="sxs-lookup"><span data-stu-id="fcfaa-131">For more information, see [Building XML Web Service Clients](https://msdn.microsoft.com/library/c606f3cb-4111-45b4-ae42-9300420fa16c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcfaa-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcfaa-132">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Web.Services>
- <xref:System.Xml.Serialization>
- [<span data-ttu-id="fcfaa-133">序列化</span><span class="sxs-lookup"><span data-stu-id="fcfaa-133">Serialization</span></span>](../../../docs/standard/serialization/index.md)
- [<span data-ttu-id="fcfaa-134">使用 ASP.NET 和 XML Web Service 用戶端建立的 XML Web Service</span><span class="sxs-lookup"><span data-stu-id="fcfaa-134">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)
