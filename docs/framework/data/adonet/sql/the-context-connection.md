---
title: "內容連接 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 內容連接
內部資料存取的問題是很常見的案例。  也就是說，您想要存取執行 Commn Language Runtime \(CLR\) 預存程序或函式所在的同一部伺服器。  有一個選擇是使用 <xref:System.Data.SqlClient.SqlConnection> 建立連接，指定指向本機伺服器的連接字串，並開啟連接。  這需要指定認證以進行登入。  連接與預存程序或函式位於不同的資料庫工作階段中，因此可能會具有不同的 `SET` 選項、位於單獨交易中，或是找不到暫存資料表等。  如果 Managed 預存程序或函式程式碼是在 SQL Server 處理序中執行的，則會是因為其他使用者已連接至該伺服器並執行 SQL 陳述式來叫用它。  您可能會想讓預存程序或函式在該連接的內容及其交易、`SET` 選項等條件中執行。  這就稱為內容連接。  
  
 內容連接可讓您在第一次叫用程式碼的同一內容中執行 Transact\-SQL 陳述式。  如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。  
  
 **SQL Server 線上叢書**  
  
1.  [內容連接](http://go.microsoft.com/fwlink/?LinkId=115395)  
  
## 請參閱  
 [Creating SQL Server 2005 Objects In Managed Code](http://msdn.microsoft.com/zh-tw/5358a825-e19b-49aa-8214-674ce5fed1da)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)