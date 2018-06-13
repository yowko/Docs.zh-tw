---
title: 從 XML 產生資料型別類型
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: 6b38a0aea3101c70b3c3ec0c8feb4ee88018b64e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498663"
---
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="65015-102">從 XML 產生資料型別類型</span><span class="sxs-lookup"><span data-stu-id="65015-102">Generating Data Type Classes from XML</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<span data-ttu-id="65015-103"> 包含可以從 XML 產生資料類型類別的新功能。</span><span class="sxs-lookup"><span data-stu-id="65015-103"> includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="65015-104">本主題描述如何自動產生資料型別之.NET 部落格 rss 摘要。</span><span class="sxs-lookup"><span data-stu-id="65015-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="65015-105">取得 XML，從.NET 部落格 RSS 摘要</span><span class="sxs-lookup"><span data-stu-id="65015-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1.  <span data-ttu-id="65015-106">在 Internet Explorer 中，瀏覽至[.NET 部落格 RSS 摘要](https://blogs.msdn.microsoft.com/dotnet/feed/)。</span><span class="sxs-lookup"><span data-stu-id="65015-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://blogs.msdn.microsoft.com/dotnet/feed/).</span></span>  
  
2.  <span data-ttu-id="65015-107">頁面上按一下滑鼠右鍵，然後選取**檢視原始檔**。</span><span class="sxs-lookup"><span data-stu-id="65015-107">Right-click the page and select **View Source**.</span></span>  
  
3.  <span data-ttu-id="65015-108">複製摘要的文字，按**Ctrl + A**選取所有文字，並**Ctrl + C**複製。</span><span class="sxs-lookup"><span data-stu-id="65015-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="65015-109">建立資料類型</span><span class="sxs-lookup"><span data-stu-id="65015-109">Creating the data types</span></span>  
  
1.  <span data-ttu-id="65015-110">開啟要使用 Proxy 的程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="65015-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="65015-111">這個檔案應是 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="65015-111">This file should be part of a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="65015-112">將游標放在檔案中任何現有類別以外的位置。</span><span class="sxs-lookup"><span data-stu-id="65015-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3.  <span data-ttu-id="65015-113">選取**編輯**，**貼上特殊**，**貼上 XML 做為類別**。</span><span class="sxs-lookup"><span data-stu-id="65015-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4.  <span data-ttu-id="65015-114">類別，稱為`link`， `rss`， `rssChannel`， `rssChannelImage`，`rssChannelItem`和`rssChannelItemGuid`存取 RSS 摘要中的項目建立具有所需的成員。</span><span class="sxs-lookup"><span data-stu-id="65015-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="65015-115">使用產生的類別</span><span class="sxs-lookup"><span data-stu-id="65015-115">Using the generated classes</span></span>  
  
1.  <span data-ttu-id="65015-116">這些類別一旦產生，就可以像其他類別一樣在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="65015-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="65015-117">下列程式碼範例會傳回 `rssChannelImage` 類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="65015-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
