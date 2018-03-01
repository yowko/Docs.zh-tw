---
title: "資料合約名稱"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], naming
ms.assetid: 31f87e6c-247b-48f5-8e94-b9e1e33d8d09
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 56744318e6ea29350fd02d1cb35e49e566894a23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="data-contract-names"></a>資料合約名稱
有時候用戶端和服務不會共用相同的類型。 只要兩邊的資料合約都相同，仍然可以相互傳遞資料。 [資料合約等價](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)根據資料合約與資料成員名稱，並因此提供的機制是將對應的類型和成員到這些名稱。 此主題說明資料合約的命名規則，以及當建立名稱時 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 基礎結構的預設行為。  
  
## <a name="basic-rules"></a>基本規則  
 有關命名資料合約的基本規則包括：  
  
-   完整的資料合約名稱是由命名空間與名稱組成。  
  
-   資料成員只有名稱但是沒有命名空間。  
  
-   當處理資料合約時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 基礎結構對命名空間和資料合約與資料成員的名稱都會區分大小寫。  
  
## <a name="data-contract-namespaces"></a>資料合約命名空間  
 資料合約命名空間使用的格式為統一資源識別元 (URI)。 這個 URI 可為絕對或相對的。 根據預設，特定類型的資料合約會指派來自該類型之 Common Language Runtime (CLR) 命名空間的命名空間。  
  
 根據預設，任何指定的 CLR 命名空間 (以格式*Clr.Namespace*) 會對應至命名空間"http://schemas.datacontract.org/2004/07/Clr.Namespace"。 若要覆寫這個預設值，請將 <xref:System.Runtime.Serialization.ContractNamespaceAttribute> 屬性套用至整個模組或組件。 或是控制每個類型的資料合約命名空間，設定 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> 的 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性。  
  
> [!NOTE]
>  "http://schemas.microsoft.com/2003/10/Serialization" 命名空間會被保留，並且不能用來當做資料合約命名空間。  
  
> [!NOTE]
>  您無法覆寫其中包含 `delegate` 宣告之資料合約類型中的預設命名空間。  
  
## <a name="data-contract-names"></a>資料合約名稱  
 指定類型的資料合約預設名稱是該類型的名稱。 若要覆寫預設值，請將 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 的 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性設定為替代名稱。 泛型類型的特殊規則會在本主題稍後的「泛型類型的資料合約名稱」中描述。  
  
## <a name="data-member-names"></a>資料成員名稱  
 指定欄位或屬性的資料成員預設名稱是該欄位或屬性的名稱。 若要覆寫預設值，請將 <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> 的 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性設定為替代值。  
  
### <a name="examples"></a>範例  
 下列程式碼範例顯示如何覆寫資料合約與資料成員的預設命名行為。  
  
 [!code-csharp[C_DataContractNames#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#1)]
 [!code-vb[C_DataContractNames#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#1)]  
  
## <a name="data-contract-names-for-generic-types"></a>泛型類型的資料合約名稱  
 判定泛型類型的資料合約名稱有特殊規則。 這些規則會協助避免相同泛型類型的兩個封閉式泛型之間發生資料合約名稱衝突。  
  
 根據預設，資料合約名稱的泛型型別為型別的名稱，後面接著字串"Of"，後面接著資料合約名稱的泛型參數，後面接著*雜湊*使用資料合約命名空間的計算泛型參數。 雜湊是數學函式計算出來的結果，用來當做唯一識別資料片段的「指紋」。 當所有的泛型參數都是基本型別時，就會省略雜湊。  
  
 以下列範例中的型別為例：  
  
 [!code-csharp[C_DataContractNames#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#2)]
 [!code-vb[C_DataContractNames#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#2)]  
  
 在此範例中，型別 `Drawing<Square,RegularRedBrush>` 的資料合約名稱為 "DrawingOfSquareRedBrush5HWGAU6h"，其中 "5HWGAU6h" 是 "urn:shapes" 和 "urn:default" 命名空間的雜湊。 型別 `Drawing<Square,SpecialRedBrush>` 的資料合約名稱為 "DrawingOfSquareRedBrushjpB5LgQ_S"，其中 "jpB5LgQ_S" 是 "urn:shapes" 和 "urn:special" 命名空間的雜湊。 請注意，如果沒有使用雜湊，兩個名稱會完全相同，因而會發生名稱衝突。  
  
## <a name="customizing-data-contract-names-for-generic-types"></a>自訂泛型類型的資料合約名稱  
 有時候無法接收針對泛型類型產生的資料合約名稱 (如同之前所描述)。 例如，您可能事先知道不會產生名稱衝突並且想要移除雜湊。 在此例中，您可以使用 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 屬性 (Attribute) 的 `DataContractAttribute` 屬性 (Property) 指定不同的名稱產生方式。 您可以在 `Name` 屬性內使用以大括號包圍的數字，參考泛型參數的資料合約名稱  (0 參考第一個參數，1 參考第二個參數，以此類推)。您可以在大括號中使用數字 (#) 符號以參考雜湊。 您可以多次使用這些參考或完全不用。  
  
 例如，先前的泛型 `Drawing` 型別應該要如下的宣告方式：  
  
 [!code-csharp[c_DataContractNames#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#3)]
 [!code-vb[c_DataContractNames#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#3)]  
  
 在此例中，型別 `Drawing<Square,RegularRedBrush>` 的資料合約名稱為 "Drawing_using_RedBrush_brush_and_Square_shape"。 請注意，因為在 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 屬性中有一個 "{#}"，而雜湊不是名稱的一部分，所以型別就容易發生命名衝突；例如型別 `Drawing<Square,SpecialRedBrush>` 可能會擁有完全相同的資料合約名稱。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.ContractNamespaceAttribute>  
 [使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [資料合約等價](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [資料合約名稱](../../../../docs/framework/wcf/feature-details/data-contract-names.md)  
 [資料合約版本控制](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
