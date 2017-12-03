---
title: "LINQ to SQL 範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f39db9e-0e62-42c9-8c98-bb8b54cec98c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 03805d8917d16752cd84838fe210540a68c3f905
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="linq-to-sql-sample"></a>LINQ to SQL 範例
這個範例示範如何建立活動，以使用 SQL Server 資料庫資料表中的 LINQ to SQL 查詢實體。  
  
> [!IMPORTANT]
>  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\Samples\WCFWFCardspace`  
>   
>  如果此目錄不存在，請按一下頁面最上方的 [下載範例] 連結。 請注意，這個連結會下載及安裝所有 [!INCLUDE[wf1](../../../../includes/wf1-md.md)]、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 和 [!INCLUDE[infocard](../../../../includes/infocard-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\Samples\WCFWFCardSpace\WF\Scenario\ActivityLibrary\Linq\LinqToSql`  
  
## <a name="activity-details-for-findinsqltable"></a>FindInSqlTable 的活動詳細資料  
 這個活動可讓使用者使用 LINQ to SQL 查詢資料庫資料表中的實體。 活動使用者也可以提供 Lambda 運算式形式的 LINQ 述詞來篩選結果。 如果未提供述詞，則會傳回整個資料表。 下表詳細說明活動的屬性和傳回值。  
  
|屬性或傳回值|描述|  
|------------------------------|-----------------|  
|`Collection` 屬性|指定來源集合的必要屬性。|  
|`Predicate` 屬性|必要屬性，指定 Lambda 運算式形式的集合篩選。|  
|傳回值|篩選的集合。|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a>使用自訂活動的程式碼範例  
 下列程式碼範例使用 `FindInSqlTable` 自訂活動，在名為 `Employee` 的 SQL Server 資料表中尋找 `Role` 資料行等於 `SDE` 的所有資料列。  
  
```csharp  
new FindInSqlTable<Employee>   
{  
    ConnectionString = @"Data Source=.\SQLExpress;Initial Catalog=LinqToSqlSample;Integrated Security=True",                          
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(emp => emp.Role.Equals("SDE"))),  
    Result = new OutArgument<IList<Employee>>(employees)  
},  
```  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  開啟命令提示字元。  
  
2.  導覽至包含這個範例的資料夾。  
  
3.  執行 Setup.cmd 命令檔。  
  
    > [!NOTE]
    >  Setup.cmd 指令碼會嘗試在本機電腦 SQL Server Express 安裝範例資料庫。 如果您想要在其他 SQL Server 執行個體中安裝，請編輯 Setup.cmd。  
  
     Setup.cmd 指令碼會執行下列動作：  
  
    -   建立名為 LinqToSqlSample 的資料庫。  
  
    -   建立 Roles 資料表。  
  
    -   建立 Employees 資料表。  
  
    -   將 3 個記錄插入至 Roles 資料表。  
  
    -   將 12 個記錄插入至 Employees 資料表。  
  
4.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 LinqToSQL.sln 方案檔案。  
  
5.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
6.  若要執行此方案，請按 F5。  
  
#### <a name="to-uninstall-the-linqtosql-sample-database"></a>若要解除安裝 LinqToSql 範例資料庫  
  
1.  開啟命令提示字元。  
  
2.  導覽至包含這個範例的資料夾。  
  
3.  執行 Cleanup.cmd 命令檔。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Liiinq\LinqToSql`  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to SQL](http://go.microsoft.com/fwlink/?LinkId=150376)  
 [使用者入門 (LINQ to SQL)](http://go.microsoft.com/fwlink/?LinkId=150377)
