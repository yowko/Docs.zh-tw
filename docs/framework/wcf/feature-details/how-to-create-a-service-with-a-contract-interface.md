---
title: HOW TO：使用合約介面來建立服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: 796870b80ed72db2353e79db3e4e3fc164c22875
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489790"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>HOW TO：使用合約介面來建立服務
若要建立 Windows Communication Foundation (WCF) 合約的慣用的方法是使用介面。 此合約可指定存取服務提供之作業時所需的訊息集合與結構。 此介面可將 <xref:System.ServiceModel.ServiceContractAttribute> 類別套用到介面，並將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用到您想要公開的方法上，藉此定義輸入與輸出類型。  
  
 如需服務合約的詳細資訊，請參閱[設計服務合約](../../../../docs/framework/wcf/designing-service-contracts.md)。  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>使用介面來建立 WCF 合約  
  
1.  建立新的介面，使用 Visual Basic、 C# 中，或任何其他 common language runtime 語言。  
  
2.  將 <xref:System.ServiceModel.ServiceContractAttribute> 類別套用到介面。  
  
3.  在介面中定義方法。  
  
4.  套用<xref:System.ServiceModel.OperationContractAttribute>必須公開為公用的 WCF 合約一部分的每個方法的類別。  
  
## <a name="example"></a>範例  
 下列程式碼範例會顯示可定義服務合約的介面。  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 已套用 <xref:System.ServiceModel.OperationContractAttribute> 類別的方法依預設會使用要求-回覆訊息模式。 如需有關此訊息模式的詳細資訊，請參閱[How to： 建立要求-回覆合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)。 您也可以設定屬性 (Attribute) 的屬性 (Property) 來建立並使用其他訊息模式。 如需其他範例，請參閱[How to： 建立單向合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)和[How to： 建立雙工合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
