---
title: "CLR 預存程序 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# CLR 預存程序
預存程序是無法在純量運算式中使用的常式。  它們可將表格式結果及訊息傳回到用戶端、叫用資料定義語言 \(DDL\) 及資料操作語言 \(DML\) 陳述式，並傳回輸出參數。  
  
> [!NOTE]
>  Microsoft Visual Basic 支援輸出參數的方式，與 Microsoft Visual C\# 所使用的方式不同。  您必須指定以傳址方式傳遞參數，並套用 \<Out\(\)\> 屬性以表示輸出參數，如下所示：  
  
```  
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```  
  
 如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。  
  
 **SQL Server 線上叢書**  
  
1.  [CLR 預存程序](http://go.microsoft.com/fwlink/?LinkId=115400)  
  
## 請參閱  
 [Creating SQL Server 2005 Objects In Managed Code](http://msdn.microsoft.com/zh-tw/5358a825-e19b-49aa-8214-674ce5fed1da)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)