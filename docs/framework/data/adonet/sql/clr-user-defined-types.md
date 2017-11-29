---
title: "CLR 使用者定義類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e81cf54ed9dc516d88b8c7a97c8a5b33b8943d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="clr-user-defined-types"></a>CLR 使用者定義類型
Microsoft SQL Server 可支援以 Microsoft .NET Framework Common Language Runtime (CLR) 實作的使用者定義型別 (UDT)。 這項將 CLR 整合進 SQL Server 的機制可讓您擴充資料庫的型別系統。 UDT 可讓使用者擴充 SQL Server 資料型別系統，以及定義複雜的結構化型別。  
  
 從應用程式架構的角度來看，UDT 有兩個主要優點：  
  
-   (在用戶端及伺服器上) 強式封裝內部狀態與外部行為。  
  
-   與其他相關伺服器功能深度整合。 定義自己的 UDT 後，您可在 SQL Server 中所有可以使用系統型別的內容中使用它，包括資料行定義以及做為變數、參數、函式結果、游標、觸發程序及複寫。  
  
 如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。  
  
 **SQL Server 線上叢書**  
  
1.  [CLR 使用者定義型別](http://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="see-also"></a>另請參閱  
 [在 Managed 程式碼中建立 SQL Server 2005 物件](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
