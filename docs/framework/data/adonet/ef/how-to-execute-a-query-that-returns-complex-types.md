---
title: "HOW TO：執行可傳回複雜類型的查詢 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "ESQL"
  - "jsharp"
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# HOW TO：執行可傳回複雜類型的查詢
本主題展示如何執行會傳回內含複雜型別屬性之實體類型物件的 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查詢。  
  
### 執行此範例中的程式碼  
  
1.  將 [AdventureWorks Sales Model](http://msdn.microsoft.com/zh-tw/f16cd988-673f-4376-b034-129ca93c7832) 加入至專案中，並將專案設定為使用 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。  如需詳細資訊，請參閱[How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/zh-tw/dadb058a-c5d9-4c5c-8b01-28044112231d)。  
  
2.  在應用程式的字碼頁中加入下列 `using` 陳述式 \(在 Visual Basic 中為 `Imports`\)：  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  您可以在實體設計工具的 [&#91;模型瀏覽器&#93; 視窗](http://msdn.microsoft.com/zh-tw/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd)中按兩下 .edmx 檔顯示模型。  在實體設計工具介面上，選取 `Contact` 實體類型的 `Email` 和 `Phone` 屬性，然後以滑鼠右鍵按一下並選取 \[**重構至新的複雜型別**\]。  
  
4.  含有已選取之 `Email` 和 `Phone` 屬性的新複雜型別隨即會加入到 \[**模型瀏覽器**\]。  複雜型別已有預設名稱：請在 \[**屬性**\] 視窗中將型別重新命名為 `EmailPhone`。  也會將新的 `ComplexProperty` 屬性加入至 `Contact` 實體類型。  將屬性重新命名為 `EmailPhoneComplexType.`  
  
     如需使用實體資料模型精靈來建立及修改複雜型別的詳細資訊，請參閱 [How to: Refactor Existing Properties into a Complex Type Property](http://msdn.microsoft.com/zh-tw/5b2eb3b3-693d-42cb-b43a-405812d677eb) 和 [How to: Create and Modify Complex Types](http://msdn.microsoft.com/zh-tw/afb8e206-0ffe-4597-b6d4-6ab566897e1d)。  
  
## 範例  
 下列範例所執行的查詢，會傳回 `Contact` 物件的集合並顯示 `Contact` 物件的兩個屬性：`ContactID` 和 `EmailPhoneComplexType` 複雜型別的值。  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]