---
title: 從 XML 產生資料型別類型
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: bf5596211e78842153b7406273626a7fa3c3aeea
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990280"
---
# <a name="generating-data-type-classes-from-xml"></a>從 XML 產生資料型別類型
.NET Framework 4.5 包含從 XML 產生資料類型類別的新功能。 本主題說明如何自動產生 .NET Blog RSS 饋送的資料類型。  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>從 .NET Blog RSS 饋送取得 XML  
  
1. 在 Internet Explorer 中，流覽至[.Net BLOG rss 饋送](https://devblogs.microsoft.com/dotnet/feed/)。  
  
2. 以滑鼠右鍵按一下頁面，然後選取 [ **View Source**]。  
  
3. 按下**Ctrl + A**選取所有文字，然後按**ctrl + C**複製，以複製摘要的文字。  
  
### <a name="creating-the-data-types"></a>建立資料類型  
  
1. 開啟要使用 Proxy 的程式碼檔。 這個檔案應該是 .NET Framework 4.5 專案的一部分。  
  
2. 將游標放在檔案中任何現有類別以外的位置。  
  
3. 選取 [**編輯**]、[**貼上特殊**]、[貼上 XML]**作為類別**。  
  
4. 名`link`為`rss`、、 、`rssChannelImage`和的類別，是使用存取RSS摘要中的專案所需的成員所建立。`rssChannelItemGuid` `rssChannel` `rssChannelItem`  
  
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
