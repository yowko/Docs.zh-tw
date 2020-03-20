---
title: 從 XML 產生資料型別類型
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: d66cbd1806b90d21a483d0c470f953ddfb9c4fca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184126"
---
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="01300-102">從 XML 產生資料型別類型</span><span class="sxs-lookup"><span data-stu-id="01300-102">Generating Data Type Classes from XML</span></span>
<span data-ttu-id="01300-103">.NET 框架 4.5 包括一個新功能，用於從 XML 生成資料類型類。</span><span class="sxs-lookup"><span data-stu-id="01300-103">.NET Framework 4.5 includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="01300-104">本主題介紹如何自動為 .NET 博客 RSS 源生成資料類型。</span><span class="sxs-lookup"><span data-stu-id="01300-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="01300-105">從 .NET 博客 RSS 源獲取 XML</span><span class="sxs-lookup"><span data-stu-id="01300-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1. <span data-ttu-id="01300-106">在 Internet 資源管理器中，導航到[.NET 博客 RSS 源](https://devblogs.microsoft.com/dotnet/feed/)。</span><span class="sxs-lookup"><span data-stu-id="01300-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2. <span data-ttu-id="01300-107">按右鍵頁面並選擇 **"查看源**"。</span><span class="sxs-lookup"><span data-stu-id="01300-107">Right-click the page and select **View Source**.</span></span>  
  
3. <span data-ttu-id="01300-108">通過按**Ctrl_A**以選擇所有文本複製源的文本，然後**按 Ctrl_C**進行複製。</span><span class="sxs-lookup"><span data-stu-id="01300-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="01300-109">建立資料類型</span><span class="sxs-lookup"><span data-stu-id="01300-109">Creating the data types</span></span>  
  
1. <span data-ttu-id="01300-110">開啟要使用 Proxy 的程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="01300-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="01300-111">此檔應是 .NET 框架 4.5 專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="01300-111">This file should be part of a .NET Framework 4.5 project.</span></span>  
  
2. <span data-ttu-id="01300-112">將游標放在檔案中任何現有類別以外的位置。</span><span class="sxs-lookup"><span data-stu-id="01300-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3. <span data-ttu-id="01300-113">選擇 **"編輯**"、"**粘貼特殊**"、"**粘貼XML為類**"。</span><span class="sxs-lookup"><span data-stu-id="01300-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4. <span data-ttu-id="01300-114">使用訪問`link` `rss`RSS 源中的元素的必要成員`rssChannel`創建名為 、、`rssChannelImage``rssChannelItem`和`rssChannelItemGuid`的類。</span><span class="sxs-lookup"><span data-stu-id="01300-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="01300-115">使用產生的類別</span><span class="sxs-lookup"><span data-stu-id="01300-115">Using the generated classes</span></span>  
  
1. <span data-ttu-id="01300-116">這些類別一旦產生，就可以像其他類別一樣在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="01300-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="01300-117">下列程式碼範例會傳回 `rssChannelImage` 類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="01300-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```csharp
    var channelImage = new rssChannelImage()
    {
        title = "MyImage",
        link = "http://www.contoso.com/images/channelImage.jpg",
        url = "http://www.contoso.com/entries/myEntry.html"
    };  
    ```
