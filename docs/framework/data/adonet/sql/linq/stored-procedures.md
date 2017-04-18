---
title: "預存程序 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 預存程序
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會使用您物件模型 \(Object Model\) 中的方法，表示資料庫中的預存程序 \(Stored Procedure\)。  您可套用 <xref:System.Data.Linq.Mapping.FunctionAttribute> 屬性 \(Attribute\) 和 \(視需要\) 套用 <xref:System.Data.Linq.Mapping.ParameterAttribute> 屬性，將方法指定為預存程序。  如需詳細資訊，請參閱 [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)。  
  
 使用 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 的開發人員通常會使用 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] 來對應預存程序。本節中的主題顯示自行撰寫程式碼時，如何在應用程式中形成和呼叫這些方法。  
  
## 在本節中  
 [HOW TO：傳回資料列集](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md)  
 描述如何傳回資料列，以及顯示如何使用輸入參數。  
  
 [HOW TO：使用接受參數的預存程序](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-that-take-parameters.md)  
 描述如何使用輸入和輸出參數。  
  
 [HOW TO：使用對應多個結果圖案的預存程序](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 描述如何為在相同預存程序中傳回多個圖案做準備。  
  
 [HOW TO：使用對應循序結果圖案的預存程序](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 描述如何為已知傳回序列情況下的多個圖案做準備。  
  
 [使用預存程序自訂作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)  
 描述如何使用預存程序來實作插入、更新和刪除作業。  
  
 [僅使用預存程序自訂作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures-exclusively.md) SQL\)  
 描述如何只使用預存程序來實作插入、更新和刪除作業。  
  
## 相關章節  
 [程式設計手冊](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 提供如何建立和使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 物件模型的相關資訊。  
  
 [逐步解說：僅使用預存程序 \(Visual Basic\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)  
 包含可說明如何在 Visual Basic 中使用預存程序的相關程序。  
  
 [逐步解說：僅使用預存程序 \(C\#\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)  
 包含可說明如何在 C\# 中使用預存程序的相關程序。