---
title: 從 XML 產生資料型別類型
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: 977b12b5c61c196a4f033361d37785e4ed0af73a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975847"
---
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="1d4ce-102">從 XML 產生資料型別類型</span><span class="sxs-lookup"><span data-stu-id="1d4ce-102">Generating Data Type Classes from XML</span></span>
<span data-ttu-id="1d4ce-103">.NET Framework 4.5 包含從 XML 產生資料類型類別的新功能。</span><span class="sxs-lookup"><span data-stu-id="1d4ce-103">.NET Framework 4.5 includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="1d4ce-104">本主題說明如何自動產生 .NET Blog RSS 饋送的資料類型。</span><span class="sxs-lookup"><span data-stu-id="1d4ce-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="1d4ce-105">從 .NET Blog RSS 饋送取得 XML</span><span class="sxs-lookup"><span data-stu-id="1d4ce-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1. <span data-ttu-id="1d4ce-106">在 Internet Explorer 中，流覽至[.Net BLOG rss 饋送](https://devblogs.microsoft.com/dotnet/feed/)。</span><span class="sxs-lookup"><span data-stu-id="1d4ce-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2. <span data-ttu-id="1d4ce-107">以滑鼠右鍵按一下頁面，然後選取 [ **View Source**]。</span><span class="sxs-lookup"><span data-stu-id="1d4ce-107">Right-click the page and select **View Source**.</span></span>  
  
3. <span data-ttu-id="1d4ce-108">按下**Ctrl + A**選取所有文字，然後按**ctrl + C**複製，以複製摘要的文字。</span><span class="sxs-lookup"><span data-stu-id="1d4ce-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="1d4ce-109">建立資料類型</span><span class="sxs-lookup"><span data-stu-id="1d4ce-109">Creating the data types</span></span>  
  
1. <span data-ttu-id="1d4ce-110">開啟要使用 Proxy 的程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="1d4ce-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="1d4ce-111">這個檔案應該是 .NET Framework 4.5 專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="1d4ce-111">This file should be part of a .NET Framework 4.5 project.</span></span>  
  
2. <span data-ttu-id="1d4ce-112">將游標放在檔案中任何現有類別以外的位置。</span><span class="sxs-lookup"><span data-stu-id="1d4ce-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3. <span data-ttu-id="1d4ce-113">選取 [**編輯**]、[**貼上特殊**]、[貼上 XML]**作為類別**。</span><span class="sxs-lookup"><span data-stu-id="1d4ce-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4. <span data-ttu-id="1d4ce-114">名為 `link`、`rss`、`rssChannel`、`rssChannelImage`、`rssChannelItem` 和 `rssChannelItemGuid` 的類別會使用必要的成員來建立，以存取 RSS 摘要中的元素。</span><span class="sxs-lookup"><span data-stu-id="1d4ce-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="1d4ce-115">使用產生的類別</span><span class="sxs-lookup"><span data-stu-id="1d4ce-115">Using the generated classes</span></span>  
  
1. <span data-ttu-id="1d4ce-116">這些類別一旦產生，就可以像其他類別一樣在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="1d4ce-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="1d4ce-117">下列程式碼範例會傳回 `rssChannelImage` 類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="1d4ce-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```csharp
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
