---
title: "資料合約名稱 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "資料合約 [WCF], 命名"
ms.assetid: 31f87e6c-247b-48f5-8e94-b9e1e33d8d09
caps.latest.revision: 27
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 27
---
# 資料合約名稱
有時候用戶端和服務不會共用相同的類型。只要兩邊的資料合約都相同，仍然可以相互傳遞資料。[資料合約等價](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)是根據資料合約與資料成員名稱，因此會提供機制將型別與成員對應至這些名稱。此主題說明資料合約的命名規則，以及當建立名稱時 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 基礎結構的預設行為。  
  
## 基本規則  
 有關命名資料合約的基本規則包括：  
  
-   完整的資料合約名稱是由命名空間與名稱組成。  
  
-   資料成員只有名稱但是沒有命名空間。  
  
-   當處理資料合約時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 基礎結構對命名空間和資料合約與資料成員的名稱都會區分大小寫。  
  
## 資料合約命名空間  
 資料合約命名空間使用的格式為統一資源識別元 \(URI\)。這個 URI 可為絕對或相對的。根據預設，特定類型的資料合約會指派來自該類型之 Common Language Runtime \(CLR\) 命名空間的命名空間。  
  
 根據預設，任何指定的 CLR 命名空間 \(使用格式 *Clr.Namespace*\) 都會對應至命名空間 "http:\/\/schemas.datacontract.org\/2004\/07\/Clr.Namespace"。若要覆寫這個預設值，請將 <xref:System.Runtime.Serialization.ContractNamespaceAttribute> 屬性套用至整個模組或組件。或是控制每個類型的資料合約命名空間，設定 <xref:System.Runtime.Serialization.DataContractAttribute> 的 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> 屬性。  
  
> [!NOTE]
>  "http:\/\/schemas.microsoft.com\/2003\/10\/Serialization" 命名空間會被保留，並且不能用來當做資料合約命名空間。  
  
> [!NOTE]
>  您無法覆寫其中包含 `delegate` 宣告之資料合約類型中的預設命名空間。  
  
## 資料合約名稱  
 指定類型的資料合約預設名稱是該類型的名稱。若要覆寫預設值，請將 <xref:System.Runtime.Serialization.DataContractAttribute> 的 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 屬性設定為替代名稱。泛型類型的特殊規則會在本主題稍後的「泛型類型的資料合約名稱」中描述。  
  
## 資料成員名稱  
 指定欄位或屬性的資料成員預設名稱是該欄位或屬性的名稱。若要覆寫預設值，請將 <xref:System.Runtime.Serialization.DataMemberAttribute> 的 <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> 屬性設定為替代值。  
  
### 範例  
 下列程式碼範例顯示如何覆寫資料合約與資料成員的預設命名行為。  
  
 [!code-csharp[C_DataContractNames#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#1)]
 [!code-vb[C_DataContractNames#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#1)]  
  
## 泛型類型的資料合約名稱  
 判定泛型類型的資料合約名稱有特殊規則。這些規則會協助避免相同泛型類型的兩個封閉式泛型之間發生資料合約名稱衝突。  
  
 根據預設，泛型類型的資料合約名稱是類型的名稱，後面接著字串 "Of"、泛型參數的資料合約名稱，以及使用泛型參數之資料合約命名空間計算出來的「*雜湊*」\(Hash\)。雜湊是數學函式計算出來的結果，用來當做唯一識別資料片段的「指紋」。當所有的泛型參數都是基本型別時，就會省略雜湊。  
  
 以下列範例中的型別為例：  
  
 [!code-csharp[C_DataContractNames#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#2)]
 [!code-vb[C_DataContractNames#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#2)]  
  
 在此範例中，型別 `Drawing<Square,RegularRedBrush>` 的資料合約名稱為 "DrawingOfSquareRedBrush5HWGAU6h"，其中 "5HWGAU6h" 是 "urn:shapes" 和 "urn:default" 命名空間的雜湊。型別 `Drawing<Square,SpecialRedBrush>` 的資料合約名稱為 "DrawingOfSquareRedBrushjpB5LgQ\_S"，其中 "jpB5LgQ\_S" 是 "urn:shapes" 和 "urn:special" 命名空間的雜湊。請注意，如果沒有使用雜湊，兩個名稱會完全相同，因而會發生名稱衝突。  
  
## 自訂泛型類型的資料合約名稱  
 有時候無法接收針對泛型類型產生的資料合約名稱 \(如同之前所描述\)。例如，您可能事先知道不會產生名稱衝突並且想要移除雜湊。在此例中，您可以使用 `DataContractAttribute` 屬性 \(Attribute\) 的 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 屬性 \(Property\) 指定不同的名稱產生方式。您可以在 `Name` 屬性內使用以大括號包圍的數字，參考泛型參數的資料合約名稱 \(0 參考第一個參數，1 參考第二個參數，以此類推\)。您可以在大括號中使用數字 \(\#\) 符號以參考雜湊。您可以多次使用這些參考或完全不用。  
  
 例如，先前的泛型 `Drawing` 型別應該要如下的宣告方式：  
  
 [!code-csharp[c_DataContractNames#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#3)]
 [!code-vb[c_DataContractNames#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#3)]  
  
 在此例中，型別 `Drawing<Square,RegularRedBrush>` 的資料合約名稱為 "Drawing\_using\_RedBrush\_brush\_and\_Square\_shape"。請注意，因為在 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 屬性中有一個 "{\#}"，而雜湊不是名稱的一部分，所以型別就容易發生命名衝突；例如型別 `Drawing<Square,SpecialRedBrush>` 可能會擁有完全相同的資料合約名稱。  
  
## 請參閱  
 <xref:System.Runtime.Serialization.DataContractAttribute>   
 <xref:System.Runtime.Serialization.DataMemberAttribute>   
 <xref:System.Runtime.Serialization.ContractNamespaceAttribute>   
 [使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)   
 [資料合約等價](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)   
 [Data Contract Names](../../../../docs/framework/wcf/feature-details/data-contract-names.md)   
 [資料合約版本控制](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)