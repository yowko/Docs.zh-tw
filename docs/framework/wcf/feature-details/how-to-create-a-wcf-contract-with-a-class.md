---
title: HOW TO：使用類別建立 Windows Communication Foundation 合約
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 0be2400ef3da5f0bbc218032ecd69af23f82cabd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597133"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>HOW TO：使用類別建立 Windows Communication Foundation 合約
建立 Windows Communication Foundation （WCF）合約的慣用方法是使用介面。 如需詳細資訊，請參閱[如何：定義服務合約](../how-to-define-a-wcf-service-contract.md)。 另一個方式就像這裡所略述的步驟，先建立一個類別，然後將 <xref:System.ServiceModel.ServiceContractAttribute> 屬性直接套用至該類別，並將 <xref:System.ServiceModel.OperationContractAttribute> 屬性套用該類別中屬於合約部分的各個方法。  
  
> [!WARNING]
> `[ServiceContract]` 和 `[ServiceContractAttribute]` 會執行相同的動作。 和的情況也是如此 `[OperationContract]` `[OperationContractAttribute]` 。 在每個案例中，前者是後者的速記。  
  
 如需服務合約的詳細資訊，請參閱[設計服務合約](../designing-service-contracts.md)。  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>以類別建立 Windows Communication Foundation 合約  
  
1. 使用 Visual Basic、c # 或其他任何 common language runtime 語言建立新的類別。  
  
2. 將 <xref:System.ServiceModel.ServiceContractAttribute> 類別套用至該類別。  
  
3. 建立類別內的方法。  
  
4. 將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用至必須公開為公用 WCF 合約一部分的每個方法。  
  
## <a name="example"></a>範例  
 下列程式碼範例會示範定義服務合約的類別。  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 已套用 <xref:System.ServiceModel.OperationContractAttribute> 類別的方法依預設會使用要求-回覆訊息模式。 如需此訊息模式的詳細資訊，請參閱[如何：建立要求-回復合約](how-to-create-a-request-reply-contract.md)。 您也可以設定屬性 (Attribute) 的屬性 (Property) 來建立並使用其他訊息模式。 如需更多範例，請參閱[如何：建立單向合約](how-to-create-a-one-way-contract.md)和[如何：建立雙工合約](how-to-create-a-duplex-contract.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
