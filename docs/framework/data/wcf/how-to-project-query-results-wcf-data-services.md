---
title: HOW TO：專案查詢結果（WCF Data Services）
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
ms.openlocfilehash: 758bb01764fcfe195d4f940705316e7579be95ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780015"
---
# <a name="how-to-project-query-results-wcf-data-services"></a>作法：專案查詢結果（WCF Data Services）
投影提供一種機制，可藉由指定回應中僅傳回特定實體屬性的方式降低查詢傳回的資料量。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]您可以`$select`使用查詢選項，或在 LINQ 查詢中使用[select](../../../csharp/language-reference/keywords/select-clause.md)子句（在 Visual Basic 中[選取](../../../visual-basic/language-reference/queries/select-clause.md)），來執行查詢結果的投影。 如需詳細資訊，請參閱[查詢資料服務](querying-the-data-service-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成[WCF Data Services 快速入門](quickstart-wcf-data-services.md)時，會建立此服務和用戶端資料類別。  
  
## <a name="example"></a>範例  
 下列範例顯示會將 Customers 實體投射至新的 CustomerAddress 類型之 LINQ 查詢，其中僅包含位址專用屬性加上識別屬性。 這個 `CustomerAddress` 類別已在用戶端上定義並屬性化，如此用戶端程式庫便能將它辨認為實體類型。  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>範例  
 下列範例顯示會將傳回之 Customers 實體投射至新的 CustomerAddressNonEntity 類型之 LINQ 查詢，其中僅包含位址專用屬性但不包含識別屬性。 這個 `CustomerAddressNonEntity` 類別已在用戶端上定義，但並未屬性化為實體類型。  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>範例  
 下列範例會顯示先前範例中使用`CustomerAddress`之`CustomerAddressNonEntity`和類型的定義。  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customeraddress.vb#customeraddressdefinition)]
