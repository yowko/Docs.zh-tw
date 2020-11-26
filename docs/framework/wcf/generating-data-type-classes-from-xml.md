---
title: 從 XML 產生資料型別類型
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: a7920a8c8c4f279dd3fc52029c5da5e9b685efe2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238245"
---
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="1c14d-102">從 XML 產生資料型別類型</span><span class="sxs-lookup"><span data-stu-id="1c14d-102">Generating Data Type Classes from XML</span></span>

<span data-ttu-id="1c14d-103">.NET Framework 4.5 包含從 XML 產生資料類型類別的新功能。</span><span class="sxs-lookup"><span data-stu-id="1c14d-103">.NET Framework 4.5 includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="1c14d-104">本主題說明如何自動產生 .NET Blog RSS 摘要的資料類型。</span><span class="sxs-lookup"><span data-stu-id="1c14d-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="1c14d-105">從 .NET Blog RSS 饋送取得 XML</span><span class="sxs-lookup"><span data-stu-id="1c14d-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1. <span data-ttu-id="1c14d-106">在 Internet Explorer 中，流覽至 [.Net Blog 的 rss](https://devblogs.microsoft.com/dotnet/feed/)摘要。</span><span class="sxs-lookup"><span data-stu-id="1c14d-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2. <span data-ttu-id="1c14d-107">以滑鼠右鍵按一下頁面，然後選取 [ **視圖來源**]。</span><span class="sxs-lookup"><span data-stu-id="1c14d-107">Right-click the page and select **View Source**.</span></span>  
  
3. <span data-ttu-id="1c14d-108">按 **ctrl + A** 以選取所有文字，然後按 **ctrl + C** 複製，以複製摘要的文字。</span><span class="sxs-lookup"><span data-stu-id="1c14d-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="1c14d-109">建立資料類型</span><span class="sxs-lookup"><span data-stu-id="1c14d-109">Creating the data types</span></span>  
  
1. <span data-ttu-id="1c14d-110">開啟要使用 Proxy 的程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="1c14d-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="1c14d-111">此檔案應該是 .NET Framework 4.5 專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="1c14d-111">This file should be part of a .NET Framework 4.5 project.</span></span>  
  
2. <span data-ttu-id="1c14d-112">將游標放在檔案中任何現有類別以外的位置。</span><span class="sxs-lookup"><span data-stu-id="1c14d-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3. <span data-ttu-id="1c14d-113">選取 [ **編輯**]、[ **特殊貼** 上]、[ **貼上 XML 為類別**]。</span><span class="sxs-lookup"><span data-stu-id="1c14d-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4. <span data-ttu-id="1c14d-114">呼叫 `link` 、 `rss` 、、和的類別， `rssChannel` `rssChannelImage` `rssChannelItem` `rssChannelItemGuid` 是使用存取 RSS 摘要中的專案所需的成員所建立。</span><span class="sxs-lookup"><span data-stu-id="1c14d-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="1c14d-115">使用產生的類別</span><span class="sxs-lookup"><span data-stu-id="1c14d-115">Using the generated classes</span></span>  
  
1. <span data-ttu-id="1c14d-116">這些類別一旦產生，就可以像其他類別一樣在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="1c14d-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="1c14d-117">下列程式碼範例會傳回 `rssChannelImage` 類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="1c14d-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```csharp
    var channelImage = new rssChannelImage()
    {
        title = "MyImage",
        link = "http://www.contoso.com/images/channelImage.jpg",
        url = "http://www.contoso.com/entries/myEntry.html"
    };  
    ```
