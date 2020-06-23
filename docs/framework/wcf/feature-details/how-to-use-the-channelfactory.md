---
title: HOW TO：使用 ChannelFactory
description: 瞭解如何建立通道處理站來建立多個通道，以使用 WCF 用戶端來存取服務。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 7c87026ca4cf7c739f4615da9bc7f0272a382392
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246658"
---
# <a name="how-to-use-the-channelfactory"></a>HOW TO：使用 ChannelFactory
會在需要建立通道處理站的進階案例中使用泛型 <xref:System.ServiceModel.ChannelFactory%601> 類別，以建立多個通道。  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>建立及使用 ChannelFactory 類別  
  
1. 建立並執行 Windows Communication Foundation （WCF）服務。 如需詳細資訊，請參閱[設計和執行服務](../designing-and-implementing-services.md)、設定[服務](../configuring-services.md)和[裝載服務](../hosting-services.md)。  
  
2. 使用[System.servicemodel 中繼資料公用程式工具（Svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md)來產生用戶端的合約（介面）。  
  
3. 在用戶端程式碼中，使用 <xref:System.ServiceModel.ChannelFactory%601> 類別以建立多個端點接聽項。  
  
## <a name="example"></a>範例  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
