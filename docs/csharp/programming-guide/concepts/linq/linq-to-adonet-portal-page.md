---
title: "LINQ to ADO.NET (入口網站頁面) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f1c70901d5c2e5f5d709ec3c10821fbd1aa9dee6
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (入口網站頁面)
[!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)] 可讓您使用 [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] 程式設計模型，針對 [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] 中的任何可列舉物件進行查詢。  
  
> [!NOTE]
>  [!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)] 文件位於 .NET Framework SDK 的 ADO.NET 區段︰[LINQ 和 ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)。  
  
 有三種不同的 ADO.NET [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] 技術：[!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] 和 [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)]。 [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)] 提供更豐富且最佳化的 <xref:System.Data.DataSet> 查詢；[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] 可讓您直接查詢 [!INCLUDE[ssNoVersion](../../../../csharp/programming-guide/concepts/linq/includes/ssnoversion_md.md)] 資料庫結構描述，而 [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)] 可讓您查詢 [!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)]。  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet> 是 [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] 中最廣為使用的其中一個元件，並為已中斷連接程式設計模型 ([!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] 建置於其上) 的重要項目。 雖然 <xref:System.Data.DataSet> 具有上述優點，但是它的查詢功能仍然有限。  
  
 [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)] 可讓您使用許多其他資料來源適用的相同查詢功能，將更為豐富的查詢功能建置在 <xref:System.Data.DataSet> 中。  
  
 如需詳細資訊，請參閱 [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] 提供的執行階段基礎結構可以將關聯式資料當成物件來管理。 在 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] 中，關聯式資料庫的資料模型會對應至以開發人員的程式設計語言表示的物件模型。 執行應用程式時，[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] 會將物件模型中的 Language-integrated Query (LINQ) 轉譯成 SQL，並將這些查詢傳送至資料庫以便執行。 當資料庫傳回結果時，[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] 會將結果轉譯回物件，方便您加以管理。  
  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] 可支援資料庫的預存程序和使用者定義函式，以及物件模型中的繼承。  
  
 如需詳細資訊，請參閱 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)。  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 透過 [!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)]，關聯式資料會公開為 .NET 環境內的物件。 如此一來，物件層就成為理想的 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 支援目標，讓程式開發人員可以根據用於建置商務邏輯的語言，針對資料庫編寫查詢。 這項功能稱為 [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)]。 如需詳細資訊，請參閱 [LINQ to Entities](http://msdn.microsoft.com/library/641f9b68-9046-47a1-abb0-1c8eaeda0e2d)。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ 和 ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)   
 [Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
