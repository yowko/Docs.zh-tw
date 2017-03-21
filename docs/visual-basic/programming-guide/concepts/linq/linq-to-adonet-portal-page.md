---
title: "LINQ to ADO.NET (入口網站頁面) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5c71b304dbff960320b1a9f46e38259705b8dadc
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (入口網站頁面)
[!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)]可讓您查詢中任何可列舉物件上方[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]使用[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]程式設計模型。  
  
> [!NOTE]
>  [!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)]文件位於.NET Framework SDK 的 ADO.NET 區段︰ [LINQ 和 ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)。  
  
 有三種不同的 ADO.NET [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] 技術：[!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] 和 [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)]。 [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]提供更豐富且最佳化查詢<xref:System.Data.DataSet>，[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]可讓您直接查詢[!INCLUDE[ssNoVersion](../../../../csharp/programming-guide/concepts/linq/includes/ssnoversion_md.md)]資料庫結構描述，以及[!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)]可讓您查詢[!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)]。</xref:System.Data.DataSet>  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet>是最廣泛使用的元件中的其中一個[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]，為索引鍵之中斷連接程式設計模型的項目和[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]為建置基礎。</xref:System.Data.DataSet> 這個優點，不過，儘管<xref:System.Data.DataSet>具有有限的查詢功能。</xref:System.Data.DataSet>  
  
 [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]可讓您建置更豐富的查詢功能<xref:System.Data.DataSet>使用相同的查詢功能可用於許多其他資料來源。</xref:System.Data.DataSet>  
  
 如需詳細資訊，請參閱[LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] 提供的執行階段基礎結構可以將關聯式資料當成物件來管理。 在[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]，關聯式資料庫的資料模型會對應至以開發人員的程式語言表示的物件模型。 當您執行應用程式，[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]物件模型中的 language-integrated query 轉譯成 SQL 並將它們傳送到資料庫中執行。 當資料庫傳回結果，[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]轉譯回您可以管理的物件。  
  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]物件模型中包含預存程序和使用者定義函式，在資料庫中，以及繼承的支援。  
  
 如需詳細資訊，請參閱[LINQ to SQL](https://msdn.microsoft.com/library/bb386976)。  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 透過 [!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)]，關聯式資料會公開為 .NET 環境內的物件。 如此一來，物件層就成為理想的 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 支援目標，讓程式開發人員可以根據用於建置商務邏輯的語言，針對資料庫編寫查詢。 這項功能稱為 [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)]。 請參閱[LINQ to Entities](http://msdn.microsoft.com/library/641f9b68-9046-47a1-abb0-1c8eaeda0e2d)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ 和 ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)   
 [語言整合查詢 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
