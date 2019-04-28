---
title: 資料合約等價
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
ms.openlocfilehash: a526a58ef801e91775756e6a84a94a066d32d284
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857229"
---
# <a name="data-contract-equivalence"></a>資料合約等價
若要讓用戶端成功地將特定型別的資料傳送至服務，或讓服務成功地將資料傳送至用戶端，傳送的型別不一定要存在於接收端。 唯一的需求是這兩個型別的資料合約必須相等  (某些情況下，嚴格等價並非必要，所述[資料合約版本控制](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)。)  
  
 若要讓資料合約相等，則資料合約必須具有相同的命名空間和名稱。 此外，某一端的每個資料成員都必須有另一端的對等資料成員。  
  
 若要讓資料成員相等，則資料成員必須具有相同的名稱。 此外，還必須有相同的資料型別，也就是說，它們的資料合約必須相等。  
  
> [!NOTE]
>  請注意，資料合約名稱、命名空間和資料成員名稱必須區分大小寫。  
  
 如需有關資料合約名稱和命名空間，以及資料成員名稱的詳細資訊，請參閱 < [Data Contract Names](../../../../docs/framework/wcf/feature-details/data-contract-names.md)。  
  
 如果兩個型別存在於同一端 (傳送者或接收者)，但資料合約不相等 (例如，具有不同的資料成員)，則不應該為它們指定相同的名稱和命名空間。 這樣做可能會導致擲回例外狀況。  
  
 下列型別的資料合約是相等的：  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a>資料成員順序和資料合約等價  
 使用 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 類別的 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性，可能會影響資料合約等價。 資料合約必須以相同順序顯示成員，才會相等。 預設順序是字母順序。 如需詳細資訊，請參閱 <<c0> [ 資料成員順序](../../../../docs/framework/wcf/feature-details/data-member-order.md)。  
  
 例如，下列程式碼會產生對等的資料合約。  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 不過，下列程式碼不會產生對等的資料合約。  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a>繼承、介面和資料合約等價  
 判斷等價時，繼承自另一個資料合約的資料合約會被視為只是一個包含所有來自基底型別之資料成員的資料合約。 請記住，資料成員的順序必須相符，而且基底型別成員的順序必須在衍生型別成員之前。 此外，如果兩個資料成員有相同的順序值，則這些資料成員的順序為字母順序 (如下列程式碼範例)。 如需詳細資訊，請參閱 <<c0> [ 資料成員順序](../../../../docs/framework/wcf/feature-details/data-member-order.md)。  
  
 在下列範例中，`Employee` 型別的資料合約與 `Worker` 型別的資料合約相等。  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 在用戶端和服務之間傳遞參數和傳回值時，如果接收端點需要來自衍生類別的資料合約，則無法傳送來自基底類別的資料合約。 這符合物件導向程式設計原則。 在上一個範例中，類型的物件`Person`無法傳送`Employee`預期。  
  
 如果需要來自基底類別的資料合約，只有在接收端點使用 <xref:System.Runtime.Serialization.KnownTypeAttribute> 知道衍生型別時，才能傳送來自衍生類別的資料合約。 如需詳細資訊，請參閱 < [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。 在上一個範例中，如果需要 `Employee`，只有在接收者程式碼使用 `Person` 將 <xref:System.Runtime.Serialization.KnownTypeAttribute> 型別的物件包含在已知型別的清單時，才能傳送它。  
  
 在應用程式之間傳遞參數和傳回值時，如果預期型別是介面，它相當於 <xref:System.Object> 型別的預期型別。 因為每個型別最終都是衍生自 <xref:System.Object>，所以每個資料合約最終都會衍生自 <xref:System.Object> 的資料合約。 因此，如果需要介面，則可以傳遞任何資料合約類型。 若要成功使用介面，不需要其他步驟如需詳細資訊，請參閱 < [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [資料成員順序](../../../../docs/framework/wcf/feature-details/data-member-order.md)
- [資料合約已知類型](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [資料合約名稱](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
