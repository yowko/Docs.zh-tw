---
title: HOW TO：使用類別建立 Windows Communication Foundation 合約
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 37d0e6fae8ad0f3a91f1bead23fb5823fc52d420
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59313205"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>HOW TO：使用類別建立 Windows Communication Foundation 合約
建立 Windows Communication Foundation (WCF) 合約的慣用的方法是使用介面。 如需詳細資訊，請參閱[如何：定義服務合約](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)。 另一個方式就像這裡所略述的步驟，先建立一個類別，然後將 <xref:System.ServiceModel.ServiceContractAttribute> 屬性直接套用至該類別，並將 <xref:System.ServiceModel.OperationContractAttribute> 屬性套用該類別中屬於合約部分的各個方法。  
  
> [!WARNING]
>  `[ServiceContract]` 和 `[ServiceContractAttribute]` 會執行相同的動作。 相同的動作適用於`[OperationContract]`和`[OperationContractAttribute]`。 在每個案例中，前者是後者的簡寫。  
  
 如需有關服務合約的詳細資訊，請參閱 < [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md)。  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>以類別建立 Windows Communication Foundation 合約  
  
1. 建立新的類別，使用 Visual Basic 中， C#，或任何其他 common language runtime 語言。  
  
2. 將 <xref:System.ServiceModel.ServiceContractAttribute> 類別套用至該類別。  
  
3. 建立類別內的方法。  
  
4. 套用<xref:System.ServiceModel.OperationContractAttribute>必須公開為公用 WCF 合約一部分的每個方法的類別。  
  
## <a name="example"></a>範例  
 下列程式碼範例會示範定義服務合約的類別。  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 已套用 <xref:System.ServiceModel.OperationContractAttribute> 類別的方法依預設會使用要求-回覆訊息模式。 如需有關此訊息模式的詳細資訊，請參閱[How to:建立要求-回覆合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)。 您也可以設定屬性 (Attribute) 的屬性 (Property) 來建立並使用其他訊息模式。 如需更多範例，請參閱[如何：建立單向合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)和[How to:建立雙工合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
