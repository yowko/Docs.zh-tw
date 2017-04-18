---
title: "HOW TO：加入資料服務參考 (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, 設定"
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# HOW TO：加入資料服務參考 (WCF Data Services)
您可以使用 Visual Studio 中的 **\[加入服務參考\]** 對話方塊，加入 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 的參考。  這樣可以讓您更輕鬆地在 Visual Studio 開發的用戶端應用程式中存取資料服務。  當您完成此程序時，會根據從資料服務取得的中繼資料產生資料類別。  如需詳細資訊，請參閱[產生資料服務用戶端程式庫](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)。  
  
### 加入資料服務參考  
  
1.  \(選擇性\) 如果資料服務不是方案的一部分且尚未執行，請啟動資料服務，並且記下資料服務的 URI。  
  
2.  以滑鼠右鍵按一下用戶端專案，然後選取 \[**加入服務參考**\]。  
  
3.  如果資料服務是目前方案的一部分，請按一下 \[**探索**\]。  
  
     \-或\-  
  
     在 \[**位址**\] 文字方塊中輸入資料服務的基底 URL \(例如 `http://localhost:1234/Northwind.svc`\)，然後按一下 \[**移至**\]。  
  
4.  按一下 \[**確定**\]。  
  
     這將會加入包含資料類別的新程式碼檔案，可用於存取資料服務資源物件，並與其進行互動。  
  
## 請參閱  
 [快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)