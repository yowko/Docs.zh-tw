---
title: 作法：使用合約介面來建立服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: 2234e6fe8d0ee2e0029a061ba96ef84f840f0c9b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286340"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>作法：使用合約介面來建立服務

建立 Windows Communication Foundation (WCF) 合約的慣用方式是使用介面。 此合約可指定存取服務提供之作業時所需的訊息集合與結構。 此介面可將 <xref:System.ServiceModel.ServiceContractAttribute> 類別套用到介面，並將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用到您想要公開的方法上，藉此定義輸入與輸出類型。  
  
 如需服務合約的詳細資訊，請參閱 [設計服務合約](../designing-service-contracts.md)。  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>使用介面來建立 WCF 合約  
  
1. 使用 Visual Basic、c # 或其他任何 common language runtime 語言建立新的介面。  
  
2. 將 <xref:System.ServiceModel.ServiceContractAttribute> 類別套用到介面。  
  
3. 在介面中定義方法。  
  
4. 將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用到每個必須公開為公用 WCF 合約一部分的方法。  
  
## <a name="example"></a>範例  

 下列程式碼範例會顯示可定義服務合約的介面。  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 已套用 <xref:System.ServiceModel.OperationContractAttribute> 類別的方法依預設會使用要求-回覆訊息模式。 如需此訊息模式的詳細資訊，請參閱 [如何：建立 Request-Reply 合約](how-to-create-a-request-reply-contract.md)。 您也可以設定屬性 (Attribute) 的屬性 (Property) 來建立並使用其他訊息模式。 如需更多範例，請參閱 [如何：建立 One-Way 合約](how-to-create-a-one-way-contract.md) 和 [如何：建立雙工合約](how-to-create-a-duplex-contract.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
