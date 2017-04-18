---
title: "自訂作業：概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 自訂作業：概觀
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 預設會根據對應產生動態 SQL，以便進行插入、更新和刪除作業。但實際上，您通常會想加入自己的商務邏輯，為安全性、驗證等做準備。  
  
 用於自訂這些作業的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 技巧包含下列各項。  
  
## 載入選項  
 在查詢中，您可以控制在您連接至資料庫時要擷取多少與主要目標相關的資料。  這項功能大部分是使用 <xref:System.Data.Linq.DataLoadOptions> 來實作。  如需詳細資訊，請參閱[延後和立即載入的比較](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)。  
  
## 部分方法  
 在其預設對應中，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 提供了部分方法來協助您實作商務邏輯。  如需詳細資訊，請參閱[使用部分方法加入商務邏輯](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)。  
  
## 預存程序和使用者定義的函式  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援使用預存程序 \(Stored Procedure\) 和使用者定義函式。  預存程序時常用於自訂作業。  如需詳細資訊，請參閱[預存程序](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)。  
  
## 請參閱  
 [自訂插入、更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)