---
title: HOW TO：比較宣告
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
ms.openlocfilehash: 1ef957efcb4cc9330c1c273a1c953afc5b7dd240
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-compare-claims"></a>HOW TO：比較宣告
識別模型基礎結構中 Windows Communication Foundation (WCF) 用來執行授權檢查。 因此，比較授權內容中的宣告與執行所要求動作或存取所要求資源所需要的宣告，屬於常見的工作。 本主題將描述如何比較宣告，包括內建和自訂的宣告類型。 如需身分識別模型基礎結構的詳細資訊，請參閱[管理宣告和授權的方式識別模型](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)。  
  
 宣告比較需要將宣告中的三個部分 (類型、權限和資源) 與其他宣告的相同部分進行比較，以便判斷兩種宣告是否相等。 請參閱下列範例。  
  
 [!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
 [!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]  
  
 這兩個宣告的宣告類型都是 <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>、權限都是 <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>，而且資源也都是 "someone" 字串。 由於宣告的所有三個部分都相等，因此這些宣告本身是相等的。  
  
 內建的宣告類型會使用 <xref:System.IdentityModel.Claims.Claim.Equals%2A> 方法來進行比較。 必要時，則會使用宣告特定的比較程式碼。 例如，在下列這兩個指定的使用者主要名稱 (UPN) 宣告中：  
  
 [!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
 [!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]  
  
 中的比較程式碼<xref:System.IdentityModel.Claims.Claim.Equals%2A>方法會傳回`true`，此時是假設`example\someone`相同網域使用者識別為 「someone@example.com"。  
  
 自訂的宣告類型也可以使用 <xref:System.IdentityModel.Claims.Claim.Equals%2A> 方法來進行比較。 不過，在宣告的 <xref:System.IdentityModel.Claims.Claim.Resource%2A> 屬性所傳回的類型不同於原始類型的情況下，根據 <xref:System.IdentityModel.Claims.Claim.Equals%2A> 方法，只有在 `true` 屬性傳回的值相等時，`Resource` 才會傳回 <xref:System.IdentityModel.Claims.Claim.Equals%2A>。 在某些不適當的情況下，`Resource` 屬性傳回的自訂類型應該覆寫 <xref:System.IdentityModel.Claims.Claim.Equals%2A> 和 <xref:System.Object.GetHashCode%2A> 方法，以便執行任何必要的自訂處理。  
  
### <a name="comparing-built-in-claims"></a>比較內建的宣告  
  
1.  在兩個特定的 <xref:System.IdentityModel.Claims.Claim> 類別執行個體中，使用 <xref:System.IdentityModel.Claims.Claim.Equals%2A> 來進行比較，如下列程式碼所示。  
  
     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]  
  
### <a name="comparing-custom-claims-with-primitive-resource-types"></a>比較具有原始資源類型的自訂宣告  
  
1.  對於具有原始資源類型的自訂宣告，可以使用與內建宣告相同的方法來執行比較，如下列程式碼所示。  
  
     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]  
  
2.  對於具有結構或類別架構之資源類型的自訂宣告，資源類型應該覆寫 <xref:System.IdentityModel.Claims.Claim.Equals%2A> 方法。  
  
3.  首先，檢查 `obj` 參數是否為 `null`，如果是，則傳回 `false`。  
  
     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]  
  
4.  接下來，呼叫 <xref:System.Object.ReferenceEquals%2A>，然後將 `this` 和 `obj` 當做參數傳遞。 如果它傳回 `true`，則傳回 `true`。  
  
     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]  
  
5.  接下來，嘗試指派 `obj` 給類別類型的本機變數。 如果這個作業失敗，則參考為 `null`。 在這種情況下，將會傳回 `false`。  
  
6.  執行必要的自訂比較，以便正確地比較目前的宣告與提供的宣告。  
  
## <a name="example"></a>範例  
 下列範例會示範自訂宣告的比較，其中的宣告資源並非原始類型。  
  
 [!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
 [!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]  
  
## <a name="see-also"></a>另請參閱  
 [使用身分識別模型來管理宣告與授權](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [如何：建立自訂宣告](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
