---
title: "從 XML 產生資料型別類型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 從 XML 產生資料型別類型
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 包含可以從 XML 產生資料類型類別的新功能。  本主題說明如何自動產生 MSDN Library RSS 摘要的資料類型。  
  
### 從 MSDN Library RSS 摘要取得 XML  
  
1.  在 Internet Explorer 中，瀏覽至 [MSDN RSS 摘要](http://go.microsoft.com/fwlink/?LinkId=225209)。  
  
2.  以滑鼠右鍵按一下頁面，然後選取 \[**檢視原始檔**\]。  
  
3.  按下 **Ctrl\+A** 選取所有文字，再按 **Ctrl\+C** 複製，以複製摘要的文字。  
  
### 建立資料類型  
  
1.  開啟要使用 Proxy 的程式碼檔。  這個檔案應是 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 專案的一部分。  
  
2.  將游標放在檔案中任何現有類別以外的位置。  
  
3.  依序選取 \[**編輯**\]、\[**選擇性貼上**\]、\[**貼上 XML 做為類別**\]。  
  
4.  隨即建立名為 `rss`、`rssChannel`、`rssChannelImage` 和 `rssChannelItem` 的類別，其中包含存取 RSS 摘要中元素所需的成員。  
  
### 使用產生的類別  
  
1.  這些類別一旦產生，就可以像其他類別一樣在程式碼中使用。  下列程式碼範例會傳回 `rssChannelImage` 類別的新執行個體。  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
  
    ```