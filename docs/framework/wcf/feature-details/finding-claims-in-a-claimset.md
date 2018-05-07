---
title: 在 ClaimSet 中尋找宣告
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], finding in a claimset
- claims [WCF]
ms.assetid: a76ce107-aeb3-47d0-bfa9-134c53664e20
ms.openlocfilehash: 7ca22d701277e71e509e6b291eb59a0223a0250c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="finding-claims-in-a-claimset"></a>在 ClaimSet 中尋找宣告
檢查 <xref:System.IdentityModel.Claims.ClaimSet> 內容以尋找特定類型的宣告，是在使用宣告架構授權時的常見工作。 若要檢查 <xref:System.IdentityModel.Claims.ClaimSet> 是否存在特定的宣告，請使用 <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> 方法。 這個方法比直接在 <xref:System.IdentityModel.Claims.ClaimSet> 上逐一查看提供更高的效能。 下列範例會示範這種使用方式。 請注意，`claimType` 和 `claimRight` 參數可以是 `null`。 在此情況下，這些參數將比對所有的宣告類型和宣告權限。  
  
## <a name="example"></a>範例  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 [使用身分識別模型來管理宣告與授權](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
