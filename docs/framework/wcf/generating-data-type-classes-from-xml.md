---
title: "從 XML 產生資料型別類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 67b9e239c8b60511caf3989c0b3a1a5d6dcc9b26
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="generating-data-type-classes-from-xml"></a>從 XML 產生資料型別類型
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 包含可以從 XML 產生資料類型類別的新功能。 本主題描述如何自動產生資料型別之.NET 部落格 rss 摘要。  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>取得 XML，從.NET 部落格 RSS 摘要  
  
1.  在 Internet Explorer 中，瀏覽至[.NET 部落格 RSS 摘要](https://blogs.msdn.microsoft.com/dotnet/feed/)。  
  
2.  頁面上按一下滑鼠右鍵，然後選取**檢視原始檔**。  
  
3.  複製摘要的文字，按**Ctrl + A**選取所有文字，並**Ctrl + C**複製。  
  
### <a name="creating-the-data-types"></a>建立資料類型  
  
1.  開啟要使用 Proxy 的程式碼檔。 這個檔案應是 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 專案的一部分。  
  
2.  將游標放在檔案中任何現有類別以外的位置。  
  
3.  選取**編輯**，**貼上特殊**，**貼上 XML 做為類別**。  
  
4.  類別，稱為`link`， `rss`， `rssChannel`， `rssChannelImage`，`rssChannelItem`和`rssChannelItemGuid`存取 RSS 摘要中的項目建立具有所需的成員。  
  
### <a name="using-the-generated-classes"></a>使用產生的類別  
  
1.  這些類別一旦產生，就可以像其他類別一樣在程式碼中使用。 下列程式碼範例會傳回 `rssChannelImage` 類別的新執行個體。  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
