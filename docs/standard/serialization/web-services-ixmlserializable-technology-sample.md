---
title: "Web 服務 IXmlSerializable 技術範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0202d3f1-a50b-427d-a5bb-79208b8f1c22
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 72c7e9e1cbf47dd54726a16ddeb58a193d62dc31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="web-services-ixmlserializable-technology-sample"></a><span data-ttu-id="57306-102">Web 服務 IXmlSerializable 技術範例</span><span class="sxs-lookup"><span data-stu-id="57306-102">Web Services IXmlSerializable Technology Sample</span></span>
[<span data-ttu-id="57306-103">下載範例</span><span class="sxs-lookup"><span data-stu-id="57306-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/IXmlSerializable.zip.exe)  
  
 <span data-ttu-id="57306-104">這個範例會示範如何在 ASP.NET Web 服務中使用 <xref:System.Xml.Serialization.IXmlSerializable> 來控制自訂型別的序列化。</span><span class="sxs-lookup"><span data-stu-id="57306-104">This sample shows how to use <xref:System.Xml.Serialization.IXmlSerializable> to control the serialization of custom types in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="57306-105">若要使用 Visual Studio 建置範例</span><span class="sxs-lookup"><span data-stu-id="57306-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="57306-106">開啟 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]，然後從 [檔案] 功能表中選取 [新網站]。</span><span class="sxs-lookup"><span data-stu-id="57306-106">Open [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="57306-107">在 [新網站] 對話方塊的左窗格中選取想要的程式設計語言，再從右窗格中選取 [ASP.NET Web 服務]。</span><span class="sxs-lookup"><span data-stu-id="57306-107">In the left pane of the **New Web Site** dialog, select your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="57306-108">輸入 **IXmlSerializable** 作為新 Web 服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="57306-108">Type **IXmlSerializable** as the name of the new Web service.</span></span>  
  
4.  <span data-ttu-id="57306-109">在 [方案總管] 視窗中，以滑鼠右鍵按一下 Service.asmx 的圖示，然後選取 [刪除]。另外也請針對 Service.asmx 的 Codebehind 檔案執行這個步驟。</span><span class="sxs-lookup"><span data-stu-id="57306-109">In the Solution Explorer window, right-click the icon for Service.asmx and select **Delete**; repeat this step for the Service.asmx codebehind file.</span></span>  
  
5.  <span data-ttu-id="57306-110">以滑鼠右鍵按一下專案目錄，然後選取 [新增現有項目]。</span><span class="sxs-lookup"><span data-stu-id="57306-110">Right-click the project directory and select **Add Existing Item**.</span></span> <span data-ttu-id="57306-111">在對話方塊中，巡覽至語言特定目錄的 Service 子目錄。</span><span class="sxs-lookup"><span data-stu-id="57306-111">In the dialog, navigate to the Service subdirectory of the language-specific directory.</span></span>  
  
6.  <span data-ttu-id="57306-112">選取 Service.asmx，然後對 Service.asmx 的 Codebehind 檔案重複這個步驟。</span><span class="sxs-lookup"><span data-stu-id="57306-112">Select Service.asmx, then repeat this step for the Service.asmx codebehind file.</span></span>  
  
7.  <span data-ttu-id="57306-113">開啟 [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]，巡覽至包含上述步驟 3 所建立之 IXmlSerializable 目錄的目錄。</span><span class="sxs-lookup"><span data-stu-id="57306-113">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the directory that contains IXmlSerializable directory that you created in step 3 above.</span></span>  
  
8.  <span data-ttu-id="57306-114">以滑鼠右鍵按一下 IXmlSerializable 目錄的圖示，然後選取 [共用和安全性]。</span><span class="sxs-lookup"><span data-stu-id="57306-114">Right-click the icon for the IXmlSerializable directory and select **Sharing and Security**.</span></span>  
  
9. <span data-ttu-id="57306-115">在 [Web 共用] 索引標籤中選取 [共用此資料夾]，並確認預設設定值，包括名稱 IXmlSerializable。</span><span class="sxs-lookup"><span data-stu-id="57306-115">In the Web Sharing tab, select **Share this Folder**, and confirm the default settings, including the name IXmlSerializable.</span></span>  
  
10. <span data-ttu-id="57306-116">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="57306-116">Click **OK**.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="57306-117">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="57306-117">To run the sample</span></span>  
  
1.  <span data-ttu-id="57306-118">開啟瀏覽器視窗，並選取網址列。</span><span class="sxs-lookup"><span data-stu-id="57306-118">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="57306-119">輸入 **http://localhost/IXmlSerializable/Service.asmx**。</span><span class="sxs-lookup"><span data-stu-id="57306-119">Type **http://localhost/IXmlSerializable/Service.asmx**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57306-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57306-120">See Also</span></span>  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 <xref:System.Xml.Serialization>  
 <xref:System.Xml.XmlConvert>  
 <xref:System.Xml.XmlQualifiedName>  
 <xref:System.Xml.XmlReader>  
 <xref:System.Xml.Schema.XmlSchema>  
 <xref:System.Xml.Schema.XmlSchemaSet>  
 <xref:System.Xml.XmlUrlResolver>  
 <xref:System.Xml.XmlWriter>
