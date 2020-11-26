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
# <a name="generating-data-type-classes-from-xml"></a>從 XML 產生資料型別類型

.NET Framework 4.5 包含從 XML 產生資料類型類別的新功能。 本主題說明如何自動產生 .NET Blog RSS 摘要的資料類型。  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>從 .NET Blog RSS 饋送取得 XML  
  
1. 在 Internet Explorer 中，流覽至 [.Net Blog 的 rss](https://devblogs.microsoft.com/dotnet/feed/)摘要。  
  
2. 以滑鼠右鍵按一下頁面，然後選取 [ **視圖來源**]。  
  
3. 按 **ctrl + A** 以選取所有文字，然後按 **ctrl + C** 複製，以複製摘要的文字。  
  
### <a name="creating-the-data-types"></a>建立資料類型  
  
1. 開啟要使用 Proxy 的程式碼檔。 此檔案應該是 .NET Framework 4.5 專案的一部分。  
  
2. 將游標放在檔案中任何現有類別以外的位置。  
  
3. 選取 [ **編輯**]、[ **特殊貼** 上]、[ **貼上 XML 為類別**]。  
  
4. 呼叫 `link` 、 `rss` 、、和的類別， `rssChannel` `rssChannelImage` `rssChannelItem` `rssChannelItemGuid` 是使用存取 RSS 摘要中的專案所需的成員所建立。  
  
### <a name="using-the-generated-classes"></a>使用產生的類別  
  
1. 這些類別一旦產生，就可以像其他類別一樣在程式碼中使用。 下列程式碼範例會傳回 `rssChannelImage` 類別的新執行個體。  
  
    ```csharp
    var channelImage = new rssChannelImage()
    {
        title = "MyImage",
        link = "http://www.contoso.com/images/channelImage.jpg",
        url = "http://www.contoso.com/entries/myEntry.html"
    };  
    ```
