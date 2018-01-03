---
title: "如何：投影查詢結果(WCF 資料服務)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: 474ac625-8770-43ba-8320-d3315ea9530f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80c6216315ca1fb1200e12bca89ae8ef27652947
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-project-query-results-wcf-data-services"></a>如何：投影查詢結果(WCF 資料服務)
投影提供一種機制，可藉由指定回應中僅傳回特定實體屬性的方式降低查詢傳回的資料量。 您可以執行預測的結果[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]查詢使用`$select`查詢選項或使用[選取](~/docs/csharp/language-reference/keywords/select-clause.md)子句 ([選取](~/docs/visual-basic/language-reference/queries/select-clause.md)在 Visual Basic 中) 中的 LINQ 查詢。 如需詳細資訊，請參閱[查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成建立此服務和用戶端資料類別[WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
## <a name="example"></a>範例  
 下列範例顯示會將 Customers 實體投射至新的 CustomerAddress 類型之 LINQ 查詢，其中僅包含位址專用屬性加上識別屬性。 這個 `CustomerAddress` 類別已在用戶端上定義並屬性化，如此用戶端程式庫便能將它辨認為實體類型。  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>範例  
 下列範例顯示會將傳回之 Customers 實體投射至新的 CustomerAddressNonEntity 類型之 LINQ 查詢，其中僅包含位址專用屬性但不包含識別屬性。 這個 `CustomerAddressNonEntity` 類別已在用戶端上定義，但並未屬性化為實體類型。  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>範例  
 下列範例顯示定義`CustomerAddress``CustomerAddressNonEntity`前一個範例中所用的類型。  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customeraddress.vb#customeraddressdefinition)]
