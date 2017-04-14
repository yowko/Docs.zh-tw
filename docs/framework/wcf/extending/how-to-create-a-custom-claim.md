---
title: "HOW TO：建立自訂宣告 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# HOW TO：建立自訂宣告
中的身分識別模型基礎結構[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]提供內建的宣告類型和權限的一組具有 helper 函式建立<xref:System.IdentityModel.Claims.Claim>透過這些類型和權限的執行個體。 這些內建宣告是專門用來模擬在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 預設支援的用戶端認證類型中找到的資訊。 在許多情況下，內建宣告就已足夠；不過有些應用程式可能需要自訂宣告。 宣告中包含了宣告類型、宣告適用的資源，以及擁有該資源所需的權限。 這個主題會描述如何建立自訂宣告。  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>依據基本資料型別建立自訂宣告  
  
1.  藉由傳遞宣告類型、 資源值和權限建立自訂宣告<xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29>建構函式。  
  
    1.  決定用於宣告類型的唯一值。  
  
         宣告類型為唯一的字串識別碼。 自訂宣告設計者的責任在於確保用於宣告類型的字串識別碼為獨一無二的。 如需宣告類型所定義的清單[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，請參閱<xref:System.IdentityModel.Claims.ClaimTypes>類別。  
  
    2.  選擇基本資料型別和資源的值。  
  
         資源就是物件。 資源的 CLR 型別可以是基本型別，例如<xref:System.String>或<xref:System.Int32>，或任何可序列化的型別。 因為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會在不同時間點序列化宣告，所以資源的 CLR 類型必須是可序列化的類型。 基本類型為可序列化。  
  
    3.  選擇 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 定義的權限，或者用於自訂權限的唯一值。  
  
         權限為唯一字串識別碼。 所定義的權限[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]中定義<xref:System.IdentityModel.Claims.Rights>類別。  
  
         自訂宣告設計者的責任在於確保用於權限的字串識別碼為獨一無二的。  
  
         下列程式碼範例建立自訂宣告的宣告型別`http://example.org/claims/simplecustomclaim`，名為資源`Driver's License`，與<xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>右。  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>依據非基本資料型別建立自訂宣告  
  
1.  藉由傳遞宣告類型、 資源值和權限建立自訂宣告<xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29>建構函式。  
  
    1.  決定用於宣告類型的唯一值。  
  
         宣告類型為唯一的字串識別碼。 自訂宣告設計者的責任在於確保用於宣告類型的字串識別碼為獨一無二的。 如需宣告類型所定義的清單[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，請參閱<xref:System.IdentityModel.Claims.ClaimTypes>類別。  
  
    2.  選擇或定義資源的可序列化非基本類型。  
  
         資源就是物件。 因為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會在不同時間點序列化宣告，所以資源的 CLR 類型必須是可序列化的類型。 基本類型已為可序列化。  
  
         定義新的型別時，套用<xref:System.Runtime.Serialization.DataContractAttribute>至類別。 也適用於<xref:System.Runtime.Serialization.DataMemberAttribute>屬性設定為需要序列化為宣告一部分之新類型的所有成員。  
  
         下列程式碼範例會定義名稱為 `MyResourceType` 的自訂資源類型。  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]  
  
    3.  選擇 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 定義的權限，或者用於自訂權限的唯一值。  
  
         權限為唯一字串識別碼。 所定義的權限[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]中定義<xref:System.IdentityModel.Claims.Rights>類別。  
  
         自訂宣告設計者的責任在於確保用於權限的字串識別碼為獨一無二的。  
  
         下列程式碼範例建立自訂宣告的宣告型別`http://example.org/claims/complexcustomclaim`，自訂資源類型的`MyResourceType`，與<xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>右。  
  
     [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
     [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]  
  
## <a name="example"></a>範例  
 下列程式碼範例會示範如何使用基本資源類型和非基本資源類型建立自訂宣告。  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IdentityModel.Claims.Claim>   
 <xref:System.IdentityModel.Claims.Rights>   
 <xref:System.IdentityModel.Claims.ClaimTypes>   
 <xref:System.Runtime.Serialization.DataContractAttribute>   
 <xref:System.Runtime.Serialization.DataMemberAttribute>   
 [使用識別模型管理宣告與授權](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)   
 [使用識別模型管理宣告與授權](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)