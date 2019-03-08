---
title: 從 XML 產生資料型別類型
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: a6666f1ba23dd563bd7a005d458cd7fe8253c3af
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679082"
---
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="70b61-102">從 XML 產生資料型別類型</span><span class="sxs-lookup"><span data-stu-id="70b61-102">Generating Data Type Classes from XML</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] <span data-ttu-id="70b61-103">包含可以從 XML 產生資料類型類別的新功能。</span><span class="sxs-lookup"><span data-stu-id="70b61-103">includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="70b61-104">本主題描述如何自動產生.NET 部落格 rss 摘要的 資料類型。</span><span class="sxs-lookup"><span data-stu-id="70b61-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="70b61-105">取得 XML.NET 部落格 rss 摘要</span><span class="sxs-lookup"><span data-stu-id="70b61-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1.  <span data-ttu-id="70b61-106">在 Internet Explorer 中，瀏覽至[.NET 部落格 RSS 摘要](https://devblogs.microsoft.com/dotnet/feed/)。</span><span class="sxs-lookup"><span data-stu-id="70b61-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2.  <span data-ttu-id="70b61-107">以滑鼠右鍵按一下  頁面上，然後選取**檢視原始檔**。</span><span class="sxs-lookup"><span data-stu-id="70b61-107">Right-click the page and select **View Source**.</span></span>  
  
3.  <span data-ttu-id="70b61-108">複製摘要的文字，按下**Ctrl + A**以選取所有文字，並**Ctrl + C**複製。</span><span class="sxs-lookup"><span data-stu-id="70b61-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="70b61-109">建立資料類型</span><span class="sxs-lookup"><span data-stu-id="70b61-109">Creating the data types</span></span>  
  
1.  <span data-ttu-id="70b61-110">開啟要使用 Proxy 的程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="70b61-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="70b61-111">這個檔案應是 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="70b61-111">This file should be part of a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="70b61-112">將游標放在檔案中任何現有類別以外的位置。</span><span class="sxs-lookup"><span data-stu-id="70b61-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3.  <span data-ttu-id="70b61-113">選取 **編輯**，**貼上特殊**，**貼上做為類別的 XML**。</span><span class="sxs-lookup"><span data-stu-id="70b61-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4.  <span data-ttu-id="70b61-114">類別，稱為`link`， `rss`， `rssChannel`， `rssChannelImage`，`rssChannelItem`和`rssChannelItemGuid`存取 RSS 摘要中的項目會建立具有必要的成員。</span><span class="sxs-lookup"><span data-stu-id="70b61-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="70b61-115">使用產生的類別</span><span class="sxs-lookup"><span data-stu-id="70b61-115">Using the generated classes</span></span>  
  
1.  <span data-ttu-id="70b61-116">這些類別一旦產生，就可以像其他類別一樣在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="70b61-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="70b61-117">下列程式碼範例會傳回 `rssChannelImage` 類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="70b61-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
