---
title: HOW TO：使用 ChannelFactory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 7d542a3dcae514e75194b49c23a8dec5dd7e8c3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047252"
---
# <a name="how-to-use-the-channelfactory"></a>HOW TO：使用 ChannelFactory
會在需要建立通道處理站的進階案例中使用泛型 <xref:System.ServiceModel.ChannelFactory%601> 類別，以建立多個通道。  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>建立及使用 ChannelFactory 類別  
  
1. 建置並執行 Windows Communication Foundation (WCF) 服務。 如需詳細資訊，請參閱[設計與實作服務](../../../../docs/framework/wcf/designing-and-implementing-services.md)， [Configuring](../../../../docs/framework/wcf/configuring-services.md)，並[裝載服務](../../../../docs/framework/wcf/hosting-services.md)。  
  
2. 使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來產生用戶端的合約 （介面）。  
  
3. 在用戶端程式碼中，使用 <xref:System.ServiceModel.ChannelFactory%601> 類別以建立多個端點接聽項。  
  
## <a name="example"></a>範例  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
