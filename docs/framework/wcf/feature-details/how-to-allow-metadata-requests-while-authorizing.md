---
title: 如何：授權時同時允許中繼資料要求
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
ms.openlocfilehash: 4d549bb953ecdcbddd0ea4730a766538b2205d0f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082668"
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a>如何：授權時同時允許中繼資料要求
自訂授權期間，可能需要允許處理中繼資料的要求。 下列主題逐步解說要驗證如此要求的步驟。  
  
 如需有關 Windows Communication Foundation (WCF) 授權的詳細資訊，請參閱 <<c0> [ 授權](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)。  
  
### <a name="to-allow-metadata-requests-during-authorization"></a>授權時同時允許中繼資料要求  
  
1.  建立 <xref:System.ServiceModel.ServiceAuthorizationManager> 類別的延伸。  
  
2.  覆寫 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 方法。 方法會依據是否允許授權而傳回 `true` 或 `false`。 關於目前程式的資訊可在 <xref:System.ServiceModel.OperationContext> 傳給方法的參數找到。  
  
3.  在覆寫中，如以下範例所示，檢查合約名稱、命名空間以及動作。 如果條件為有效的則傳回 `true.`  
  
4.  使用擴充點套用類別。 如需詳細資訊，請參閱[如何：建立自訂授權管理員服務](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)。  
  
## <a name="example"></a>範例  
 下例範例示範 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 方法的覆寫。  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [使用身分識別模型來管理宣告與授權](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
