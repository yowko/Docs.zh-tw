---
title: 如何：投影查詢結果(WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: 474ac625-8770-43ba-8320-d3315ea9530f
ms.openlocfilehash: 8a3a278a8459da073b7ad3cbf8d1fff1d435a18c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175183"
---
# <a name="how-to-project-query-results-wcf-data-services"></a>如何：投影查詢結果(WCF 資料服務)

投影提供一種機制，可藉由指定回應中僅傳回特定實體屬性的方式降低查詢傳回的資料量。 您可以使用 `$select` 查詢選項或在 LINQ 查詢的 Visual Basic) 中使用[select](../../../csharp/language-reference/keywords/select-clause.md) (子句，在 WCF Data Services 查詢的結果上[Select](../../../visual-basic/language-reference/queries/select-clause.md)執行預測。 如需詳細資訊，請參閱 [查詢資料服務](querying-the-data-service-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 此服務和用戶端資料類別會在您完成 [WCF Data Services 快速入門](quickstart-wcf-data-services.md)時建立。  
  
## <a name="example"></a>範例  

 下列範例顯示會將 Customers 實體投射至新的 CustomerAddress 類型之 LINQ 查詢，其中僅包含位址專用屬性加上識別屬性。 這個 `CustomerAddress` 類別已在用戶端上定義並屬性化，如此用戶端程式庫便能將它辨認為實體類型。  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>範例  

 下列範例顯示會將傳回之 Customers 實體投射至新的 CustomerAddressNonEntity 類型之 LINQ 查詢，其中僅包含位址專用屬性但不包含識別屬性。 這個 `CustomerAddressNonEntity` 類別已在用戶端上定義，但並未屬性化為實體類型。  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>範例  

 下列範例 `CustomerAddress` `CustomerAddressNonEntity` 會顯示先前範例中所使用之和類型的定義。  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customeraddress.vb#customeraddressdefinition)]
